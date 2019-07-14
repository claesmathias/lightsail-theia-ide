# lightsail-theia-ide
Cloud IDE

## Edit config
Edit the following lines in `user-data.txt` 

## Create instance
Create AWS Lightsail instance via [AWS Lightsail CLI](https://docs.aws.amazon.com/cli/latest/reference/lightsail/index.html "AWS Lightsail CLI")
```
aws lightsail create-instances --instance-names "theia-vm" --availability-zone eu-west-2a --blueprint-id centos_7_1901_01 --bundle-id medium_2_0 --user-data file://user-data.txt
```
You can find the script in `/var/lib/cloud/instance/user-data.txt` on the instance

## Configure instance
### Open ports
```
aws lightsail open-instance-public-ports --port-info fromPort=443,toPort=443,protocol=TCP --instance-name theia-vm
```

## Aftercare
Download the key file [here](https://lightsail.aws.amazon.com/ls/webapp/account/keys "AWS Lightsail keys")
```
chmod 600 LightsailDefaultKey-eu-west-2.pem
ssh -i LightsailDefaultKey-eu-west-2.pem centos@DOMAIN_URL
```
