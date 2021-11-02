# Integration Tools

Integrations are a core functionality in a number of projects. Over the years several solutions of different nature have been designed to assist with integrations. Furthermore, the years of integrations have resulted in a number of design patterns to be created. Nonetheless, still a large number of projects end up constructing integrations with a lot of customizations. The most common reason for the customization efforts or the lack of adoption of frameworks and platforms are: licensing costs, lack of ownership on process, and requirements are way too complex to deal with standard functionality.

The scope of the project is to provide open-source building blocks (assets) for the most common integration scenarios, while still allowing the solution to be constructed to the specifications and limitations of the project.

## How to deal with complex integrations

Integrations always consist of 3 simple phases:

* Extract of data from a source system
* Preparation of data for the target system (transformation of data from source to target)
* Loading of data to 1 or more target systems

However, although these 3 steps can be quite well distinguished, a lot of solutions fail to simplify the transformation phase. Typically reasons for this failure can be abstractly generalized in 4 factors (in no particular order):

* Not understanding the business process demand for the integration
* Using the wrong technology for the job
* Not well segregating the requirement into manageable steps
* Tackling the problem from the wrong aspect

Let's look at each one and how it can be simplified.

### Segregating the requirements

A way to common practice is to look at the requirements for an integration as one block. That is, when analyzing a requirement it is common to talk about required fields, field dependencies, validations required for both sides of the story, data type conversions or restrictions and field mappings as a single entity. Although this is a feasible practice for consultants and business analysts, it is not that feasible for development. When it comes to development trying to merge all the information into 1 process can lead to complex implementations, which in turn will make the code difficult to build and maintain.

To overcome such situations and simplify the integration a very simple process can be applied to try to reduce the complexity. First consider the processing part of the integration as:

1. Validate the data that was extracted from the source system
2. Manipulate the data to the format that is required by the target system
3. Validate the data produced against the target system requirements

With this in mind, split the requirements into what is needed as step 1, step 2 and step 3. Next each step can be evaluated further by classifying the work that needs to be done.

For the validation steps, classify the requirements as:

* Checking of required fields,
* Checking the type compatibility,
* Checking against an expected pattern,
* A custom logic based validation.

Next do a similar classification for the transformation process:

* Copy the field to another field,
* Copy the field to another field but change the type of the field,
* Populate a field based on some custom logic

The majority of the requirements will match the simple parts, while the parts that require custom logic become the case to complicate the integrations throughout. By trying to keep the separation between the processes it becomes easier to handle the requirement. A simplification process for the custom logic can be performed and extracted to steps that are manageable. Thus the development starts getting simpler with every step.

#### How does the project help in this approach

The project provides libraries for the transformation and validation process that matches the simplification process mentioned above. By defining validation and transformation rules separately, and the need to call the functions performing the entire logic separately, one needs to simplify the complex blocks.

The initial release caters for part of the scenarios mentioned for each step, with the ability to add logic where required. With the evolution of the libraries more and more configurable scenarios will be defined.

### Using the wrong technology

One of the most common reasons for integrations becoming complex can be blamed to technology. A vast variety of technologies are around all developed and designed with specific ideas and concepts. Due to the ability of developers to twist the technology to their needs, it became common to try to fit all requirements to one technology. When the technology is heavily molded or is used for the wrong purpose, issues start to crop up. Due to personal preferences or because of business demands, rather than switching the technology and accepting the need for the change, most of the time developers are pushed to simply fix the issues by continuing to increase complexity.

#### How can the project be used to reduce the risk of using the wrong technology

The project will not solve the issue, especially if it is coming from the business. This project is focused on the transformation and validation aspects of integrations. However sister projects will be made available to handle this problem.

### Tackling the problem from the wrong angle

There is no technology or concepts that can be applied to identify that the problem is being tackled wrongly. The best approach if things start complicating, is to stop, rest and relook at the problem from the beginning.

### Not understanding the business process demand for the integration

When an integration looks well over complicated with many special cases and edge scenarios, typically it is the result of not understanding the business. Sometimes it can be the business that is not understanding what the integration performs. The later is easy to cater for through training sessions. For the former, the best approach is to collect all the information, consolidate it into a business process from one end user to another and re-run it with the business specialists. Once an agreement is achieved, split the problem into manageable pieces and apply the process described earlier to get to the implementation requirements.

Ok, 1 to 1 solutions are easy. What if there is an N to N integration demand.

### Dealing with multiple target systems

When dealing with 1 source and multiple targets, look at the integration as a 1 to 1 integrations. The 1 to N can be achieved through the integration code. However, as long as the target systems have no dependency on each other, the integration is still 1 to 1.

When integrations have dependencies between targets, consider the integration as two different 1 to 1 integrations. The integration between the source and the dependent target, can be seen as the integration between the source and the target that will be the source for the second target.

### Dealing with multiple sources to one target system

With multiple sources sending the data to a single target system, the integration can still be considered as a 1 to 1 system. Most of the systems nowadays accept that the data can be updated. For these systems, each source system can send its own data separately and the target system construct the final data. If the target system cannot combine the details or has required fields that stop the data form being created and the required data come from the different systems, try to add a middle layer like a database to reduce the complexity of the import.

## Table of Contents

* Libraries
  * [Documentation](Libraries/documentation.md)
  * [Planned Features](Libraries/planned_features.md)
* Documents for Contributors
  * [Extending the Libraries](Contributors/extending_the_libraries.md)
  * [Project Boards](Contributors/project_boards.md)
  * [Working on Ideas](Contributors/working_on_ideas.md)