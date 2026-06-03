# phishing-email-analysis
Analyzed phishing websites and emails from for certain patterns and discrepancies. I documented certain techniques and practices with a structured report.




Phishing Email & URL Analysis
For my first cybersecurity project, I analyzed 5 real-world phishing samples from PhishTank and my own email inbox. The goal was simple — figure out how these attacks work, what makes them convincing, and what gives them away. Each sample is broken down by red flags, social engineering tactics, and what would actually happen if someone fell for it.

Table of Contents

Overview
Tools & Resources Used
Sample Analysis

Sample 1 — Allegro Marketplace Scam
Sample 2 — Microsoft Office 365 Credential Harvester
Sample 3 — Fake Spanish Moving Company
Sample 4 — UC Berkeley Spear Phishing Email
Sample 5 — Netflix Billing Scam


Patterns I Noticed
IOC Summary Table
Recommendations
What I Learned


Overview
FieldDetailsProject TypePhishing AnalysisSourcesPhishTank, Personal EmailSamples Analyzed5Targets CoveredE-commerce, Corporate, Education, EntertainmentDateJune 2026
Phishing is one of the most common ways attackers get into systems — and it works because it targets people, not just technology. I wanted to understand how these attacks are actually built, what psychological tricks they use, and how to spot them. I picked 5 samples covering different industries and attack styles to get a broad picture.

Tools & Resources Used
ToolWhat I Used It ForPhishTankFinding verified real-world phishing URLs to analyzeManual URL inspectionBreaking down domain structure and encoded parametersVisual comparisonComparing fake pages side by side with legitimate onesEmail header inspectionChecking sender addresses for spoofing

Sample Analysis

Sample 1 — Allegro Marketplace Scam
FieldDetailsSourcePhishTankImpersonatingAllegro (popular Polish e-commerce platform)GoalSteal credit card infoTargetGeneral public, elderly users, home shoppers
URL:
https://supra.smartistickids.info/?app_vl=ZYFwlHFpbWKEmLqxy5qmnnx0YsC2wa-TpaiVYsBxj2phmqOgnLFwrYw&e=kasia-g18%40wp.pl&sui={sui}&fn=Katarzyna&ln=Gacek&p=&z=PL-PLNAMERAW-2505-digi10
Red flags:

The URL is extremely long with a bunch of random encoded parameters — always suspicious
The base domain (smartistickids.info) has nothing to do with Allegro
The URL actually contains the victim's personal info baked right in — email address, first name, last name, and country code. This suggests the attacker already had some of this data from a previous breach or scraping operation
The fake site has a countdown timer that the real Allegro site doesn't have
The overall design looks noticeably off compared to the real Allegro website

How it tries to look real:

Uses the actual Allegro logo and brand colors
Features a real product sold on Allegro (a Philips Air Fryer)
Puts Instagram and Facebook icons at the bottom to look like an established business

Social engineering at work:
TacticHow they used itTrustCopied branding and a real product listingUrgencyCountdown timer — "buy now or miss out"DealsProduct offered at an attractive price
If someone fell for it:
Their credit card details get stolen and potentially used for fraud. Since the attacker already had some personal info going in, the victim may also face identity theft beyond just the financial hit.

Sample 2 — Microsoft Office 365 Credential Harvester
FieldDetailsSourcePhishTankImpersonatingMicrosoft / Office 365GoalSteal corporate login credentialsTargetBusiness employees
URL:
https://pub-eec4ae31337347448b4d9a7013a85762.r2.dev/eknt.html
Red flags:

The domain is .r2.dev — that's a Cloudflare R2 public storage bucket, not Microsoft
The long random string of characters in the subdomain is a giveaway of automated phishing infrastructure
Legitimate corporate login pages don't end in .html
The login page was rendering in Korean, which doesn't match an English-speaking corporate target

How it tries to look real:

This one is clever — the attacker hosted the page on Cloudflare's infrastructure, which automatically gives it a valid HTTPS certificate. The padlock shows up in the browser, which many users take as a sign the site is safe
The actual login page UI closely copies the real Microsoft 365 login design
After you enter credentials, it tells you they're wrong — prompting you to try again and submit twice

Social engineering at work:
TacticHow they used itTrustClean, professional UI that looks like the real thingAuthorityMicrosoft is one of the most recognized brands in enterprise softwareUrgency"Wrong credentials" bait gets users to submit a second time
If someone fell for it:
The attacker gets valid corporate credentials and can walk straight into the company's Microsoft environment — email, files, internal systems, everything. From there they can move laterally through the network, steal data, or launch follow-up attacks against colleagues from a trusted internal account.
Worth noting: This was the most technically sophisticated sample. Using legitimate cloud infrastructure to get a real SSL certificate is a smart move — it defeats the basic advice of "look for the padlock." The padlock just means the connection is encrypted, not that the site is trustworthy.

Sample 3 — Fake Spanish Moving Company
FieldDetailsSourcePhishTankImpersonatingA Spanish-speaking international moving companyGoalSteal credentials and payment infoTargetCustomers looking for moving services
URL:
https://internacionall.dreamhosters.com/
Red flags:

internacionall has a double l — classic typosquatting. Easy to miss at a glance
dreamhosters.com is a free staging domain from DreamHost. No real international logistics company would use a free subdomain
The site looks like a Google Slides template, not a professional business

How it tries to look real:

Claims to offer rare, premium services (international sea and air moving) to come across as a specialized, credible provider
Includes a phone number, address, and a privacy policy — things people associate with legitimate businesses but rarely verify

