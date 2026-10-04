# Checkpoint 2 – Infrastructure Assessment

## Project
GovTech Project – Security Operations Centre (SOC) Setup Simulation

## Assessment
Infrastructure Security Assessment

## Target
`192.168.56.101`

## Environment
Authorized Metasploitable2 laboratory environment.

## Objective

Assess the infrastructure layer of the authorized lab target, including:

- Network services and exposed ports
- Service and software versions
- Authentication mechanisms
- Anonymous access
- Patch and version weaknesses
- Infrastructure-level vulnerabilities
- Security misconfigurations

## Activities Performed

- Network service and port enumeration using Nmap
- Operating system detection
- Service and version identification
- FTP anonymous-access assessment
- SSH authentication-method assessment
- Telnet service assessment
- SMB share and anonymous-access assessment
- MySQL authentication assessment
- PostgreSQL service assessment
- VNC security assessment
- HTTP method and header assessment
- DNS service assessment
- SMTP command enumeration
- Apache and SSL/TLS vulnerability assessment
- Nmap vulnerability scanning

## Key Findings

The assessment identified several infrastructure-level security weaknesses, including:

1. Anonymous FTP access on port 21
2. Anonymous SMB read/write access on ports 139/445
3. MySQL root account with an empty password on port 3306
4. Java RMI remote class-loading exposure on port 1099
5. SSL/TLS CCS Injection
6. SSLv3 POODLE exposure
7. Weak Diffie-Hellman parameters
8. Multiple outdated and unnecessary network services

## Evidence

The folder contains the assessment report and supporting Nmap evidence files.

### Main Report

`Checkpoint2_Infrastructure_Assessment.pdf`

### Evidence Files

- `checkpoint2_nmap_services.txt`
- `checkpoint2_os_detection.txt`
- `checkpoint2_ftp_anonymous.txt`
- `checkpoint2_smb_shares.txt`
- `checkpoint2_mysql_empty_password.txt`
- `checkpoint2_ssh_auth.txt`
- `checkpoint2_telnet.txt`
- `checkpoint2_postgresql.txt`
- `checkpoint2_vnc.txt`
- `checkpoint2_http80.txt`
- `checkpoint2_http_headers.txt`
- `checkpoint2_http_headers_curl.txt`
- `checkpoint2_http_methods.txt`
- `checkpoint2_dns.txt`
- `checkpoint2_smtp.txt`
- `checkpoint2_apache_vuln.txt`
- `checkpoint2_vuln_scan.txt`
- `finding_01_anonymous_ftp.txt`

## Severity

Confirmed and assessed findings are documented in the main PDF report with severity and CVSS information where applicable.

## Recommendations

Key recommendations include:

- Disable unnecessary services
- Disable anonymous FTP access
- Remove anonymous SMB read/write permissions
- Configure strong database authentication
- Restrict database access to trusted hosts
- Disable unsafe Java RMI remote class loading
- Disable SSLv3
- Upgrade vulnerable and outdated software
- Replace weak cryptographic parameters
- Use firewall rules and network segmentation

## Conclusion

The infrastructure assessment identified multiple exposed services, authentication weaknesses, outdated software, and infrastructure-level vulnerabilities on the authorized lab target.

The detailed findings, evidence, severity information, and recommendations are provided in the accompanying assessment report.
