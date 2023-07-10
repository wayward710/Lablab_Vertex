Common Vulnerabilities and Exposures (CVEs) are a standardized way of cataloging vulnerabilities in software. When a security vulnerability is discovered, it can be assigned a CVE identifier to ensure that information about the vulnerability can be shared and referenced across different platforms and organizations. CVEs are currently maintained as freeform text descriptions of vulnerabilities, but will soon be maintained in JSON format.

A Software Bill of Materials (SBOM) is a document that provides a comprehensive inventory of software components and dependencies. It is a structured list that includes information about the software components, libraries, frameworks, and other third-party software used in the development or deployment of a software product. SBOMs can be automatically generated from files that define build information for software, e.g. POM files for Maven, requirements.txt for Python, etc.

It would be extremely useful to be able to automatically scan SBOMs to see whether the associated software packages are vulnerable to the CVEs. Google Vertex's Palm turned out to be capable of automatically finding a list of affected versions based on the CVE descriptions. For example, there was a major vulnerability in Apache Log4J in late 2021. Let's take a look at the version information in the CVE (https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2021-44832): 

"Apache Log4j2 versions 2.0-beta7 through 2.17.0 (excluding security fix releases 2.3.2 and 2.12.4) are vulnerable to a remote code execution (RCE) attack...." That makes sense to a human, but it's not conducive to automatic processing. 

Google Vertex was able to generate a specific list of Log4J versions that met the criteria in the description. It also shows potential for automatically extracting additional information from text descriptions in CVEs. With this information, we can automatically read an SBOM and determine whether the software is vulnerable to a particular CVE.
