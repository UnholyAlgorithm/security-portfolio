# Investigating Potential Deployment Threat

## Scenario
A junior intern was given temporary contributor access to deploy a test environment before the weekend. The deployed environment did not follow governance standards, triggering related policy alerts. 

## Environment
A live Microsoft Azure training tenant with reader access.

## Investigation
The core. Numbered steps IN YOUR OWN WORDS: what you looked at, what you found, what you concluded at each step. 6 to 12 screenshots of meaningful moments (portal views, query results, before/after).

1. After logging in and navigating to the Resource Manager, verifying the naming conventions of the existing resource groups.

<img width="1917" height="569" alt="resourcemanagerclick" src="https://github.com/user-attachments/assets/ebd0f7ef-7606-4f23-b128-e4146799b526" />

2. I then identified the violating resource group, and verified tags of the deployed resource.
   
<img width="1520" height="736" alt="interntags" src="https://github.com/user-attachments/assets/dc87c184-b304-4cce-aab2-4db4d9af56b1" />

4. Navigated to "Deployments" finding the deployment that violated naming convention policy.
   
<img width="1920" height="1080" alt="deploymentscheck" src="https://github.com/user-attachments/assets/09287071-19d5-4ca4-9c7c-d95395872f22" />
<img width="1595" height="573" alt="deploymentoverview" src="https://github.com/user-attachments/assets/99f44a0d-f164-4449-af0b-c76e1f83dbdb" />

5. Navigated to the "Policies", "Assignments", then "Naming Convention" and identified that the policy effect type is set to "Audit," allowing noncompliant resource creation.

<img width="1913" height="729" alt="policyblur" src="https://github.com/user-attachments/assets/1984c6f4-0b48-4a0d-b7eb-28ad9fd3eeb1" />
<img width="1179" height="518" alt="complianceview" src="https://github.com/user-attachments/assets/6328f6bf-d5f0-4ca5-8d98-4d0e6d712127" />

## What broke / what surprised me
What surprised me is the amount of information gathered from simple tags, attribute, and timestamps. Microsoft Azure leaves generous amounts of information throughout the environment. What started as potential Shadow IT was investigated and identified from what Azure records.

## Findings and recommendations
Found a resource and deployment that violated naming convention policy. Naming conventions allow for readability and accountability. Failing to adhere to policies can create confusion, or be an indication of possible threats. Recommendation to change policy rule from "Audit" to "Deny" to strictly enforce this requirement.

## What I learned
Azure tags made it easy to identify ownership of related deployments, and were crucial in following an audit trail and creating the timeline. Azure's Compliance section identifies policy violations and what scopes are affected. The policy having an Audit effect type allowed the intern to create and deploy resources that violated the policy and flagged them instead of blocking them with the Deny effect type.
