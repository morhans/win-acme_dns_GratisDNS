# Gratisdns has been bought by one.com and this script is no longer functional

# win-acme dns api for danish DNS provider gratisdns.dk
win-acme_dns_GratisDNS

**Author:** Morten Hansen

**Repository:** https://github.com/morhans/win-acme_dns_GratisDNS

### Disclaimer

This is my first powershell script. So, any ideas and better ways of doing things is welcome.

### What is this?

This is a dns api for use with [wacs](https://win-acme.com) that uses Let's Encrypt for issuing certificates.
It enables you to automatically update gratisdns.dk dns-records for
your domains hosted on their dns servers.


### Instructions

For this to work, download and install [wacs](https://win-acme.com) and copy the
**GratisDNS.ps1** file into the sub directory **Scripts**. 

Before using it with [wacs](https://win-acme.com) you have to register username and password.

This is done with running the script with the user [wacs](https://win-acme.com) is to run with.
If not, it will not be possible for [wacs](https://win-acme.com) to read out the credentials, due to credentials is encrypted to that user.

Run script with option setcred 

`GratisDNS.ps1 setcred`

Fill in your correct gratisdns username and password as asked by the script.

**GratisDNS.ps1** takes the default parameters asked by [wacs](https://www.win-acme.com/reference/plugins/validation/dns/script). That is:

`create {Identifier} {RecordName} {Token}` 

and

`delete {Identifier} {RecordName} {Token}`

Specific to GratisDNS they sometimes ask for Acceptence of Terms on login.
By default, this is accepted by the script. If this is undesired add the parameter **DeclineTerms** to the end.
Example:

`create {Identifier} {RecordName} {Token} DeclineTerms`

In case GratisDNS askes for Acceptence of Terms and **DeclineTerms** is issued an error will be trown stating terms was not accepted.

[wacs](https://www.win-acme.com/reference/settings) default wait timer for DNS replication may not be sufficient consider increasing these.
Example in settings.json file: 

    "PreValidateDnsRetryCount": 5,
    "PreValidateDnsRetryInterval": 150,

#### Information on using WACS

Please see win-acme website found at https://www.win-acme.com
 
