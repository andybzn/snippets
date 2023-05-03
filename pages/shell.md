# 🐚 Shell

Stuff for the shell

## Use AWS SSO with Terraform 

You need to export the current, logged-in profile name as an environment variable before running the terraform command

```bash 
AWS_PROFILE="{profile_name}" terraform {command}
```
