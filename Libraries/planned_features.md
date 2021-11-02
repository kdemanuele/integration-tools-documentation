# Planned Features

A number of features are planned to be added to the libraries. Everyone can contribute towards these features by cloning the project, create a feature branch and then submit a pull request into the develop branch.

For any feature suggestions, please submit an Issue tagged as Enhancement for review.

## Transformation Upcoming Features

| Feature Number | Issue Reference | Description | Status |
|:-----|:-------|:------|:----:|
| T001 | not applicable | Support of conversion using a table containing mappings between labels and their values. Ideal when dealing with solutions that need to map string or integer values of multiple systems. For example: Option Sets (in Dynamics 365 CE) <br/> As working with labels across systems might introduce text inconsistencies, the feature needs to support Expressions to assist in the matching. | ![#f03c15](https://via.placeholder.com/300x100/f03c15/ffffff?text=Pending) |
| T002 | not applicable | The ability to defined the transformation mappings using a JSON file. | ![#f03c15](https://via.placeholder.com/300x100/f03c15/ffffff?text=Pending) |
| T003 | not applicable | Some integrations can ignore errors during the transformation especially if no critical fields are impacted. Currently the libraries throws the exception and stops. A mechanism to trap the exception and continue the evaluation of the source objects can allow control on when to stop the process or continue. | ![#f03c15](https://via.placeholder.com/300x100/f03c15/ffffff?text=Pending) |
| V001 | not applicable | Support for basic validation of data before and after the transformation. To support: required field checking, input type comparison, custom function for validation | ![#f03c15](https://via.placeholder.com/300x100/f03c15/ffffff?text=Pending) |
| V002 | not applicable | Support verification on the type of the object. | ![#f03c15](https://via.placeholder.com/300x100/f03c15/ffffff?text=Pending) |

Back to [Documentation](documentation.md)

Back to [Homepage](../index.md)
