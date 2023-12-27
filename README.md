# Huawei iBMC Fan Control script

This repository contains an script for a docker image and a SystemD service to periodically monitor
CPU temperature and adjust fans.

## Configure iBMC

In order for the script to be able to set the configuration of the fans, you
need to enable SNMP v2c and configure a community key.

To do so:

1. Log in into your iBMC
2. Go to `Configuration` > `System`
3. Enable `SNMPv2c`
4. Put a password-like value in `Read/Write Community` and in the `Confirm Read/Write Community` fields.
5. Save

**Warning:** Do not share your community value. It can be used to access your
iBMC configuration and change it. It is a password.

docker run --rm --privileged -e COMMUNITY=YOUR_SNMPv2_PASSWORD -e IBMC_IP=YOUR_IBMC_IP asturking/huawei-fan-controller:latest

## Systems tested with:

- Huawei RH2288H v3
