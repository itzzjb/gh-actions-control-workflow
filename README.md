# Controlling Workflows

We are able to write workflows that executes from the start to the end. When a step of a job fails in the workflow starting from the next step and the remainder of the workflow won't execute because the workflow fails.

But we may need to continue executing steps even if a step fails, and we may need to some steps to execute if a certain step fails. Simply we need more control over when exactly which job and step executes in our workflow.

- Running Jobs and Steps conditionally
- Running Jobs with a Matrix
- Re-Using Workflows

### Conditional Jobs & Steps

| Jobs                                 | Steps                                        |
| ------------------------------------ | -------------------------------------------- |
| Conditional execution via `if` field | Conditional execution via `if` field         |
|                                      | Ignores errors via `continue-on-error` field |

We can add the conditions via `if` and `continue-on-error` fields with the help of expressions.

### Conclusion and Outcome

[For more details](https://docs.github.com/en/actions/learn-github-actions/contexts#steps-context)

| Property   | Description                                                               |
| ---------- | ------------------------------------------------------------------------- |
| Conclusion | The result of a completed step **after** `continue-on-error` is applied.  |
| Outcome    | The result of a completed step **before** `continue-on-error` is applied. |

### Special IF Condition Functions

| Function    | Description                                                |
| ----------- | ---------------------------------------------------------- |
| failure()   | Returns `true` when any previous step or job failed        |
| success()   | Returns `true` when none of the previous steps have failed |
| always()    | Causes the step to always execute. even when cancelled     |
| cancelled() | Return `true` if a workflow has been cancelled             |

These functions can be used in our conditions, to ensure that certain steps only run when other steps `failed` or `succeeded` of they always run or only run if a workflow has been `cancelled`.
