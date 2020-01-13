### Login Details
Legit users are authenticated using username and passwords. These are lock and keys for the website. People tend to use simple and easy to remember passwords but there lies the vulnerability, common passwords. I’ve seen many people using passwords as simple as admin : admin. Is this how you care for the web security? This type of attack is called Brute force attack, where the attacker uses different username/password combinations to attempt to log into the admin panel. This attack is performed using brute force tools like Brutus, hydra and burp suite.  
## Hydra   

Hydra is the tool mostly used for brute forcing Gmail accounts. Due to versatility of this tool, it is everybody’s favourite. It can perform brute force on network protocols/services like ssh and also web based forms (POST). Before starting a brute force attack, one should know its merits and demerits. It’s like a guessing game where you predict a username and password combination and try it on the login page hoping that it will work. Now doing this manually will be a heck of a job; therefore, we use tools like hydra to automate our work. Hydra is now a magic wand that will work only if you have imputed write parameters. To successfully execute a brute force attack, one need to understand what words or symbols a user might have used in his/her username and password. If guessed correctly, it might take minutes to crack the login page.
Types of Brute force attack:

1) Simple/Traditional Brute Force
Traditional Brute force attack requires all the alphabets, symbols, numbers, special chars, that a user might have used in his username or password.

E.g.
 testing123@ is the password of the user so the attacker might input all the alphabets, numbers and symbols to hydra which means using all this data tool will create n number of combinations and try it on web forms. So, knowing about the password accurately will reduce the number of combinations to try and the time to crack the password.

2) Dictionary Attack
On the other hand, dictionary attack might do your work pretty easily and fast as it contains only commonly used passwords and dictionary words. This reduces the crack time. Use this method  as the last option after you have tried everything else.

Official website:

https://www.thc.org/thc-hydra/

Things you need

•	
o	IP address of the website
•	
o	Protocol information (http/https)
•	
o	Type of parameter (GET/POST)
•	
o	Username or password list
•	
o	Brain

Assuming targetsite.com/wp-login.php is the target page.

Usage:
Start your terminal and enter the following command:

hydra 192.168.10.10 http-form-post "/wp-login.php:log=^USER^&pwd=^PASS^:Bad login" -L users.txt -P pass.txt -t 10 -w 30 -o hydra-http-post-attack.txt 

Now the tool will try each and every username/password combination on the webform until it finds a valid one.  
## WPscan
## Burpsuit
