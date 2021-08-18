# Application Security
All tasks that introduce a **secure** software development life cycle
Requirements analysis, design, implementation, verification, and maintenance

## Approaches
* Design Review - Threat Model
* Whitebox security review/code review - Noticing security flaws in source code
* Blackbox security audit - Using the application and testing for security vulnerabilities
* Automated Tooling - tools integrated into code editor or CI/CD platforms
* Coordinated vulnerability platforms - hacker-powered application security solutions - bug bounties etc


Open Web Application Security Project

Top 10 Most Critical Web App Sec risks:
1. Injection
2. Broken Authentication
3. Sensitive Data Exposure
4. XML External Entities
5. Broken Access Control
6. Security Misconfiguration
7. Cross-Site Scripting
8. Insecure Deserialsation
9. Using Components with Known Vulnerabilities
10. Insufficient Logging and Monitoring

Injection
When untrusted data is sent to an interpreter
The data can trick the interpreter into executing unintended commands or accessing data without proper authorisation

Broken Authentication
When authentication and session management are implemented incorrectly
Allows attackers to compromise secrets, assume other user's identities

Sensitive Data Exposure
When sensitive data is not properly protected
Attackers can steal or modify data to conduct crimes. (fraud, id theft, etc.)

XML External Entities
Older or poorly configured XML processors evaluate external entity references within XML documents. 
External entities can disclose internal files using the file URI handler, internal file shares, internal port scanning, remote code execution, and denial of service attacks.

Broken Access Control
Restrictions on what authenticated users are allowed to do are not properly enforced.
Attackers can exploit these flaws to access unauthorised functionality.

Security Misconfiguration
Insecure default configurations, incomplete or ad hoc configurations, open cloud storage, misconfigured HTTP headers, and verbose error messages containing sensitive information.
All OS, frameworks, libraries, and applications must be securely configured, as well well as be patched/upgraded in a timely fashion.

Cross-Site Scripting XSS
When an applications includes untrusted data in a new/updated webpage without proper validation or escaping.
Allows attackers to execute scripts in victim's browser, hijacking session, defacing websites, redirectiong to malicious sites.

Insecure Deserialsation
When insecure deserialisation leads to remote code execution.
Even if it doesn't result in remote code execution, they can be used to perform attacks, including replay attackes, injection attacks, and privilege escalation attacks.

Using Components with Known Vulnerabilities
Libraries, frameworks, and other software modules, run with the same privilege as the application.
If a vulnerable component is exploited, such an attack can facilitate data loss or server takeover.
Applications using components with known vulnerabilities may undermine application defenses and enable various attacks and impacts.

Insufficient Logging & Monitoring
Insufficient logging and monitoring, coupled with missing or ineffective integration with incident response, allows attackers to further attack systems, maintain ersistence, pivot to more systems, and tamper, extract, or destroy data.
Most breach studies show time to detect a breach is over 200 days, typically detected by external parties rather than internal processes or monitoring.




THREAT MODEL WORKSHOP

As many people from product team as possible, 3, 5, 10

Describe architecture in project

Act as Threat Actors

Encrypt data at rest in DB
