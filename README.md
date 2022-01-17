# **Research**

# Table of Contents
1. [Introduction to XSS](#XSSIntroduction)
2. [What are the different types Of XSS attacks?](#XSSAttacks)
    1. [Reflected XSS](#ReflectedXSS)
    2. [Stored XSS](#StoredXSS)
    3. [DOM-Based XSS](#DOMBasedXSS)
3. [How do you prevent XSS attacks?](#XSSPrevent)
4. [Conclusion](#XSSConclusion)
3. [References](#XSSReferences)

# Cross-Site Scripting (XSS)

# Introduction <a id="XSSIntroduction"> </a>  
Cross-site scripting is a type of attack where the attacker injects malicious scripts into a website.  
The attack is carried out by using a web application to send malicious scripts to a different user.  
It XSS is one of the most common vulnerability  on the web taking up almost 40% of all cyberattacks in 2019.  
XSS uses a vulnerability  in a web application where the web applisation doesn't validate or encode a user's input.  
The user isn't able to distinguish as XSS script from a non-malicious script, because the origin of both   
scripts are the same so the user has reason to assume that the script is malicious. This research is written using  
the DOT-framework. The research pattern that was used was Library Research. And the research method that was used is  
Literature Study. We used this method and pattern because the internet has a substantial amount of information about  
this topic which we can use. 


# Research Questions<a id="XSSQuestions"></a>  
How does react prevent XSS attacks?  
  
Sub-questions:  
- What are the different types of XSS attacks?  
- How do you prevent XSS attacks?  
  
# the different types of XSS attacks<a id="XSSAttacks"></a>
There are mainly 3 different types of XSS. Which are: 
Reflected XSS, Where the vulnerability lies in the Http request sent.  
Stored XSS, Where the vulnerability lies in the data being stored to the datbase.  
DOM-Based XSS, Where the vulnerability lies in the client-side code.  

## **Reflected XSS**<a id="ReflectedXSS"> </a>
Reflected XSS (or Non-Persistent XSS) is the simplest variant of different XSS types.  
The attack is carried out by inserting a malicious script into a HTTP Request ususaly in the form  
of a URL. It only requires the user to click on the URL and the attack is carried out.  

| ![image](/Images/reflected-xss.png)|
|:--:|
| *(fig 1.)*|

Example:  
Let's say there is a website which shows the unfiltered URL query on the page.  
```
URL: http://www.example.com/input?q=test  
HTML: <p>Your input was test </p>  
Output: Your input was test
```    

Now let's inject a malicious script into this URL.  
```
URL: http://www.example.com/input?q=test+%3Cscript%3EMalicious_Script()%3C/script%3E  
HTML: <p>Your input was test<script>Malicious_Script()</script></p>  
Output: Your input was test  
```  
If the user clicks on the second link he will run the malicious script.  
But the user will not notice any visible difference on the website.

## **Stored XSS <a id="StoredXSS"></a>**  
Stored XSS (a.k.a. Persistent XSS or Second-Order XSS) is a type of attack where the script is stored in the application's database.   
The malicious script can be submitted to the application via HTTP requests, for example: comments, usernames, user descriptions, etc.  
The user doesn't even need to click the wrong link for the malicious script to get to them, as the script is requested by them expecting  
it to be normal data.

| ![image](/Images/stored-XSS.png)|
|:--:|
| *(fig 2.)*|  

Example:
Let's say we have a website where you can create blog posts. And the blog post in open a stored XSS vulnerablilty.
```
Input: This is a new blogpost
Database: This is a new blogpost
HTML: <p>This is a new blogpost</p>
Output: This is a new blogpost
```  
Now let's inject a malicious script to the input
```
Input: This is a new blogpost <script>Malicious_Script()</script>
Database: This is a new blogpost <script>Malicious_Script()</script>
HTML: <p>This is a new blogpost <script>Malicious_Script()</script></p>
Output: This is a new blogpost
```    
Now again we see the same output from both input's but the second input has again a malicous script hidden in it's HTML.  
For the user there is no visible difference between both input's.

## **DOM-Based XSS <a id="DOMBasedXSS"></a>**  
DOM-based XSS (also known as DOM XSS) arises when an application contains some client-side JavaScript that  
processes data from an untrusted source in an unsafe way, usually by writing the data back to the DOM.

Example:
Let's say you have a website that lets your input something and then returns it on the webpage.
```
Code:  
var input = document.getElementById('input').value;
var ouput = document.getElementById('ouput');
ouput.innerHTML = 'Your input was: ' + input;  

Input: Test
Output: Test
```
Now let's insert our malicious script
```
Code:  
var input = document.getElementById('input').value;
var ouput = document.getElementById('ouput');
ouput.innerHTML = 'Your input was: ' + input;  

Input: Test<script>Malicious_ScriptS()</script>
Output: Test
```
There is no difference between both outputs but you have injected a malicious script in the second example.  
In a typical case, the input field would be populated from part of the HTTP request, such as a URL query string parameter,  
allowing the attacker to deliver an attack using a malicious URL, in the same manner as reflected XSS.
| ![image](/Images/DOM-Based-XSS.png)|
|:--:|
| *(fig 3.)*|  
# How do you prevent XSS attacks?<a id="XSSPrevent"></a>
Because there are multiple types of XSS, there are multiple ways you can prevent XSS attacks.  
But the most effective way to combat any XSS attack is to validate every user input. When a user input  
is displayed on a webpage you remove any html tags and when a user input is saved to the database you remove any SQL Query.  
For more specific XSS preventions methods you could always use the 
<a href="https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html">OWASP Cross Site Scripting Prevention Cheat Sheet</a>.
 
# Conclusion<a id="XSSConclusion"></a>

# References<a id="XSSReferences"></a>
https://owasp.org/www-community/attacks/xss/  

https://portswigger.net/web-security/cross-site-scripting 

https://www.veracode.com/security/xss

https://financialit.net/news/cybersecurity/cross-site-scripting-xss-makes-nearly-40-all-cyber-attacks-2019#:~:text=Cross%2DSite%20Scripting%20(XSS),All%20Cyber%20Attacks%20in%202019&text=10%3A31%20am-Cyber%2Dattacks%20have%20targeted%20nearly%2075%20percent%20of%20large%20companies,over%20the%20last%20twelve%20months.  

*(fig 1.)* https://miro.medium.com/max/1050/1\*o_asKsD_JqunhqggHoxodw.png  
*(fig 2.)* https://www.imperva.com/learn/wp-content/uploads/sites/13/2019/01/sorted-XSS.png  
*(fig 3.)* https://miro.medium.com/max/1050/1\*yuRkBR6YroYLCGpka9KdRA.png  