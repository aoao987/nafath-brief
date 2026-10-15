Version: NAFATH-V4
Track: Software 

## Overview
Securing the software supply chain requires coordinated controls across the technologies used to build, deliver, and operate digital services. Software teams should separate configuration from application code and protect sensitive credentials. AI systems need testing against adversarial attacks that can manipulate inputs or training data. Mobile application security standards help teams define and verify protection requirements. At the network level, BGP route hijacking can disrupt or redirect traffic, while RPKI supports route-origin validation. Vulnerabilities such as Log4Shell demonstrate why organizations must identify affected dependencies and apply security updates promptly. A Software Bill of Materials (SBOM) improves visibility into software components and supports vulnerability response. These measures complement one another, but none guarantees complete security. Effective supply-chain protection depends on continuous verification, reliable inventories, timely remediation, and clear ownership throughout the software lifecycle.

## Software
The Twelve-Factor App methodology recommends storing deploy-specific configuration separately from application code. Configuration may include database connection details, service endpoints, and credentials. Separating configuration helps teams deploy the same code across development, testing, and production environments without embedding environment-specific values in the codebase. Sensitive secrets should be managed through appropriate secret-management systems, with access restricted to authorized services and people. Teams should also avoid committing credentials to public repositories and rotate exposed secrets promptly. This approach reduces accidental disclosure and makes configuration easier to audit and maintain.

Resource: The Twelve-Factor App — https://12factor.net/config

## AI
Machine-learning systems can be vulnerable to adversarial attacks. Evasion attacks modify inputs at inference time to cause incorrect predictions, while poisoning attacks manipulate training data to influence model behavior. These threats can affect the reliability of AI-enabled services and may create security or operational risks. Defenses depend on the system and threat model and can include validating training data, monitoring model behavior, testing against adversarial examples, and controlling access to training pipelines. Organizations should evaluate AI systems before deployment and continue testing them after changes to data, models, or operating conditions.

Resource: NIST — Adversarial Machine Learning: A Taxonomy and Terminology of Attacks and Mitigations — https://csrc.nist.gov/pubs/ai/100/2/e2023/final

## Mobile
The OWASP Mobile Application Security Verification Standard (MASVS) provides a structured basis for assessing mobile application security. It covers areas such as secure storage, cryptography, authentication, network communication, platform interaction, code quality, resilience, and privacy. Development teams can use the standard to define security requirements and guide testing throughout the application lifecycle. Verification should consider both the application itself and how it handles sensitive data and communicates with external services. Using a recognized standard makes security expectations clearer, although compliance alone cannot guarantee that an application is free from vulnerabilities.

Resource: OWASP Mobile Application Security Verification Standard (MASVS) — https://mas.owasp.org/MASVS/

## Networking
The Border Gateway Protocol (BGP) allows networks to exchange information about the routes used to reach IP address prefixes. A BGP hijack can occur when a network announces routing information that causes traffic to take an unintended path, potentially leading to interception or disruption. Resource Public Key Infrastructure (RPKI) supports route-origin validation by allowing resource holders to authorize which autonomous systems may originate particular prefixes. Network operators can use Route Origin Authorizations (ROAs) and validation results to help identify invalid route announcements. RPKI reduces certain routing risks, but it does not prevent every type of BGP attack, so operators still need monitoring and sound routing policies.

Resource: RIPE NCC — Resource Public Key Infrastructure (RPKI) — https://www.ripe.net/manage-ips-and-asns/resource-management/certification/

## Cybersecurity
Log4Shell is a critical vulnerability identified as CVE-2021-44228 in Apache Log4j 2, a widely used Java logging library. Under vulnerable configurations, an attacker could trigger a JNDI lookup through crafted input, potentially enabling remote code execution. The vulnerability was especially concerning because logging libraries are often included indirectly through application dependencies. Organizations should identify affected Log4j versions across their environments, upgrade to a vendor-supported fixed version, and follow relevant vendor and security-agency guidance. Temporary mitigations may reduce exposure, but they should not replace appropriate patching and verification. Asset inventories and dependency monitoring help teams respond more quickly to similar vulnerabilities.

Resource: CISA — Apache Log4j Vulnerability Guidance — https://www.cisa.gov/news-events/cybersecurity-advisories/aa21-356a

## Data
A Software Bill of Materials (SBOM) is a structured inventory of software components and their relationships within a product. It can identify direct and transitive dependencies, helping organizations understand which third-party packages are included in their applications. When a new vulnerability is disclosed, teams can use an SBOM to check whether affected components may be present and prioritize investigation and remediation. SBOMs are most useful when they are accurate, maintained, and linked to the software version being deployed. However, an SBOM does not prove that software is secure or automatically eliminate vulnerabilities; it provides visibility that supports vulnerability management and supply-chain risk assessment.

Resource: CISA — Software Bill of Materials (SBOM) — https://www.cisa.gov/sbom

## Misconception in My Track
A common misconception in software development is that an application is secure once its own source code has been reviewed and tested. In reality, applications often depend on third-party libraries, build tools, packages, and external services that may introduce vulnerabilities or compromise risks. Even well-written application code can be affected by a vulnerable dependency or a tampered build process. Software teams should therefore review dependencies, keep components updated, verify package sources, and protect build pipelines. Security must be considered throughout the software lifecycle, not treated as a final check before release.

## Open Question
How can small software teams maintain reliable visibility into third-party dependencies and verify the integrity of their software build process when they have limited time, budget, and security expertise?
