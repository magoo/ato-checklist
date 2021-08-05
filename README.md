# Account Takeover (ATO) Checklist
This is a list of considerations when designing a sophisticated program to deal with account takeover threats.

A [deciduous threat model](https://swagitda.com/deciduous/) is [here](model.yaml) for mitigation planning. 

![A threat model for ATO](model.svg)

---

🐑🐑🐺🐑

---


## Infrastructure 🛠
Backend systems we rely on for detection and mitigation.

- [ ] General Rate Limiting
- [ ] User Event / Authentication Logs
- [ ] Device Identification (Cookie)
	- See reference like [AuthTables](https://github.com/magoo/AuthTables)
- [ ] Browser Fingerprinting (No Cookie)
	-  See [AmIUnique](https://amiunique.org/), [Cover Your Tracks](https://coveryourtracks.eff.org/)
	-  🚨 Do not mix with ads infra 🚨
- [ ] Device Verification (Email confirmation, SMS, Snail Mail)
- [ ] Customer Session, Password Reset Workflows (Backend)
- [ ] Link Shim
- [ ] Leaked Credential Pipeline (Backend)
	- [ ] Scraping (Pastebin, torrents, etc)
	- [ ] D a R k W e B and UnDErGroUnD
	- [ ] Periodically accessible dumps

## ATO Indicators and Features 🕵️‍♀️
This section describes useful data that often needs to be acquired externally. These can be used in automated classification or to decorate investigation workflows with correlating info. 

- [ ] Known proxies, tor, vps & colocation
- [ ] Observed malicious or  compromised (Paid)
- [ ] Known Leaked Credentials
- [ ] Recent Sim Swap
- [ ] Domain intelligence
	-  [ ] New domains
	-  [ ] Disposable 
	-  [ ] Previously abused
-  [ ] Address verification
-  [ ] Cellular verification (VoIP detection)

## Product / UX 🎮
All user facing experiences to help reduce risk within a product.

- [ ] MFA Options
	- Security keys, MFA, SMS, backup codes, etc.
- [ ] Knowledge Base and self-support
	- Reducing outreach to support for questions.
- [ ] Link Shim
	- Allows for disabling of external links when copy-pasted, emailed, or otherwise brought off platform.
	- Allows for warning messages before leaving platform.
- [ ] Victim and Witness escalation (Report Abuse)
	- Where victims of ATO report their issue.
	- Where witnesses of abuse report off-platform impact of on-platform ATO.
- [ ] Forced Password Reset Workflows
	- [ ] Retroactively ask users to change leaked passwords
		- Existing customers will have weak passwords.
	- [ ] Handle newly found customers from a leaked credential backend
		- Newly leaked credentials will cause a regular need to change customer passwords.
	- [ ] "Reset the password to your email"
		- Some investigations will indicate a customer's email is compromised, not their password.
	- [ ] Account re-enable
		- Self service workflows to get back online after you have intervened.
- [ ] Enforce [password strength](https://github.com/dropbox/zxcvbn) to prevent future weak passwords 
	- [ ] New Registration
	- [ ] Password Change
	- [ ] Ongoing leaked / Newly weak
- [ ] Developer console prompts w/ a warning message
	- Example: [Facebook](https://security.stackexchange.com/questions/158106/facebooks-warning-of-self-xss)
- [ ] Verification / Challenge workflows
	- When you are uncertain of the customer's location or device.
		- [ ] SMS
		- [ ] Email
		- [ ] Account / Identity Knowledge
		- [ ] ID Submission	
		- [ ] CAPTCHA

## Customer Service ☎️
Operational customer service interactions (Support tickets). Support organizations often escalate abuse at scale to engineering and have the most visibility into what is, or is not, working.

- [ ] Standard Org Language
	- What counts as ATO?
- [ ] Metrics / KPI
	- Tracking abuse going up or down.
- [ ] IR Escalation
	- Playbooks / Plans for creating an outage or getting engineering resources involved.
- [ ] Reset Workflows (Administrative Frontends)
	- Empowering scalable operations to mitigate abuse scenarios.

## Investigations & Response 🚑
There will be periodic deep dives into ATO attacks to ask "what happened?". This section pertains to that perspective of work.

- [ ] Authentications are searchable by device, ip, user agent
	- [ ] Searches can pivot: Device to IP, IP to device, etc.
	- [ ] Bonus: Actions / Events are searchable
	- [ ] Bonus: All routes / Endpoints are searchable
- [ ] Tooling exists to reset bulk accounts that meet criteria
- [ ] Tooling exists to reverse transactions / changes that meet criteria.

## Automation 🤖
Tying everything together for operational ATO systems. Engineering time is the least scalable, customer support hours are more scalable, fully automated systems are the most scalable.

- [ ] Customer service classifies abuse cases 
- [ ] AI systems classifies authentication events
- [ ] Suspicious cases push customers to verify activity
- [ ] XFN meetings between groups to improve anti-abuse systematically

## Anti-Phishing 🎣
Raising the bar against trivial credential stealing attacks which cause the most problems for unprepared organizations.

- [ ] SPF / DMARC / DKIM 
- [ ] Brand protection (Internet scanning for your brand being spoofed)
- [ ] spoofed@ and customer phish reporting
- [ ] App store hunting
- [ ] Domain / ISP Takedowns
- [ ] Browser blacklisting
- [ ] Referer, hotlinks, adversary leaks