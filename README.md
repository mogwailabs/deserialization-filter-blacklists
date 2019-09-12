# JEP 290 blacklist filter policies

This repository contains different black lists for classes that are used in publicly known Java deserialization gadget chains. It can be used with the pattern-based serialization filter from Java 9. This functionallity was also backported to older Java versions:
- Java 8 - 8u121 
- Java 7 - 7u131 
- Java 6 - 6u141

## Usage
The easiest way to use this list is to set the filter policy during application startup. This sets the global filter policy for all ObjectInputStream instances of the application, without changeing the actual code. 

Example: 

```bash
java -Djava.security.properties=blacklist-filter.properties -jar application.jar 
```

It is also possible to use the policy in a custom filter, please see the [official Java documentation](https://docs.oracle.com/javase/10/core/serialization-filtering1.htm#JSCOR-GUID-3ECB288D-E5BD-4412-892F-E9BB11D4C98A).

## Limitations
This policy does not provide any ressource limit filters which help to protect your application against potential Denial of Service (DoS) attacks. Use this policy on your own risk. 

## References
- [Official Java documentation - Serialization filtering](https://docs.oracle.com/javase/10/core/serialization-filtering1.htm#JSCOR-GUID-3ECB288D-E5BD-4412-892F-E9BB11D4C98A)
- [RedHat Blog Post - JDK approach to address deserialization Vulnerability](https://access.redhat.com/blogs/766093/posts/3135411)
