---
type: study
topic: school
---

#school #IT4823

# 1. Types of Encryption
`Module 2, slides: cryptography`
# 2. Authentication
`Module 1, slides: authenticatoin`
## User Authentication
* Fundamental security building block
	Basis of access control and user accountability
* has two steps
	Identification - specify identifier
	Verification - bind entity (person) and identifier
* Distinct from message authentication
* has four means
	knows (e.g. password, pin)
	posseses (e.g. key, card)
	is (static biometrics) - e.g. retina, fingerprint
	does (dynamic biometrics) - e.g. voice, sign

## password auth
* issues
	how is password stored?
	how does system check password?
	how easy is it to guess password?
* basic password scheme
	hash function
	password stored as hashed password
 * salt
	 random digits/chars added to make guessing harder

## token auth
# 3. Authorization
`authorization is the third step in access control (identification, authentication, authorization, grant access`
* 
# 4. Traffic Analysis
# 5.  Vulnerability and Exploit
# 6. Goals and Policies of Information Security
• Prevention  
• Prevent violations of security policy

• Detection  
• Detect violations of security policy

• Response and Recovery

- Stop the violation, assess and repair damage
    
- Continue to function correctly even if security policy is violated
    
- Return system to a state consistent with policy
# 7. Absolute vs Computational Secure
• Absolutely secure: There is no way to recover the plaintext from the cipher text without the key. (And the algorithm)

• Computationally secure: The time to recover the plaintext from the cipher text is so great that the message has little or no value by the time it can be decrypted.

How long does “We attack at dawn!” need to remain secure?
# 8. Man-in-the-Middle
Man in the middle attack is when someone inserts themselves into the middle of communication/data-transfer in order to eavesdrop, steal data, or impersonate.
# 9. Cryptographic hashes
• Cryptographic hashes: Generate a fixed length “fingerprint” that identifies a variable- length message.
- The MD5 hash code is 128 bits; SHA is 160.
    
- So, there are 2128 or 2160 possible hashes (a lot!)
    
- The probability that two messages have the same hash code is very small.
    
- Can a message be especially crafted to have the same hash code as an arbitrary message?  
    (Not easily.)
    
- That is the strength of cryptographic hash algorithms.
# 10. Social Engineering
# 11. Least Privilege / Default Deny
• The system planning process should identify what is actually required for a given system (least privilege.)
- Principle of least privilege (default deny): block all portsthatarenotspecificallyneeded. (HowdoIknow that BO isn’t using a “needed” port?)
# 12. Key Exchange
https://en.wikipedia.org/wiki/Key_exchange
# 13. Key Strength
# 14. Digital signature
one way is with public vs private keys. encrypting the data with a private key means that the person who owns that private key must've encrypted it.
the e sign law (2000) gives digital signatures the same legal weight as "wet ink" signatures (the law doesn't specify a specific technology).
# 15. Access controls / ACL
` Module 1, slide: Access Control`
* Access control has four steps
	Identification
	Authentication
	Authorization
	Grant access
# 16. Management of keys (Symmetric/Asymmetric)
Symmetric vs asymmetric is a comparison that's often used in the world of cryptography and computer security. **Symmetric encryption involves using a single key to encrypt and decrypt data, while asymmetric encryption uses two keys - one public and one private - to encrypt and decrypt data**.
# 17. Digital certificates
Certificates are used to bind an identity to a public key.
• Create token (message) containing • Identity of principal (here, George) • Corresponding public key  
• Type of hash used
• Other information (e.g. identity of signer)
Digitally signed by trusted authority  
Cs = George || kGB || T || Signer || {Digest} kCV
# 18. Public vs private keys
• Is there a way to use cryptography to verify originintegrity? (Hint:Yes.)

• The public and private keys of a key pair are cryptographic inverses of each other.

• A message encrypted with the public key can only be decrypted with the corresponding private key.

• But, a message encrypted with the private key can be decrypted using the corresponding public key!
Public key cryptography works both ways; the keys are cryptographic inverses of one another!

Bob encrypts a message with his private key Anyone can decrypt it using Bob’s public key.

Only Bob could have encrypted it, so, it is “signed” by Bob.

overall , public keys are used to encrypt, while private keys are used to decrypt (it seems).
# 19. Software Security Vulnerabilities
# 20. Attackers Triad
• Disclosure: compromises confidentiality • Outside attackers  
• Insiders  
• Programming or other errors

• Alteration: compromises integrity • Accidental or malicious alteration • Programming or equipment failure

• Denial: compromises availability  
• Deliberate attacks  
• Failures of systems or environment
# 21. DMZ
• DMZ: “demilitarized zone”  
• Portion of network separating purely internal

network from external network

• Allows control of accesses to some trusted systems inside the corporate perimeter

• If DMZ systems breached, internal systems are still safe

• Can perform different types of checks at boundary of internal, DMZ networks and DMZ,Internet network
# 22. Firewalls
# 23. Buffer Overflow
• Often there are assumptions about buffer size • e.g. that user input is only a line of text  
• size buffer accordingly but fail to verify size • resulting in buffer overflow

• Testing may not identify vulnerability  
• since focus on “normal, expected” inputs

• Safe coding treats all input as dangerous  
• hence must process so as to protect program

buffer overflow attack
application error occurs when more data is sent to a buffer than it can handle
when the buffer overflows, the attacker can make the target system execute instructions, or the attacker can take advantage of some other unintended consequence of the failure.
usually the attacker fill the overflow buffer with the executable program code to elevate the attacker's permission to that of an administrator.