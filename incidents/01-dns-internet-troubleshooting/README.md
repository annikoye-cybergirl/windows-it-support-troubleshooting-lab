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

Step 1 — IP Configuration
The ipconfig command was used to examine the workstation's network configuration, including:

-IPv4 address
-Default gateway
-DNS configuration

The workstation had a valid network configuration.

Step 2 — IP Connectivity Test

The following command was used:

ping 8.8.8.8

The test was successful.

This confirmed that the workstation could communicate with an external IP address and that general network connectivity was functioning.

Step 3 — DNS Resolution Test

The following command was used:

ping google.com

The test initially failed with:

Ping request could not find host google.com

This indicated that the workstation could reach the Internet but could not resolve the domain name.

Step 4 — DNS Configuration Investigation

The IPv4 DNS configuration was reviewed through:

Ethernet → Properties → Internet Protocol Version 4 (TCP/IPv4) → Properties

Invalid DNS server addresses were configured as part of the controlled troubleshooting scenario.

The DNS configuration was identified as the source of the problem.

5. Findings

The troubleshooting tests showed that:

The workstation had a valid IP configuration.
External IP connectivity was working.
DNS name resolution was failing.
The problem was therefore isolated to DNS rather than general network connectivity.

The issue was successfully isolated by testing an external IP address separately from a domain name.

6. Root Cause

The workstation was configured with invalid DNS server addresses.

Because the DNS servers were invalid, the workstation could communicate with external IP addresses but could not translate domain names such as google.com into IP addresses.

7. Resolution

The incorrect DNS configuration was removed.

The network adapter was returned to automatically obtain DNS server information.

The DNS resolver cache was then cleared using:

ipconfig /flushdns
8. Verification

After restoring the DNS configuration, the following command was used:

ping google.com

The domain resolved successfully and the workstation received replies.

This confirmed that DNS name resolution had been restored and the issue was successfully resolved.

9. Evidence
IP Configuration

The workstation's network configuration was reviewed using ipconfig.

Screenshot: IP configuration and network details.

IP Connectivity Test

The workstation successfully reached the external IP address 8.8.8.8.

Screenshot: Successful ping 8.8.8.8 test.

DNS Resolution Failure

The workstation initially failed to resolve google.com.

Screenshot: DNS resolution failure showing:

Ping request could not find host google.com
DNS Resolution Restored

After correcting the DNS configuration, google.com resolved successfully.

Screenshot: Successful ping google.com after the fix.

10. Troubleshooting Methodology

The following structured troubleshooting approach was used:

Identify the reported problem.
Check the workstation's IP configuration.
Test connectivity using an external IP address.
Test DNS resolution using a domain name.
Compare the results to isolate the problem.
Investigate the DNS configuration.
Correct the DNS configuration.
Clear the DNS resolver cache.
Retest connectivity.
Document the root cause and resolution.
11. Lessons Learned

This incident demonstrated the importance of separating network connectivity problems from DNS resolution problems.

Testing an IP address and a domain name independently made it possible to identify that the workstation had Internet connectivity but was unable to resolve domain names.

Technical Skills Demonstrated
Windows 11 troubleshooting
IPv4 configuration
DNS troubleshooting
Network connectivity testing
Command Prompt
ipconfig
ping
ipconfig /flushdns
Root cause analysis
Incident documentation
Problem-solving
Technical communication
12. Outcome

The DNS resolution issue was successfully identified, corrected, and verified.

The workstation was able to resolve domain names and communicate with external services after the DNS configuration was restored.
