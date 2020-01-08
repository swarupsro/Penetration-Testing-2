#  File Upload Exploitation
Still updating... : )

* ##  [  What is a file upload functionality?]()

* ##  [  How does it work?]()
 
   #### + [     ]()

* ##  [  What we can achieve by uploading the unrestricted files into the server?]()
* ##  [  Types of filters]()
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
