Week 2 Day 5 — VM Hardening and OSINT Report

Date: 29 September 2026
Lab Environment: Ubuntu Virtual Machine
OSINT Target: example.com
Purpose: To document basic Ubuntu security hardening and demonstrate passive and limited DNS-based OSINT techniques.

1. Objectives

The objectives of this lab were to review the Ubuntu system's security configuration, apply basic hardening measures, verify security controls, and collect publicly available information about a designated example domain.

2. System Hardening
2.1 Firewall Configuration

The Uncomplicated Firewall (UFW) was enabled and checked.

Firewall status: Active.
Default incoming traffic: Denied.
Default outgoing traffic: Allowed.
SSH access: Restricted to the 192.168.56.0/24 network on port 22.

Observation: The firewall configuration limits unsolicited incoming connections and restricts SSH access to the specified lab network.

2.2 SSH Hardening

The effective SSH server configuration was checked using sshd -T.

Setting	Verified value
PermitRootLogin	no
PasswordAuthentication	no
PubkeyAuthentication	yes
MaxAuthTries	3

Observation: Root login and password-based SSH authentication are disabled, public-key authentication is enabled, and the number of authentication attempts is limited.

2.3 Fail2ban

Fail2ban was checked to verify that the SSH protection jail was present and active.

Fail2ban service: Active.
SSH jail: Present.
Failed attempts and bans: Zero at the time of checking.

Observation: Zero bans does not indicate a failure. It means no activity had triggered a ban during the recorded check.

2.4 User and Privilege Audit

The system's accounts and privileged users were reviewed.

The UID 0 check returned only the root account.
The sudo group contained the ubuntu user.
The SUID file search identified system executables such as sudo, passwd, and su.

Observation: The checks identified the expected root account and administrative membership. SUID executables should be reviewed periodically to ensure that their permissions are appropriate.

3. OSINT Methodology

The following tools and techniques were used against the reserved example domain example.com.

3.1 theHarvester

The command used was:

theHarvester -d example.com -l 20 -b duckduckgo -f theharvester-example

Findings: The search returned no email addresses, people, IP addresses, or hosts in the collected results.

Interpretation: No records were returned by this particular search. This does not prove that no public information exists.

3.2 Gobuster DNS Enumeration

A small wordlist containing www, mail, test, and dev was used for DNS enumeration.

Finding: www.example.com was discovered during the test.

Interpretation: The result demonstrates how a DNS enumeration tool tests candidate subdomain names. The limited wordlist does not provide a comprehensive subdomain inventory.

3.3 Manual Google Dorking

The following searches were performed:

site:example.com
site:example.com filetype:pdf
site:example.com intitle:"index of"

Findings:

The site search returned pages associated with example.com, including its www hostname.
The PDF-focused search returned no matching documents.
The directory-listing search returned no confirmed exact match.

Interpretation: Search-engine results provide only an indication of indexed public content. No matching result does not guarantee that a file or directory is absent.

4. Findings Summary
Area	Result
UFW	Active; incoming traffic denied by default
SSH	Root and password login disabled
Fail2ban	Active; SSH jail present
UID 0 audit	Only root returned
theHarvester	No records returned by the selected search
Gobuster DNS	www.example.com discovered
Google dorking	Domain pages found; no confirmed PDF or directory-listing match
5. Evidence and Limitations

Evidence was collected in the ~/w2d5-evidence directory, including firewall and SSH configuration checks, user and SUID audits, tool outputs, and OSINT search results.

Important baseline limitation: The files named before-* were captured after hardening had already begun. Therefore, the comparisons with after-* do not establish a true initial-to-final change. The blank differences indicate that the compared captures showed no differences; they do not prove that hardening changed the system from its original state.

The OSINT target example.com is a reserved example domain. The results are for lab demonstration only and must not be treated as an assessment of a real organization's security. TheHarvester and Google results can also vary over time.

6. Conclusion

This lab demonstrated basic Ubuntu hardening through firewall configuration, SSH security settings, Fail2ban verification, and user privilege auditing. It also demonstrated introductory OSINT techniques using theHarvester, Gobuster DNS enumeration, and Google search operators.

The checks confirmed the recorded security settings and produced a limited DNS discovery. Future work should capture a genuine pre-hardening baseline, repeat the checks after changes, and retain command outputs as evidence.

Lab status: Hardening checks and introductory OSINT exercises completed; baseline evidence limitations documented.
