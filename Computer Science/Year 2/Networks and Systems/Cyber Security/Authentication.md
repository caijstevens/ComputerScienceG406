 #nas 

# Identification 

Subjects/objects have identities, needed to perform system actions.
- **abstraction layer**: actions done on claimed identities of entities

### Identity Management 

**Identification**: when they "know" your identity
**Authentication**: verifying credentials 
**Authorisation**: a decision about which resources/actions can be used by certain user
**Auditing**: who/what was authenticated and performed which actions 

# Authentication 

Process that leads to **verify** that identity provided is correct.

Confusion matrix used to evaluate accuracy:![[Screenshot 2025-10-27 at 11.18.23.png]]
- perfect authentication would only find true positive and true negative.
- perfect does not exist, trade-off between usability and security 

Credentials in following categories:
- something known (password, signal)
- something owned (token, smartcard)
- something you are (fingerprint, DNA)

### Password 

Should always be stored in hash in case of leaks
- random "salt" added to disrupt brute-force 

Honeywords store multiple hashes, only one of which for actual password
- brute force attack would likely find honeyword before actual password
- honeyword usage detectable, can block system or change passwords 
- requires external checker service 

# One Time Password 

Password generated from hash from secret key and current time 
- generated every user-defined time gap
- server generates all possible hashes for corresponding time to check if number matches 

# Biometrics 

Usually unique to individual, identification step implicit
- readable features extracted from physiological or behavioural biometrics
- enrolment process stores features in database
- recognition process compares extracted features with stored ones 

### Tolerance Threshold 

Matching features is quantitative process, has **level of confidence**
- trade off between false acceptance rate and false rejection rate 
- equal error rate: FRR=FAR (usually used as comparison criterion)

### Properties 

Ideal biometric feature should have following properties:
- universality (everyone owns it)
- uniqueness (different per person)
- stability (does not change over time)
- collectability (easy to acquire)
- performance (fast to process with low error rates)
- acceptability (individual accepts collection)
- resistance to forgery (hard to fake)

# Facial Recognition 

Images collected in either visible spectrum or infrared
- non-invasive, hands-free, quite accepted 
- not recommended for high security

Extraction approaches:
- **Principal Component Analysis**: models face as weighted combination of basis faces
- **Local Feature Analysis**: Locates facial features and assesses geometry and relative position 
- **Skin Texture Analysis**
- all can be affected by expression, hair, makeup, glasses etc

Property assessment:
- universality: high
- uniqueness: low
- stability: medium
- collectability: high 
- performance: low 
- acceptability: high 
- resistance to forgery: low 

# Authentication Issues 

Security:
- phishing
- brute force 
- malicious recovery (re-enrolment with new credentials)
- leakage

Usability:
- information re-use 
- authentication fatigue
- privacy concerns 
- risk independence 

# Multi-Factor Authentication 

Spreads risk of spoofing over multiple mechanisms
- assumes that likelihood of spoofing one mechanism is independent to spoofing others 
- improves security but limits usability 

# Continuous Authentication 

Reduces authentication fatigue by avoiding repeat asks
- user has authentication level that decays with time
- biometrics and passive mechanisms useful for implementation 
- continuous monitoring very costly
- privacy issue: continuous authentication may require users to be trackable at all times 

# Federated Identity Management 

Distributed systems require identity in multiple places
- can use single sign-on, authenticates only once and produces token for re-use 

# OAuth 

OpenI is authentication protocol: token received by user just indicates certified identity
- sub-services can decide what their authorisation policies are based on ID token
- can be useful to forward an authorisation token: OAuth![[Screenshot 2025-10-27 at 11.37.46.png]]
