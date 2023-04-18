# Cheat Sheet

This document contains an overview of fundamental concepts and terminology, you can use this as a reference book if you get lost in the terminology along the way.

## Github actions high level components

<img width="671" alt="image" src="https://user-images.githubusercontent.com/10853833/216319332-3d5529e8-abfc-4dab-b9b7-e55c4cba99e5.png">

## Yaml functions

| Function                        | Description                                                                                           |
|---------------------------------|-------------------------------------------------------------------------------------------------------|
| success()                       | Returns true if none of the previous steps have failed or been cancelled.                             |
| always()                        | Returns true even if a previous step was cancelled and causes the step to always get executed anyway. |
| cancelled()                     | Returns only true if the workflow was canceled.                                                       |
| failure()                       | Returns true if a previous step of the job had failed.                                                |
| contains(search, item)          | Returns true if search contains item.                                                                 |
| startsWith(search, item)        | Returns true if search starts with item.                                                              |
| endsWith(search, item)          | Return true if search ends with item.                                                                 |
| format('{0} {1}', item1, item2) | Replaces placeholders in a string.                                                                    |
| join(array, separator)          | All values in array are concatenated into a string using provided separator                           |
| toJSON(value)                   | Returns a pretty-print JSON representation of value.                                                  |
| fromJSON(value)                 | Returns a JSON object or JSON data type for value.                                                    |

## Workflow commands

See also:
https://docs.github.com/en/actions/using-workflows/workflow-commands-for-github-actions
Actions can communicate with the runner machine to set environment variables, output values used by other actions, add debug messages to the output logs, and other tasks.
Most workflow commands use the echo command in a specific format, while others are invoked by writing to a file. 

Example echo workflow command:
```bash
echo "::workflow-command parameter1={data},parameter2={data}::{command value}"
```
Example write to file workflow command:
```bash
echo "SELECTED_COLOR=green" >> $GITHUB_OUTPUT
```
