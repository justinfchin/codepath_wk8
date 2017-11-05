# Project 8 - Pentesting Live Targets

Time spent: **X** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: 1. Username Enumeration
  - GIF Walkthrough:
    - ![1]()
  - Details:
    - Looking at the 'Inspect Elements' you can see that the span class was different (failed vs. failure). This resulted in the bolding of 'Log in was unsuccessful' for valid usernames. Looking at the 'Sources' section, we can see under 'styles.css' that there is 'span.failure' which changes the font to bold.  

Vulnerability #2: 
  - GIF Walkthrough:
    - ![2]()
  - Details:
    - hi
---
## Green

Vulnerability #1: 
  - GIF Walkthrough:
    - ![3]()
  - Details:
    - hi

Vulnerability #2: 
  - GIF Walkthrough:
    - ![4]()
  - Details:
    - hi

---
## Red

Vulnerability #1: 
  - GIF Walkthrough:
    - ![5]()
  - Details:
    - hi

Vulnerability #2: 
  - GIF Walkthrough:
    - ![6]()
  - Details:
    - hi


## Notes

Describe any challenges encountered while doing the work

