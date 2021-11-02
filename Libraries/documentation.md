# Introduction

The project defines two libraries, one for transformation and another one for validation. The libraries are separate as it is possible to use one of them without dependencies on each other.

## Transformation of Data

This project attempts to define a library that allow transformation to be handled with minimal code requirements. The library is built to use JSON as the object base for all operations. The benefit of using JSON with Newtonsoft library is that objects are returned a parser tokens on which a number of operations are available. On top of the JSON object, the library defines a set of transformation that can be performed.

### Types of Transformation

There are 4 main types of data transformations that are required by projects

| Transformation Type | Description |
|:-----|:-----------|
| Leave as is | The data is copied from one field to another without any transformation |
| Simple Transformation | These are the most common transformations where a field is converted using Type Conversion (between compatible types), or Label to a Value or vice-versa |
| Computation Transformations | These are the type of transformations where the value is either a concatenation, converting an array to a list, arithmetic computation on inputs, and more |
| Complex Transformations | These type of transformation are very business specific and can be a combination of any logic |

#### Leave as is Transformation

The leave as is type of transformation is the simplest kind where no logic is required. However this type of transformation comes with heavy limitations. Only the basic types of data can be handled, like string, integer, decimal, numeric, etc. Objects are one of the cases that a Leave as Is transformation cannot deal with. Although it is easy to copy an object across, it raises a number of questions related to the inner fields of the object and what if these fields are objects themselves.

#### Conversion Transformation

The conversion type of transformation is when a field value needs to be converted to a compatible type, for example and integer to double or date to a specific representation. A number of supported conversations are built in as described in the [Supported Conversions](supported_conversions.md).

#### Complex Transformation

Complex transformations are the most difficult to pre-develop support for. To support these type of conversions, an `Expression` support is added to the mapping rules class. The Expression takes a function with 2 parameters, the source field (or object) and a logger if set in the `Transform` class.

### Supported Conversions

A number of standard conversion between data types are available.

Available Conversions:

| ```Rule.As``` Value | Details |
|:-----|:-----|
| Double | Converts the object's string representation into a Double (Fraction). Note that Double is the largest representation in .NET for fraction numbers. When the object doesn't represent a valid whole number the property is considered invalid and ignored in the output. |
| IsoUtcDate | Converts a date object to UTC and in the format ``yyyy-MM-ddTHH:mm:ss.fffffffZ`` |
| IsoDate | Converts a date object to Server TimeZone and in the format ``yyyy-MM-ddTHH:mm:ss.fffffff`` if a timezone was added to the date object when received, the timezone of the server is inserted in the reply. _Note Use this conversion only if all systems support the server timezone or are able to handle timezones_ |
| SerializeJson | Converts the object to its string representation. |
| String | Converts the object to its string representation using the ``ToString()`` |
| WholeNumber | Converts the object in string representation into a Whole Number (Integer). When the object doesn't represent a valid whole number the property is considered invalid and ignored in the output. |

**Note** _When a property cannot be converted and is ignored, this is mentioned in the logs as a Warning._

## Validating the data

The validation library, similar to the transformation library works over a JSON object. By iterating over the JSON tokens it evaluates the validation rules provided and returns whether the input to the library satisfies the rules or not.

### Supported Validations

The following validations have been implemented

| Validation Type | Description |
|:-----|:-----------|
| Required | The field is required to be present in the object received |
| Pattern | If the value is present, it must be in a format that matches a pattern. For example, validation of email address or telephone number |
| Computational | A number of validations can be created based on the specific need of the project. For example, checking dependent fields or either-or fields. To keep the library as flexible as possible, any specific logic can be added to rules by using the `Expression` parameter |

Back to [Homepage](../index.md)
