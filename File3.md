# Leaked AWS Credentials Response Playbook

How to react to leaked Amazon Web Services (AWS) credentials.

## What

Amazon Web Services (AWS) credentials verify who you are and if you have permission to access the resources that you are requesting inside AWS. They can be just a combination of username and password, but can also include access keys. All of those are private information. If this information is exposed, unauthorized people may impersonate an authorized person to cause damage to Nubank's cloud-based systems.

## How
This is a playbook with instructions designed to limit Nubank’s exposure in case of a possible attack.

Some of these steps require contacting someone with the ability to administer IAM permissions (IAM admin). To find the right person, run:
```sh
$ nu sec iam show group infosec-permissions-admin
```


### Instructions
This response has 4 aims:

1. Revoking permissions from affected user.
2. Communicating steak holders.
3. Creating new credentials for affected user.
4. Communicating affected user about the new credentials.

![This UML sequence diagram represents the process and the participants.](https://lh3.googleusercontent.com/mCrZJHBLk3MGRsldDCXl-XL1XtwLRN0e3I2ptIXci51POVnLlNN8AQKwPrSBh0Y5ZcT_wREkyCRZuXNG7FzPIcDiPfZmgbl8ju9cscYTAsI08ADTgZQJEqjkykgeypuP1hUFERYXo4Y=w2400)
*Above is a UML representation of the Leaked AWS Credentials Response workflow presented below.*


#### 1. Remove all permissions from affected user (do not revoke credentials).
1.1 Contact an IAM admin and ask them to remove all inline policies from the affected user by running:
```sh
$ nu iam disallow <user> Source
```

1.2 Ask the IAM admin to find all IAM groups for the affected user and remove the user from all groups by running:
```sh
$ nu sec iam show <user>
$ nu sec iam remove <user> <groups>
```

#### 2. Communicate with relevant stakeholders
2.1 Use Slack to send a direct message to the affected user:
>"Your AWS permissions has been temporarily suspended pending an investigation into a possible compromise. If you have questions about this, please get in touch with Infosec. Please keep the incident private until you get an all clear from Infosec."

2.2 Use Slack to send a direct message to the Tech Manager or Engeneering Manager of the affected user:
>"There has been wrongful activity using this engineer's AWS account, please inform them that permissions associated with it have been temporarily blocked. Direct them to further understand the incident . Please advise them to keep the incident private until all clear from Infosec."

#### 3. Revoke the affected AWS credentials.
3.1 Contact IAM admin and ask them to disable/delete the affected credentials using the AWS console. ???

#### 4. Ask the IAM admin to generate via AWS console new credentials and a new key-pair for the affected user.

#### 5. Use Slack to send a direct message to the affected user attaching the new credentials. 
5.1 Along with the key pair, instruct the user to update AWS keys everywhere they are referenced (e.g., .bash_profile). There are instructions [here](https://github.com/nubank/nudev/blob/master/setupnu.sh) and [here](https://github.com/nubank/nu-setup).
