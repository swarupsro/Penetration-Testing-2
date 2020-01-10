Table of Contents

    What is Penetration Testing or Pen Testing?
    Web App Penetration Testing Types:
    1. Internal Penetration Testing
        List of Web Application Penetration Testing Checklist
             1. Proxy Server(s) Testing
             2. Spam Email Filter Testing
            3. Network Firewall Testing
            4. Security Vulnerabilities Testing
            5. Credential Encryption Testing
            6. Cookie Testing
            7. Contact Form Testing
            8. Open Ports Testing
            9. Application Login Page Testing
            10. Error Message Testing
            11. HTTP Method(s) Testing
            12. Username and Password Testing
            13. Scanning File
            14. SQL Injection Testing
            15. XSS Testing
            16. Access permission testing
            17. Testing user session
            18. Brute Force Attack Testing
            19. DoS (Denial of Service) Attack Testing
            20. Browsing Directory Testing
    2. External Penetration Testing
        How Penetration Testing is performed?
            Best Penetration Testing Companies of (2018-2019)
            Certificates of penetration testing:

What is Penetration Testing or Pen Testing?

Penetration testing is the process of testing software for its security vulnerabilities by trained security experts (e.g. penetration tests or ethical hackers). The aim of such a test is to strengthen the security vulnerabilities that the software may contain, so that the hacking community does not easily exploit (or take advantage of). In Web App Pen testing, the software being tested is a web application stored on a remote server that clients can access via the Internet.

Obviously, web applications are easy targets for hackers and it is therefore imperative that web applications developers frequently perform penetration tests to ensure that their web applications remain healthy–away from various security vulnerabilities and malware attacks.

Let’s look at some of the elements in this blog that every web application test checklist should contain, so that the penetration testing process is really effective.
Web App Penetration Testing Types:

Web applications can be tested in two ways. Tests can simulate an indoor or outdoor attack.

    Internal Penetration Testing
    External Penetration Testing

1. Internal Penetration Testing

As the name suggests, internal pen testing is carried out via the LAN within the organization, which means that web applications hosted on the intranet are tested. This helps to find out whether there is any vulnerability in the corporate firewall. We always believe that attacks can only occur externally and that the internal pen test of many times is ignored or does not matter much.

Basically, it includes attacks by disgruntled employees or contractors who have resigned but are aware of internal security policies and passwords, social engineering attacks, phishing attack simulations and attacks using user privileges or abuse of an unlocked terminal.

Testing is done primarily by accessing the environment without proper credentials and determining whether. Here are the lists of internal web application Penetration Testing checklist explained in detail.
List of Web Application Penetration Testing Checklist

    Proxy Server(s) Testing
    Spam Email Filter Testing
    Network Firewall Testing
    Security Vulnerability Testing
    Credential Encryption Testing
    Cookie Testing
    Contact Form Testing
    Open Ports Testing
    Application Login Page Testing
    Error Message Testing
    HTTP Method(s) Testing
    Username and Password Testing
    SQL Injection Testing
    XSS Testing
    Access Permission Testing
    Testing user session
    Brute Force Attack Testing
    DoS (Denial of Service) Attack Testing
    Directory Browsing Testing
    File Scanning

 1. Proxy Server(s) Testing

Proxy servers play an important role in checking the traffic to your web application and highlighting any malicious activity. Therefore, make sure that the proxy servers in your network work precisely and efficiently. Tools such as Burp Proxy and OWSAP ZAP can help you achieve this task a great deal.
 2. Spam Email Filter Testing

Ensure that spam email filters work properly. Check if incoming and outgoing traffic is successfully filtered and unsolicited emails are blocked. In other words, make sure that e-mail security policy is properly implemented. Because spam is the most popular mode of attack for hackers, as we all know.
3. Network Firewall Testing

Make sure that your firewall prevents unwanted traffic to enter your web application. In addition, ensure that the security policies set up with the firewall are properly implemented. A hitch in your firewall is like sending hackers an invitation to come and hack your web app.
4. Security Vulnerabilities Testing

Conduct a thorough security check on different aspects of your web application, such as servers and other such network devices, and list the security vulnerabilities that they present. Find and implement ways to remedy them.
5. Credential Encryption Testing

Ensure that all usernames and passwords are encrypted and transferred via a secure “HTTPS “connection so that hackers do not compromise these credentials through man-in – the-middle or other attacks of this kind. Because just as your web application needs to be secure, so your customers submit sensitive data.
6. Cookie Testing

