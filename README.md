# Cipher

A shell script that will create an AWS secrets manager for your service on edge, staging, and prod.

If you say yes to needing database support, the default set of secrets are:

```json
{
  "dbMasterUser": "postgres",
  "dbMasterPassword": "password",
  "sumologicEndpoint": ""
}
```

If you say no to needing database support, the default set of secrets are:

```json
{
  "sumologicEndpoint": ""
}
```

Cipher will also add a defaul set of tags:

| Key         | Value                                  |
|-------------|----------------------------------------|
| Service     | :app_name                              |
| Environment | :environment                           |
| Cost_Code   | SP                                     |
| Cost_Center | ENG                                    |
| Name        | :app_name-secretsmanager-:environment  |

**Notes:**

* The postgres master password will be auto generated for you.
* The sumologic endpoint is left blank so terraform deploys will still work while you request an actual value from devops

## Requirements

[jq](https://stedolan.github.io/jq/) - a lightweight and flexible command-line JSON processor

```
brew install jq
```

You will also need to be able to run okta commands into various stash aws profiles. TBD...

## Installation 

TBD...

## Usage

You will need to have the Okta Verify app open on your phone. Besides that, the script will guide you on what to do.

```
./cipher project-name
```

Follow the instructions provided. When the script is complete you will have a secretsmanager setup on edge, staging, and prod.

## Example output

![Cipher](./docs/images/cipher_final_output.png)
