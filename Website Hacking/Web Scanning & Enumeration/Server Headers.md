Check out header values in server responses. Headers like Server, X-Powered-by or X-Generator can leak information about the technologies used in the back-end. You can use Burp or wget to read server headers. Following command saves header values in index.html file.

wget --save-headers http://www.site.com/

https://www.owasp.org/index.php/Fingerprint_Web_Application_Framework_(OTG-INFO-008)
