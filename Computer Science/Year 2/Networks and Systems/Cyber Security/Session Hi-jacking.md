#nas 
# Cookies

Way for server to store info on local host
- loaded each time host visits 

Attacker stealing cookie can access info and replay authentication info
- can be stolen locally or via XSS 

# Coursework Explanation Examples 

>[!success] Excellent Example (10/10)
>"I setup a webhook using webhook.site to capture data exfiltrated by XSS. Injected JS code with XMLHttpRequest to send page data to this webhook. Ran simulate_root.php and checked webhook requests for the flag. Much harder than others. To improve, use CSP, sanitise inputs, and set HttpOnly cookies."
- details all techniques used and steps taken to find flag 
- recommendation uses specific terms and techniques for a comprehensive guide to improve security

>[!failure] Bad Example (0/10)
>"This was a very difficult flag to get as it involved several steps and lots of exploration. To do this I created a server using python that intercepted the communications between the root and the login page. The details gained allowed me to login."
- emotional explanation unnecessary
- techniques to find flag explained poorly with little detail 
- no recommendation to improve security 

>[!attention] Middling Example (7/10)
>"Login to the page and use command <?php system('');?> to access js file, then manually use phantomjs to get the password for the root. Lastly, login as root and flag is displayed. It was hard to find with multiple steps, and it should be protected by storing password on server instead of js file."
- explanation excellent, solution method different to intended but works well
- recommendation is good but some inaccuracies (password was on server)

>[!failure] Bad Example (4/10)
>"The flag tests web exploitation and privilege escalation  
Hard flag  
Accessed the site on my browser, using ssh [localhost](http://localhost/). I injected php code to obtain the D file. After decoding, I found the shuffled list. Rearranged to get password and logged in  
Input validation/sanitation to prevent code injection"
- irrelevant info e.g. using localhost.
- vague recommendation that does not link to the original problem

>[!failure] Bad Example (2/10)
>"This was a very difficult flag, I logged in with the credentials provided and then ran a script to gain root access, after combining both XSS and SQL techniques I found the flag. Stricter authorisation and filtering of scripts can improve security."
- information is incorrect (no SQL required) so explanation is a fail 
- root access is not possible so do not say this 
- recommendation basic with no specific details or techniques 

