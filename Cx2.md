# CVE Report - Pre-Authentication Command Injection Vulnerability in Motorola CX2 Routers (Affected Versions Less Than or Equal to 1.0.2)

## Vulnerability Title

Command Injection Vulnerability in Motorola CX2 Routers (Affected Versions Less Than or Equal to 1.0.2)

## Vulnerability Description

A command injection vulnerability exists in Motorola CX2 routers with versions less than or equal to 1.0.2. This vulnerability occurs in the `SetWLanRepeaterPwSettings` module within the `prog.cgi` file. The system directly calls the `system` function to execute commands when setting the uplink WiFi password for the repeater, without any filtering. This leads to a pre-authentication command injection vulnerability, provided that the router is in repeater mode.

## Reproduction Steps

1. Access the router's web page without logging in.

![image-20240827111023221](https://github.com/user-attachments/assets/8598af38-4908-41c8-8d39-eecd743366a0)

2. Visit http://192.168.51.1//MobileProblem_Key.html and inject a command:

![image-20240827111142599](https://github.com/user-attachments/assets/84a5194e-2858-4858-89f6-12c36761f66d)

3. After injecting the command, the corresponding information will appear at the bottom of the page:

![image-20240827111246465](https://github.com/user-attachments/assets/75d2b027-8f88-48e3-8f12-b80b9c73d8fe)

## Cause Analysis

The cause of this vulnerability is that the `SetWLanRepeaterPwSettings` module within the `prog.cgi` file does not adequately validate or filter user input, directly calling the `system` function to execute commands. This insecure practice allows an attacker to inject arbitrary commands without authentication.

## Affected Versions

- Motorola CX2 router version 1.0.2 and below.

## Suggested Fix

It is recommended to update the Motorola CX2 router to the latest firmware version to fix this vulnerability. Please contact Motorola technical support for detailed patch information and fixes.

## Contact Information

- Reporter: N1nEmAn