Social engineering at work:
TacticHow they used itTrustPositions itself as a specialized expert in a niche serviceCredibilityFake contact details and a privacy policy page
If someone fell for it:
The attacker gets payment details, home address, and potentially knows when the victim is moving — which has physical safety implications on top of the financial fraud.

Sample 4 — UC Berkeley Spear Phishing Email
FieldDetailsSourcePersonal observationImpersonatingUC Berkeley HR / AdministrationGoalSteal CalNet login credentialsTargetUC Berkeley students and staff
Red flags:

The sender address is not a @berkeley.edu email — the clearest single red flag
The link goes to a Google Form, not any official Berkeley system
UC Berkeley would never collect CalNet credentials through a Google Form

How it tries to look real:

The email is well-written and professionally structured — much higher quality than typical phishing
It closely mirrors the format of real Berkeley administrative emails
The scenario (annual assessment review and role eligibility) is completely plausible for the target audience

Social engineering at work:
TacticHow they used itAuthorityImpersonates the university's HR departmentUrgencyImplies the task affects role or rank eligibilityFamiliarityMatches the style of real Berkeley emails the target has already seen
If someone fell for it:
CalNet is single sign-on — one set of stolen credentials unlocks email, academic records, financial aid, and internal university systems all at once.
Worth noting: This was the most convincing sample of the five. It's a spear phishing attack — specifically crafted for a particular institution and audience rather than a generic mass campaign. The quality of the writing and the institutional specificity made it significantly harder to identify quickly. Technical controls matter less when the social engineering is this precise.

Sample 5 — Netflix Billing Scam
FieldDetailsSourcePersonal observationImpersonatingNetflixGoalSteal payment details and personal infoTargetNon-technical Netflix subscribers
Red flags:

Generic "Hi Dear" greeting — Netflix always uses your name in real emails
Rushed, informal writing that doesn't match Netflix's polished brand voice
Classic pattern: billing problem + immediate payment link = phishing
No personalization beyond the logo

How it tries to look real:

Uses Netflix's red and white branding and logo
References a billing issue that Netflix customers actually do encounter sometimes

Social engineering at work:
TacticHow they used itFearYour account is on hold — threatening loss of a paid serviceUrgencyUpdate payment details now or stay locked outTrustFamiliar Netflix branding lowers the guard
If someone fell for it:
Payment card info and personal details go straight to the attacker — financial fraud and potential identity theft.

Patterns I Noticed
After going through all five samples, some clear patterns stood out:
Every single one abused brand recognition. Whether it was Allegro, Microsoft, Netflix, or UC Berkeley — every attack leaned on a trusted name. Attackers know users extend trust to familiar logos without looking at the technical details underneath.
Social engineering did most of the heavy lifting. In most of these samples, the real weapon wasn't technical sophistication — it was psychology. Urgency and fear consistently showed up to short-circuit critical thinking.
HTTPS doesn't mean safe. Sample 2 was the clearest example of this. The attacker got a valid SSL certificate just by hosting on Cloudflare. The padlock showed up. The site was still malicious. This is probably the most important thing I learned from this project.
The URL is almost always the giveaway. Across every URL-based sample, the base domain had nothing to do with the organization being impersonated. Learning to read a URL carefully — especially the base domain before any path or parameters — would catch the majority of these attacks.
Targeted attacks are scarier than mass attacks. The UC Berkeley email was the most convincing sample despite being the least technically complex. Spear phishing works because it meets the target in a context they already know and trust.

IOC Summary Table
SampleIOC TypeWhat to Look ForAllegroURLUnrelated base domain, encoded victim PII in parametersAllegroVisualCountdown timer absent from real Allegro listingsMicrosoftDomain.r2.dev storage bucket hosting a login pageMicrosoftURLStatic .html page for a corporate loginMoving Co.DomainTyposquatting + free hosting subdomainMoving Co.VisualTemplate-grade website for an "international" companyUC BerkeleyEmailSender address not @berkeley.eduUC BerkeleyLinkGoogle Form URL instead of a university systemNetflixEmailGeneric greeting, informal language, immediate payment linkNetflixBehaviorBilling threat + urgent payment update request

Recommendations
For everyday users:

Check the base domain of any link before clicking — not the text, the actual URL
HTTPS and a padlock do not mean a site is trustworthy
Go directly to a website by typing it yourself rather than clicking links in emails
If an email creates urgency around money or login credentials, treat it as suspicious by default

For organizations:

Implement SPF, DKIM, and DMARC to reduce email spoofing
Use MFA so stolen credentials alone aren't enough to get in
Run phishing simulations so employees recognize these tactics before they see a real one
Set clear communication standards so employees know what official emails actually look like


What I Learned
A few things genuinely surprised me doing this project:
The Cloudflare infrastructure abuse in Sample 2 changed how I think about HTTPS. I went into this assuming a padlock meant something. It doesn't — at least not what most people think it means. Attackers can get valid SSL certificates just by hosting content on legitimate cloud platforms. That was probably the most practically useful thing I took away.
Typosquatting is sneaky. The internacionall domain in Sample 3 looks fine at a normal reading speed. You have to slow down and actually read the characters. That's a habit I'm building now.
The UC Berkeley spear phish reminded me that the most dangerous attacks aren't always the most technical ones. A well-written email targeting the right person in the right context can be more effective than sophisticated malware. Defenders need to think about psychology as much as technology.
Overall this project made abstract concepts like indicators of compromise and social engineering feel concrete and real. Looking forward to building on this in future projects.

All samples were analyzed safely using PhishTank's public database and personal email observation. No malicious URLs were visited or interacted with directly.
