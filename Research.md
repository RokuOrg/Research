# **Research**

# Table of Contents
1. [Cross-Site Scripting](#XSS)
    1. [What is Cross-Site Scripting (XSS)](#WhatIsXSS)
    2. [Different Types Of XSS Attacks](#XSSAttacks)
        1. [Reflected XSS](#ReflectedXSS)
        2. [Stored XSS](#StoredXSS)
        3. [DOM-Based XSS](#DOMBasedXSS)
    3. [References](#References)
2. [Concurrency](#Concurrency)

# Cross-Site Scripting (XSS) <a id="XSS"></a>

- ## What is Cross-Site Scripting <a id="WhatIsXSS"> </a>
    Cross-site scripting is a type of attack where the attacker injects malicious scripts into a website.  
    The attack is carried out by using a web application to send malicious scripts to a different user.  
    It XSS is one of the most common vulnerability  on the web taking up almost 40% of all cyberattacks in 2019.  
    XSS uses a vulnerability  in a web application where the web applisation doesn't validate or encode a user's input.  
    The user isn't able to distinguish as XSS script from a non-malicious script, because the origin of both   
    scripts are the same so the user has reason to assume that the script is malicious.  

- ## The Different Types of XSS Attacks<a id="XSSAttacks"></a>
    There are mainly 3 different types of XSS. Which are: 
    Reflected XSS, Where the vulnerability lies in the Http request sent.  
    Stored XSS, Where the vulnerability lies in the data being stored to the datbase.  
    DOM-Based XSS, Where the vulnerability lies in the client-side code.  

    ### **Reflected XSS**<a id="ReflectedXSS"> </a>
    Reflected XSS (or Non-Persistent XSS) is the simplest variant of different XSS types.  
    The attack is carried out by inserting a malicious script into a HTTP Request ususaly in the form  
    of a URL. It only requires the user to click on the URL and the attack is carried out.  
    
    | ![image](/Images/reflected-xss.png)|
    |:--:|
    | *(fig .1)*|

    Example:  
    Lets say there is a website which shows the unfiltered URL query on the page.  
    ```
    URL: http://www.example.com/input?q=test  
    HTML: <p>Your input was test </p>  
    Output: Your input was test
    ```    

    Now lets inject a malicious script into this URL.  
    ```
    URL: http://www.example.com/input?q=test+%3Cscript%3EMalicious_Script()%3C/script%3E  
    HTML: <p>Your input was test<script>Malicious_Script()</script></p>  
    Output: Your input was test  
    ```  
    If the user clicks on the second link he will run the malicious script.  
    But the user will not notice any visible difference on the website.

    ### **Stored XSS <a id="StoredXSS"></a>**  
    Stored XSS (a.k.a. Persistent XSS or Second-Order XSS) is a type of attack where the script is stored in the application's database. 

    ### **DOM-Based XSS <a id="DOMBasedXSS"></a>**

- ## How To Carry Out A XSS Attack?

- ## What Are Different Types Of XSS Vurnerabilities?

- ## How To Prevent XSS Attacks?

- ## XSS Protection In React.js

- ## References<a id="References"></a>
    https://owasp.org/www-community/attacks/xss/  
    
    https://portswigger.net/web-security/cross-site-scripting
   
    (twitter xss) https://www.youtube.com/watch?v=zv0kZKC6GAM  
    
    https://www.veracode.com/security/xss

    https://financialit.net/news/cybersecurity/cross-site-scripting-xss-makes-nearly-40-all-cyber-attacks-2019#:~:text=Cross%2DSite%20Scripting%20(XSS),All%20Cyber%20Attacks%20in%202019&text=10%3A31%20am-Cyber%2Dattacks%20have%20targeted%20nearly%2075%20percent%20of%20large%20companies,over%20the%20last%20twelve%20months.  
    
    *(fig 1.)* https://blog.sqreen.com/reflected-xss/#:~:text=A%20reflected%20XSS%20  
# Concurrency <a id="Concurrency"></a>