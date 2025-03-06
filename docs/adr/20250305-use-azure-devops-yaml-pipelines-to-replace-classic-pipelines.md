# Use Azure DevOps YAML Pipelines to Replace Classic (GUI) Pipelines

- Status: draft
- Deciders: Ashley Keller
- Date: 2025-03-06
- Tags: pipelines azure

Technical Story: [Determine Alternatives to GUI pipeline interface](https://qodexsolutions.atlassian.net/browse/HRE-316)

## Context and Problem Statement

According to [Microsoft](https://devblogs.microsoft.com/devops/disable-creation-of-classic-pipelines/), Classic Pipelines (also known as GUI) aren't officially being depricated, they are not the recommended pipelines to use. The Classic Pipelines are easier to configure and use at first, but become more difficult to maintain as the project complexity grows. They are also missing some basic security and versioning that are provided elsewhere.

## Decision Drivers

- The recommended solution should provide a way for the pipeline code to be kept in source control.
- The recommended solution should provide a way for changes to the pipeline to be reviewed.
- The recommended solution should provide a way for pipeline runs to be approved and checks to be met.

## Considered Options

- Classic Pipelines
- YAML Pipelines

## Decision Outcome

Chosen option: "YAML Pipelines", because it is the recommended approach from Microsoft. It also provides additional functionality missing from Classic and Release Pipelines that will make the pipelines more secure and easier to manage.

### Positive Consequences

- We will better align with recommendations from Microsoft.
- Getting pipeline configuration into source control will increase security and store historical context for the pipelines.
- We will gain additional features that YAML pipelines provide that are missing from Classic and Release pipelines.

### Negative Consequences

- It will take some work to migrate Classic and Release Pipelines over to YAML.
- Any sort of change to the pipelines does introduce some risk that something will not be configured correctly.

## Pros and Cons of the Options

### Classic Pipelines

One option is to continue using classic (GUI) pipelines.

- Good, because no work would need to be done.
- Bad, because some pipelines already being used are Classic while others are YAML.
- Bad, because the pipeline is not stored in source control anywhere. Once a change is made, it is active and the previous state of the pipeline is gone.
- Bad, because there is no built in way to review changes to the pipeline. Once a change is saved, it is active.
- Bad, because Microsoft is encouraging users to move away from Classic Pipelines whenever possible.

### YAML Pipelines

One option is to move to Azure DevOps' YAML Pipelines.

- Good, because it would make all pipelines consistent. There would no longer be some Classic Piplelines, some Release Pipelines, and some YAML pipelines.
- Good, because the pipeline code is stored in source control. When changes are made, the previous state of the pipeline still exists in source control and can be referenced later.
- Good, because the pipeline code is in source control, code reviews can be used. If the code branch is protected, it would be impossible to directly merge in changes to the pipeline without a code review.
- Good, because YAML pipelines have additional features that are missing from Classic Pipelines and Release Pipelines including approvals, checks, resource access management, and runtime parameters.
- Good, because YAML pipelines are the recommended approach from Microsoft.
- Bad, because pipelines that have been built using Classic Pipelines, and Release Pipelines, will need to be re-created using YAML.

## Links

- [Microsoft Blog - Disable Creation of Classic Pipelines](https://devblogs.microsoft.com/devops/disable-creation-of-classic-pipelines/)
- [Microsoft Documentation - YAML vs Classic Pipelines](https://learn.microsoft.com/en-us/azure/devops/pipelines/get-started/pipelines-get-started?view=azure-devops)
- [Microsoft Documentation - Migrate from Classic Pipelines](https://learn.microsoft.com/en-us/azure/devops/pipelines/release/from-classic-pipelines?view=azure-devops)