# 🐚 Shell

Stuff for the shell

## Use AWS SSO with Terraform 

You need to export the current, logged-in profile name as an environment variable before running the terraform command

```bash 
AWS_PROFILE="{profile_name}" terraform {command}
```

## Reset MacOS Ventura Window Manager

Useful when connecting an ultrawide monitor (5120x1440) after a reboot. Unplug the monitor, execute the command, and re-connect.

```bash
sudo sleep 20 ; sudo kill -9 $(pgrep WindowServer)
```
