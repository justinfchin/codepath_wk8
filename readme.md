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
    - ![1](https://github.com/justinfchin/codepath_wk8/blob/master/gifs/1.gif?raw-true)
  - Details:
    - Noticed when accidentally entered pperson / address combination wrong on the login page. Noticed that the error had different font style than corect username. 
    - First go to the login page. 
    - Looking at the **Inspect Elements** you can see that the span class was different (failed vs. failure). This resulted in the bolding of **Log in was unsuccessful** for valid usernames. Looking at the **Sources** section, we can see under **styles.css** that there is **span.failure** which changes the font to bold.  
---
Vulnerability #2: 3. SQLI
  - GIF Walkthrough:
    - ![2](https://github.com/justinfchin/codepath_wk8/blob/master/gifs/3.gif?raw-true)
  - Details:
    - First go to a Salesperson. Then in the URL next to id=1 for eg. write 
    '''sql 
    ' AND SLEEP(5)=0--' 
    '''. 
      - Note: you could also replace AND with OR just be sure to remove the number next to id. 

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

## Red

Vulnerability #1: 2. IDOR
  - GIF Walkthrough:
    - ![5](https://github.com/justinfchin/codepath_wk8/blob/master/gifs/2.gif?raw-true)
  - Details:
    - Noticed when logging in as pperson, we see that there are two Salespersons who has information that should not be public. We look at **Lazy** and **Testy**. Note that they have ids **11** and **10** respectively.
    - First go to Find a Salesperson and click on the first name.
    - Then change id to 11 or 10. 
    - The other sites redirect the user to the main **Find a Salesperson** page. 

Vulnerability #2: 
  - GIF Walkthrough:
    - ![6]()
  - Details:
    - hi


## Notes

Describe any challenges encountered while doing the work