Cookies store user sessions data. This piece of sensitive information, if exposed to hackers, can therefore jeopardize the safety of many users visiting your website or application. Therefore, don’t expose your cookie data. In other words, it’s not available in plain text or in readable format.
7. Contact Form Testing

The most preferred entry point for spammers is often the contact form for a web application. Therefore, your contact form should be able to identify and prevent such spam attacks. One of the easiest ways to prevent contact spamming is to include CAPTCHA.
8. Open Ports Testing

Open ports on the web server on which your web application is hosted also provide hackers with a good opportunity to take advantage of the security of your web application. Please check this security and make sure that there are no open ports on your webserver.
9. Application Login Page Testing

Make sure that your web application is locked after a number of unsuccessful login attempts. This is one of the basic elements that can go a long way in securing your web application from hackers when it is correctly implemented.
10. Error Message Testing

Ensures that all your error messages are generic and don’t reveal the problem too much. If you do so, it’s like announcing to the hacking community, “We have a problem here, you are welcome to use it!” For example: “Invalid credentials “is fine, but the message should not be specific as “invalid username or password.”
11. HTTP Method(s) Testing

Also check the HTTP methods your web application uses to interact with your clients. Make sure that PUT and Delete methods are not enabled, so hackers can easily use your web application.
12. Username and Password Testing

Testing username and password of all users in your web applications is the initial steps of your process. Passwords should be quite complex and usernames not easy to guess. Separate and alert these users to change such weak usernames and passwords.
13. Scanning File

Make sure that all files that you upload to your web application or server are scanned before uploading.
14. SQL Injection Testing

SQL Injection is one of the most popular methods used to use web applications and websites by hackers. Therefore, make sure that your web application is resistant to different SQL forms.
15. XSS Testing

Also ensure that your web application also withstands cross-site scripting or XSS attacks.
16. Access permission testing

Check your users ‘ access permissions and, if your web application provides role-based access, ensure that users only have access to those parts of the web application to which they are entitled. Nothing more or anything less.
17. Testing user session

This is very important. Ensure user sessions end after logging out. Because if they don’t, hackers can easily hijack this valid session–this process is called session hijacking –to perform malicious activity.
18. Brute Force Attack Testing

Ensure that your web application remains safe against brute force attacks using appropriate test tools.
19. DoS (Denial of Service) Attack Testing

Ensure that your web application keeps DoS (Denial of Service) attacks safe by using appropriate test tools.
20. Browsing Directory Testing

Ensure that the browsing directory is disabled on the web server that hosts your web application because if you don’t, hackers gain easy access to your limited files on server.
2. External Penetration Testing

These attacks are carried out externally from outside the organization and include Internet testing of web applications. Testers act like hackers who are not very familiar with the internal system.

To simulate these attacks, testers are provided with the IP of the target system and no further information is provided. You must search and scan public websites and find our information about target hosts and then compromise the hosts you have found.

It basically includes servers, firewalls and IDS testing.
How Penetration Testing is performed?

The pen test can be divided into five stages.

1. Planning and recognition

The first stage consists of:

    Defining the scope and objectives of a test, including the systems to be tackled and the test methods to be used etc.,
    To better understand how a target works and its potential vulnerabilities, gather intelligence (e.g. network and domain names, mail server).

2. Scanning

The next step is to understand how the target application responds to different attempts at intrusion. This is usually done using:

    Static analysis– inspecting the code of an application to estimate how it works, these instruments can scan the whole code in a single pass.
    Dynamic analysis– inspecting code in a running state for an application

This is a more practical way to scan, as it gives an in-house view of the performance of an application.

3. Access Control

This stage uses web application attacks to uncover the vulnerabilities of a target, such as cross-site scripting, SQL injection and backdoors. Testers then try to exploit these vulnerabilities in order to understand the damage they can cause by increasing privileges, stealing data, intercepting traffic, etc.

4. Maintaining access

The objective of this stage is to see whether the vulnerability can be used to achieve a persistent presence in the exploited system–long enough for a bad actor to gain access in depth. The idea is to imitate advanced, persistent threats that often remain in a system for months to steal the most sensitive data from an organization.

5. Analysis

The results of the penetration test are then compiled into a report detailing:

    Specific vulnerabilities exploited Sensitive data accessed
    The amount of time that the pen tester was able to remain undetected in the system.

This information is analyzed by security personnel to help configure the WAF settings of an enterprise and other patch vulnerability application security solutions.
Best Penetration Testing Companies of (2018-2019)

Service providers are companies that provide catering services to organizations ‘ testing needs. They usually excel and have expertise in various test areas and can test in their host test environment.
