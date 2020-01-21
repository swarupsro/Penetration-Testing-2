## Port 2049 - NFS


    NFS Enumeration
        showmount -e hostname/ip_address
        mount -t nfs ip_address:/directory_found_exported /local_mount_point
    NFS Brute Force
        Interact with NFS share and try to add/delete
        Exploit and Confuse Unix
    Examine Configuration Files
        /etc/exports
        /etc/lib/nfs/xtab

Compaq/HP Insight Manager Port 2301,2381open

    HP Enumeration
        Authentication Method
            Host OS Authentication
            Default Authentication
                Default Passwords
        Wikto
        Nstealth
    HP Bruteforce
        Hydra
        Acunetix
    Examine Configuration Files
        path.properties
        mx.log
        CLIClientConfig.cfg
        database.props
        pg_hba.conf
        jboss-service.xml
        .namazurc


```
showmount -e INSERTIPADDRESS

If you find anything you can mount it like this:

mount INSERTIPADDRESS:/ /tmp/NFS
mount -t INSERTIPADDRESS:/ /tmp/NFS
```
