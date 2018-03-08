+++
title = "Assignment 3"
description = "Securing application"
date = 2018-03-01T22:17:13+01:00
weight = 20
draft = false
bref = "Assignment 3"
toc = false
+++

## The vulnerabilities

  1. Website impersonation (hijacking)
  2. Possible bruteforce login attacks
  3. Possible Cross Site Scripting (XSS) through user input
  4. Possible repudiation
  5. (Jens)
  6. Website impersonation because of weak HTTPS configuration

## Our mitigations

  1. Strict TLS
  2. Lock-out policy
  3. Input sanitizing
  4. Traffic logging
  5. Password reset
  6. Enhardened HTTPS-configuration

### Strict TLS

The new version of the website uses the [Caddy webserver](https://caddyserver.com/), a webserver with automatic TLS with strong configurations by default. It explicitly excludes soms cipher-suites that are concered as "not secure" today. TLS is automatically configured using the ACME protocol (Let's Encrypt). Caddy handles certificate renewal so that the website always uses a valid certificate. It has even builtin man-in-the-middle (MITM) attack detector that can detect possible website impersonations. *OWASP A6:2017 - Security Misconfiguration*

### Lock-out policy
The lock-out policy is used in the application to protect ourselves from attacks on users accounts. 
Like the iCloud hack back in 2014 there was a possibility to make unlimited attempts to login with user credentials.
With our lock-out policy users have 3 tries after that, their account will be locked and they need to contact the site admin. *OWASP A2:2017 - Broken Authentication*

### Input sanitizing

All input from any source goes through a sanitizer. This is a small Express.js middleware module that sanitizes all (user) input before we do our business logic. *OWASP A7:2017 - Cross-Site Scripting (XSS)*

### Traffic logging

All traffic, inbound and outbound, of the webserver is logged in a (distributed) log file in conjunction with a timestamp, (possible) logged-in user, IP adress, complete URI with parameters and critical HTTP headers. *OWASP A10:2017 - Insufficient Logging & Monitoring*

### Password reset
Not all hackers take what they need and leave. Occasionally hackers may continue accessing your account, either to monitor your data or continue stealing information over time. It can be difficult to figure out if someone else is using your account, so by changing your password consistently, you reduce the risk that other people will have frequent access to your accounts. Consider changing your password every few months to be on the safe side.

Therefor we encourage our site users to change their password often to remain safe for breaches. This is helped by the function to reset their password in case they forgot a new password because of the different passwords. *OWASP A2:2017 - Broken Authentication*

### Enhardened HTTPS-configuration

The HTTPS configuration is enhardened. The most critical Secure Headers of the [OWASP Secure Headers Project](https://www.owasp.org/index.php/OWASP_Secure_Headers_Project) are implemented and included in every request. This contains the following:

  - Strict-Transport-Security (with max-age 31536000)
  - X-Frame-Options set to deny
  - X-XSS-Protection on with mode block.
  - X-Content-Type-Options nosniff (don't sniff the MIME type from the payload, this can be dangerous)
*OWASP A6:2017 - Security Misconfiguration*
