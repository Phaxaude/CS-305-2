Briefly summarize your client, Artemis Financial, and its software requirements. Who was the client? What issue did the company want you to address?
The client was Artemis Financial, a consulting company focused on individualized 
financial planning (savings, retirement, investments, insurance). Artemis Financial 
was modernizing its operations and needed to enhance the security of its custom 
software, particularly its public web interface. Specifically, they required a file 
verification step (checksum) for data transfers and secure communication to protect 
client data and financial information. This involved adding these security features 
to their existing application.



What did you do well when you found your client’s software security vulnerabilities? Why is it important to code securely? What value does software security add to a company’s overall well-being?

I successfully identified the lack of data integrity checks and secure communication 
channels in the existing application. I effectively implemented the SHA-256 hashing 
algorithm for checksum verification and correctly configured the application to use 
HTTPS, demonstrating the ability to integrate standard security mechanisms into 
existing code.
It's crucial to code securely to protect sensitive data (like financial information) 
from unauthorized access, modification, or theft. Secure code prevents vulnerabilities 
that attackers could exploit.
Software security adds immense value by protecting the company's reputation, 
maintaining customer trust, ensuring regulatory compliance (especially important in 
finance), and preventing financial losses associated with data breaches or system 
downtime. It's a fundamental aspect of risk management.



Which part of the vulnerability assessment was challenging or helpful to you?

Configuring the HTTPS setup with the self-signed certificate was challenging initially, 
particularly ensuring the application.properties file had the correct path, password, 
alias, and keystore type to match the generated certificate. Debugging connection 
errors required careful checking of the server startup logs.



How did you increase layers of security? In the future, what would you use to assess vulnerabilities and decide which mitigation techniques to use?

Security was layered by first ensuring data integrity at rest or during transfer 
using SHA-256 checksums, and then protecting data in transit by encrypting the 
communication channel with HTTPS/TLS. These address two different potential points 
of failure.

In the future, I would use a combination of tools and techniques:
Static Analysis Security Testing (SAST) tools (like the dependency-check tool used 
here, or others like SonarQube or Checkmarx for analyzing source code itself) to 
find known vulnerabilities early.
Dynamic Analysis Security Testing (DAST) tools (like OWASP ZAP) to test the running 
application for vulnerabilities from an attacker's perspective.
Manual code review focusing on security best practices (input validation, proper 
error handling, secure configuration).
Threat modeling (like STRIDE) during the design phase to anticipate potential threats.
Decisions on mitigation would be based on the severity of the vulnerability 
(e.g., CVSS score), the likelihood of exploitation, and the potential impact on the 
business, prioritizing critical and high-severity issues.



How did you make certain the code and software application were functional and secure? After refactoring the code, how did you check to see whether you introduced new vulnerabilities?

I performed manual testing by running the application and accessing the /hash endpoint 
via a web browser (https://localhost:8443/hash). I verified that the page loaded, 
displayed the correct developer name and data string, calculated the SHA-256 hash, 
and showed the "Checksum verified" status. I also confirmed the browser was connecting 
via HTTPS (even with the self-signed certificate warning). The server console log showing 
a successful startup without errors also confirmed basic functionality.



What resources, tools, or coding practices did you use that might be helpful in future assignments or tasks?

*Eclipse IDE (for code development and running the application), Java Keytool (for 
certificate generation), OWASP Dependency-Check Maven plugin (for static vulnerability 
analysis of dependencies).  Official Java documentation for MessageDigest (for SHA-256), 
Spring Boot documentation for SSL/HTTPS configuration in application.properties, 
tutorials on using Java Keytool.



Employers sometimes ask for examples of work that you have successfully completed to show your skills, knowledge, and experience. What might you show future employers from this assignment?

The completed Practices for Secure Software Report itself, as it documents the entire 
process of analyzing requirements, implementing security features (hashing, HTTPS), 
testing, and justifying decisions based on best practices.
