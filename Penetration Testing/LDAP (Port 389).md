
    ldap enumeration
        ldapminer
            ldapminer -h ip_address -p port (not required if default) -d
        luma
            Gui based tool
        ldp
            Gui based tool
        openldap
            ldapsearch [-n] [-u] [-v] [-k] [-K] [-t] [-A] [-L[L[L]]] [-M[M]] [-d debuglevel] [-f file] [-D binddn] [-W] [-w passwd] [-y passwdfile] [-H ldapuri] [-h ldaphost] [-p ldapport] [-P 2|3] [-b searchbase] [-s base|one|sub] [-a never|always|search|find] [-l timelimit] [-z sizelimit] [-O security-properties] [-I] [-U authcid] [-R realm] [-x] [-X authzid] [-Y mech] [-Z[Z]] filter [attrs...]
            ldapadd [-c][-S file][-n][-v][-k][-K][-M[M]][-d debuglevel][-D binddn][-W][-w passwd][-y passwdfile][-h ldaphost][-p ldap-port][-P 2|3][-O security-properties][-I][-Q][-U authcid][-R realm][-x][-X authzid][-Y mech][-Z[Z]][-f file]
            ldapdelete [-n][-v][-k][-K][-c][-M[M]][-d debuglevel][-f file][-D binddn][-W][-w passwd][-y passwdfile][-H ldapuri][-h ldaphost][-P 2|3][-p ldapport][-O security-properties][-U authcid][-R realm][-x][-I][-Q] [-X authzid][-Y mech][-Z[Z]][dn]
            ldapmodify [-a][-c][-S file][-n][-v][-k][-K][-M[M]][-d debuglevel][-D binddn][-W][-w passwd][-y passwdfile][-H ldapuri][-h ldaphost][-p ldapport][-P 2|3][-O security-properties][-I][-Q][-U authcid][-R realm][-x][-X authzid][-Y mech][-Z[Z]][-f file]
            ldapmodrdn [-r][-n][-v][-k][-K][-c][-M[M]][-d debuglevel][-D binddn][-W][-w passwd][-y passwdfile] [-H ldapuri][-h ldaphost][-p ldapport][-P 2|3][-O security-properties][-I][-Q][-U authcid][-R realm][-x] [-X authzid][-Y mech][-Z[Z]][-f file][dn rdn]
    ldap brute force
        bf_ldap
            bf_ldap -s server -d domain name -u|-U username | users list file name -L|-l passwords list | length of passwords to generate optional: -p port (default 389) -v (verbose mode) -P Ldap user path (default ,CN=Users,)
        K0ldS
        LDAP_Brute.pl
    Examine Configuration Files
        General
            containers.ldif
            ldap.cfg
            ldap.conf
            ldap.xml
            ldap-config.xml
            ldap-realm.xml
            slapd.conf
        IBM SecureWay V3 server
            V3.sas.oc
        Microsoft Active Directory server
            msadClassesAttrs.ldif
        Netscape Directory Server 4
            nsslapd.sas_at.conf
            nsslapd.sas_oc.conf
        OpenLDAP directory server
            slapd.sas_at.conf
            slapd.sas_oc.conf
        Sun ONE Directory Server 5.1
            75sas.ldif

