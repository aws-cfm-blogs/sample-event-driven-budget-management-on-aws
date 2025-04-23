## Event-Driven Budget Management on AWS

This solution provides code to implement an automated budget management system across multiple AWS accounts using CloudFormation templates. Whether you're using AWS Control Tower or AWS Organizations, this solution provides a scalable approach to cloud financial management that adapts to your organization's needs.

The following figure provides an overview of the solution:

![solutions_overview](solutions_overview.png "Solutions overview")

## Implementation Components

The solution consists of the following key components:

### Management Account Resources (budget_master_account.yaml)
- DynamoDB table to store budget values for each account
- Lambda function that processes DynamoDB stream events
- IAM roles for cross-account access

### Spoke Account Resources (budget_spoke_account.yaml)
- AWS Budget resource with configurable thresholds
- SSM Parameter Store integration
- EventBridge rules for budget updates
- Required IAM roles for automation

## Deployment Parameters

### Management Account Template
- `SSMBudgetParameter`: SSM parameter path for budget values
- `SpokeRoleName`: Name of the role to assume in spoke accounts

### Spoke Account Template
- `ManagementAccountId`: AWS Account ID of the management account
- `EmailRecipient`: Email address for budget notifications
- `BlogBudgetsThreshold`: Default budget threshold value

## Implementation and Operation Instructions
1. Deploy the management account resources with the required parameters.
2. Deploy the spoke account resources with the required parameters.
3. Locate the DynamoDB table in the management account and add an entry for the spoke account ID and budget.

## Error Handling

Common errors and resolutions:
- Budget amount validation errors: Ensure budget values are valid numeric values
- Cross-account access errors: Verify IAM roles and trust relationships are properly configured
- SSM Parameter updates: Confirm proper permissions for parameter updates in spoke accounts


## Security

See [CONTRIBUTING](CONTRIBUTING.md#security-issue-notifications) for more information.

## License

This library is licensed under the MIT-0 License. See the LICENSE file.

