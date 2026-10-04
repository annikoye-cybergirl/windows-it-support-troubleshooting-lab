# Incident 01 — DNS and Internet Connectivity Troubleshooting

## User Report

A user reported that they were unable to access websites from their
Windows workstation.

## Environment

- Operating System: Windows 11 Pro
- Device: VirtualBox Virtual Machine
- Network Configuration: NAT
- Lab Device: WIN-ITLAB01

## Initial Symptoms

The user reported an issue with internet connectivity.

## Investigation

The following commands were used:

```cmd
ipconfig
ping 8.8.8.8
ping google.com
