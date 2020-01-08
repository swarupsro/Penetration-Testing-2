#  File Upload Exploitation
Still updating... : )

* ##  [  What is a file upload functionality?]()

* ##  [  How does it work?]()
 
   #### + [     ]()

* ##  [  What we can achieve by uploading the unrestricted files into the server?]()
* ##  [  Types of filters]()
* ##  [  Bypassing Developers validation]()
* ##  [  Filter evasion techniques]()
* ##  [  File upload functionality]()
* ##  [  File Upload Testing Labs]()

#### Types of filters?

I hope you have learned file upload working carefully then you should know what is the filter.

Here are some common filters used by the developers

    Blacklisting
    Whitelisting
    Content-type Validation
    Content length Validation

##### 1. Blacklisting Bypass:

Blacklisting can be bypassed by uploading unpopular PHP extensions.
such as: pht, phpt, phtml, php3,php4,php5,php6

##### 2. Whitelisting Bypass:

Whitelisting can be bypassed by uploading a file with some type of tricks, By adding a null byte character like ( shell.php%00.gif ). Or by using double extensions for the upload file like ( shell.jpg.php ).

Pro Tip: Always brute-force extension to check acceptance of extensions

##### 3. Content-type Validation:

This type of validation can be bypassed by changing the file name for example to “shell.php” or
“shell.aspx” but keeping the “Content-Type” parameter as “image/ *” Content-Type. Such as
“image/png”, “image/jpeg”, and “image/gif”.

Pro Tip: Same as above brute-force it (Fuzzing = win)

##### 4. Content length Validation:

It can be bypass using a small length of payload like

PHP shell: (<?=`$_GET[x]`?>)

Filter Bypassing Techniques -

1. upload PHP file using .pht extension when web app validates for the extension. (Apache-Linux)

2. upload asp file using .cer & .asa extension (IIS — Windows)

3. Upload .eml file when content-type = text/HTML

4. Inject null byte shell.php%001.jpg

5. Check for .svg file upload you can achieve stored XSS using XML payload

6. put file name ../../logo.png or ../../etc/passwd/logo.png to get directory traversal via upload file

7. Upload large size file for DoS attack test using the image.

8. (magic number) upload shell.php change content-type to image/gif and start content with GIF89a; will do the job!

9. If web app allows for zip upload then rename the file to pwd.jpg bcoz developer handle it via command

10. upload the file using SQL command ‘sleep(10).jpg you may achieve SQL if image directly saves to DB.
Advance Bypassing techniques —

##### 1. Imagetragick aka ImageMagick:
ImageTragick Exploitation — CVE-2016–3714 — Mukarram Khalid
One of the many talents of the Infosec community is the ability to come up with a cool name for a critical…
mukarramkhalid.com
#### 2. LFI using video upload:

https://github.com/FFmpeg/FFmpeg

https://hackerone.com/reports/226756

https://hackerone.com/reports/237381

https://docs.google.com/presentation/d/1yqWy_aE3dQNXAhW8kxMxRqtP7qMHaIfMzUDpEqFneos/edit

Exploit — https://github.com/neex/ffmpeg-avi-m3u-xbin

##### 3. Cross Content Hijacking:

https://github.com/nccgroup/CrossSiteContentHijacking
https://soroush.secproject.com/blog/2014/05/even-uploading-a-jpg-file-can-lead-to-cross-domain-data-hijacking-client-side-attack/
Exploit = http://50.56.33.56/blog/?p=242

##### 4. Encoding scripts in PNG IDAT chunk:

https://yqh.at/scripts_in_pngs.php
Remediation: File upload functionality

File upload functionality is not straightforward to implement securely. Some recommendations to consider in the design of this functionality include:

    Use a server-generated filename if storing uploaded files on disk.
    Inspect the content of uploaded files, and enforce a whitelist of accepted, non-executable content types. Additionally, enforce a blacklist of common executable formats, to hinder hybrid file attacks.
    Enforce a whitelist of accepted, non-executable file extensions.
    If uploaded files are downloaded by users, supply an accurate non-generic Content-Type header, the X-Content-Type-Options: nosniff header, and also a Content-Disposition header that specifies that browsers should handle the file as an attachment.
    Enforce a size limit on uploaded files (for defense-in-depth, this can be implemented both within application code and in the web server’s configuration).
    Reject attempts to upload archive formats such as ZIP.

Let’s practice in Lab —
1. DVWA
2. DUVA
3. Bwapp
4. rootme
