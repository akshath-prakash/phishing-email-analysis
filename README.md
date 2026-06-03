# phishing-email-analysis
For my first cybersecurity project, I analyzed 5 real-world phishing samples from PhishTank and my own research. Each sample is broken down by red flags, social engineering tactics, and what would actually happen if someone fell for it.

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

Phishing is one of the most common ways attackers get into systems — and it works because it targets people, not just technology. I wanted to understand how these attacks are actually built, what psychological tricks they use, and how to spot them. I picked 5 samples covering different industries and attack styles to get a broad picture.

Sample Analysis

Sample 1 — Allegro Marketplace Scam

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


If someone fell for it:
Their credit card details get stolen and potentially used for fraud. Since the attacker already had some personal info going in, the victim may also face identity theft beyond just the financial hit.
