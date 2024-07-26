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

| Property   | Description                                                                                                                                                                                                                                            |
| ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Conclusion | The result of a completed step **after** `continue-on-error` is applied. Possible values are `success`, `failure` `cancelled`, or `skipped`. When a `continue-on-error` step fails, the outcome is `failure`, but the final conclusion is `success`.   |
| Outcome    | The result of a completed step **before** `continue-on-error` is applied. Possible values are `success`, `failure`, `cancelled`, or `skipped`. When a `continue-on-error` step fails, the outcome is `failure`, but the final conclusion is `success`. |
