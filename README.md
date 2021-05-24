# Account Takeover (ATO) Checklist
This is a list of considerations when designing a sophisticated response to account takeover threats.

## Infrastructure
Backend systems we rely on for detection and mitigation.

- [ ] General Rate Limiting
- [ ] User Event / Authentication Logs
- [ ] Device Identification (Cookie)
- [ ] Browser Triangulation (No Cookie)
- [ ] Device Verification (Email confirmation, SMS, )
- [ ] Customer Session, Password Reset Workflows (Backend)
- [ ] Link Shim
- [ ] Leaked Credential Pipeline (Backend)
	- [ ] Scraping (Pastebin, torrents, etc)
	- [ ] D a R k W e B and UnDErGroUnD
	- [ ] Random, high profile dumps

## Threat Intel
This section describes useful data that often needs to be acquired externally. These can be used in automated classification or to decorate investigation workflows with correlating info. 

- [ ] Known proxies, tor, vps & colocation
- [ ] Observed malicious or  compromised (Paid)
- [ ] Known Leaked Credentials
- [ ] Recent Sim Swap
- [ ] Domain intelligence
	-  [ ] New domain
	-  [ ] Disposable 
	-  [ ] Previously abused
-  [ ] Address verification
-  [ ] Cellular verification

## Product Facing
All user facing experiences to help reduce risk.

- [ ] MFA Options
- [ ] Knowledge Base
- [ ] Link Shim
- [ ] Victim and Witness escalation (Report Abuse)
- [ ] Reset Workflows (Customer Frontend)
	- [ ] Retroactively ask users to change leaked passwords
	- [ ] Handle newly found customers from leaked credential backend
	- [ ] Prevent new registrations and password changes into leaked passwords
- [ ] Developer console prompts w/ a warning message
- [ ] Verification workflows:
	- [ ] SMS
	- [ ] Email
	- [ ] Account Knowledge
	- [ ] ID Submission	

## Customer Service
Operational systems involving customer service interactions

- [ ] Metrics / KPI
- [ ] IR Escalation
- [ ] Reset Workflows (Administrative Frontends)

## Investigations & Response
You'll have to manually dive into ATO attacks and ask "what is happening?". This section pertains to that perspective of work.

- [ ] Authentications are searchable by device, ip, user agent
	- [ ] Bonus: Actions / Events are searchable
	- [ ] Bonus: All routes / Endpoints are searchable
- [ ] Tooling exists to reset bulk accounts that meet criteria
- [ ] Tooling exists to reverse transactions / changes that meet criteria.

## Automation
Tying everything together for operational ATO systems.

- [ ] Customer service classifies abuse cases[ ] 
- [ ] AI systems classifies authentication events
- [ ] Suspicious cases push customers to re-verify
- [ ] XFN meetings to improve anti-abuse systematically

## Low Hanging Anti-Phishing
Raising the bar against trivial credential stealing attacks.

- [ ] SPF / DMARC / DKIM 
- [ ] Brand Protection (Internet Scanning)
- [ ] spoofed@ and phish reporting
- [ ] App Store Takedowns
- [ ] Domain / ISP Takedowns
- [ ] Browser Blacklisting