# lza-accelerator

### OU Structure
<img width="635" alt="image" src="https://github.com/user-attachments/assets/479ef827-dd11-4f07-8a3f-2dca4fd7fdd2" />

- The `Root` OU houses the Management account. LZA is installed into this account & orchestrates CloudFormation stacks via CDK across other accounts
- The `Security` OU houses the `Log Archive` & `Audit / Security Tooling` accounts. 
	[[AWS Control Tower]] provisions this OU & related accounts automatically
- The `Infrastructure` OU houses the `Network` & `Shared Services` accounts.
	A central Network account is used to house & manage core network infrastructure. Things like (central) Transit Gateways, VPCs, DCs, S2S VPNs
	The Shared Services account is used for organisations that have resources not core. Things like bastion hosts, shared apps, etc
- Workload accounts are not housed in OUs, unless a new OU structure is defined in `organization-config.yaml`. Additional workload accounts can be defined in `accounts-config.yaml`

### Components
<img width="630" alt="image" src="https://github.com/user-attachments/assets/49f99835-05db-442b-a8ba-ae80b38a5491" />

- Installer pipeline
- CodeBuild project
	- Multiple CodeBuild stages are involved
- SNS topics can be used to alert on core pipeline events
- CodeCommit repository `aws-accelerator-config`
