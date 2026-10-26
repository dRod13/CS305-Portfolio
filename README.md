# CS 305 Software Security Portfolio

**Dayron Rodriguez | Southern New Hampshire University**

This portfolio documents my software security work for Artemis Financial in CS 305. The selected artifact is my Project Two Practices for Secure Software Report, which covers checksum generation, certificate generation, HTTPS configuration, and security testing.

## Portfolio artifact

[View report as PDF](CS305_Project_Two_Report_Dayron_Rodriguez.pdf)

The report includes the implementation discussion and screenshots. It describes a classroom application and its remaining security limitations; it is not a production deployment.

## 1. Client and software requirements

Artemis Financial was the client in the course scenario. It is a financial consulting company that develops personalized plans for savings, retirement, investments, and insurance. The company wanted to modernize its web application and protect sensitive information during communication. My task was to refactor its existing application to demonstrate checksum generation and HTTPS, then document and test the changes.

## 2. What I did well and why secure coding matters

I used Java's MessageDigest API to implement SHA-256, selected UTF-8 encoding for consistent results, and checked the generated checksum against an independent calculation. I also kept the roles of hashing and encryption clear: a checksum supports integrity checking, while HTTPS protects the connection. Secure coding matters because mistakes can expose customer information or allow data to be altered. For a company such as Artemis Financial, software security helps protect customers, maintain trust, and reduce the cost of incidents and service interruptions.

## 3. Challenges and helpful parts of the assessment

Configuring the dependency scanner was challenging. I had to work through Maven settings, Java runtime compatibility, and NVD API key configuration before the scan completed. Reviewing its output was helpful because it showed how an application inherits risk from its libraries. I also learned that BUILD SUCCESS means the scanning task completed; it does not mean the application has no vulnerabilities.

## 4. Security layers and future assessment methods

I added a SHA-256 checksum endpoint, generated a self-signed RSA certificate, and configured HTTPS on port 8443. I supplied the keystore password through an environment variable rather than storing it in the properties file. In future projects, I would combine manual code review, dependency scanning, source-code analysis, and runtime testing. I would prioritize mitigations according to the affected component, exploit conditions, exposure, and potential impact, then retest the changes. I would suppress a finding only after establishing and documenting that it is a false positive.

## 5. Functional testing and checking for new vulnerabilities

I ran the refactored application, checked its successful HTTPS startup, and opened https://localhost:8443/hash to confirm that it displayed my name, unique data string, algorithm, and checksum. I reviewed the added controller and hexadecimal conversion method and ran OWASP Dependency-Check after refactoring. The application dependency declarations remained unchanged, and the hashing code added no third-party application library. However, I did not establish a comparable before-and-after scan using the same vulnerability database, so I cannot claim that the scan proved there were no new findings. Existing dependency findings and the browser's self-signed certificate trust warning remained unresolved.

## 6. Useful resources, tools, and coding practices

Eclipse, Maven, Java Keytool, Java MessageDigest, and OWASP Dependency-Check were useful throughout the work. The course vulnerability assessment flow diagram helped organize the review. Practices I will reuse include explicit input encoding, standard cryptographic APIs, keeping credentials out of source files, checking certificate names, reviewing dependencies, and recording test evidence. I will also distinguish functional success from security assurance when documenting results.

## 7. What I would show future employers

I would show this report as an example of working with an existing Java Spring Boot application, implementing a checksum endpoint, configuring local HTTPS, and interpreting dependency scan results. The screenshots and explanations demonstrate my ability to troubleshoot configuration issues and communicate security decisions. I would also discuss the remaining findings and the steps needed before production deployment, showing that I can recognize the limits of my testing and identify further work.
