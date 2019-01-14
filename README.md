# <img src="http://www.rice.edu/_images/rice-logo.jpg" width=180> Comp427, Spring 2018, Homework 1
## Rational Paranoia
The homework specifications, as well as the corresponding course slide decks,
can be found on the [Comp427 Piazza](https://piazza.com/class/jqifhp864b37ju).
This assignment is due **Thursday, January 17 at 6 p.m.**

You will do this homework by editing the _README.md_ file. It's in
[MarkDown format](https://guides.github.com/features/mastering-markdown/)
and will be rendered to beautiful HTML when you visit your GitHub repo.

## Student Information
Please also edit _README.md_ and replace your instructor's name and NetID with your own:

_Student name_: Philip Taffet

_Student NetID_: pat2

Your NetID is typically your initials and a numeric digit. That's
what we need here.

_If you contacted us in advance and we approved a late submission,
please cut-and-paste the text from that email here._

## Problem 1
- Scenario: Documents
- Assumptions:
  - I'm assuming we (the law firm) own the physical servers running the document management system.
  - The document management system is either provided by a large, decently reputable software company or is a well-known, reputable open source project.
  This doesn't mean that it won't have bugs, only that bugs will eventually be fixed.
  - Our documents are important enough that we may be targeted by fairly sophisticated adversaries.
  We may ocassionally be attacked with zero-day exploits (i.e. those that target previously unknown vulnerabilities).
  - Users connect to the document management system via some HTTPS-based protocol.
- Assets:
  - The confidential information contained inside certain documents: This is the primary asset to protect in this scenario, but we need to protect assets that help in protecting this information.
  - The physical hardware running the document management system
  - Credentials for users with access to the sensitive information
  - Network access to any network that the document management system is also connected to
  - Keys that allow physical access to the hardware running the document management system
- Threats:
  - The most likely attack, if not mitigated, is a network mounted attack from the outside.
  These are easy for an attacker since they can be difficult to trace.
  Unless the attacker is using a new exploit, the attack also requires very little investment from the attacker.
  If the attacker is using a new exploit, this is very difficult to defend against.
  The attacker may attack the document management system web application itself, any frameworks it uses, or the operating system of the server running the application.
  I personally have seen servers that I've put online attacked by bots trying to guess credentials using brute force.
  - Physical attack
  - DoS attack
  - Insider attack (leaker)
  - Compromise of computer/credentials of user with legit access
- Countermeasures:
  - One countermeasure against network mounted attacks is to ensure that the server is only accessible over the company's internal network and not over the internet.
  The downside to this countermeasure is that lawyers may need access to documents when at home or traveling. 
  This can be mitigated by allowing access to the internal corporate network via VPN.
  - Password complexity policy
  - Server locked, hard drives encrypted
  - Access to documents managed carefully on a per-user basis
  - Users with access to sensitive information required to use 2FA
  - Monitoring of network traffic
  - Access to documents logged

## Problem 2
- Scenario: {Stadium|TSA|Documents|Grading|G20}
- Assumptions:
  - explain_your_assumptions
- Assets:
  - explanatory_paragraph
  - explanatory_paragraph ...
- Threats:
  - explanatory_paragraph 
  - explanatory_paragraph ...
- Countermeasures:
  - explanatory_paragraph
  - explanatory_paragraph ...

## Problem 3
- Scenario: Your choice (give a brief explanation)
- Assumptions:
  - explain_your_assumptions
- Assets:
  - explanatory_paragraph
  - explanatory_paragraph ...
- Threats:
  - explanatory_paragraph 
  - explanatory_paragraph ...
- Countermeasures:
  - explanatory_paragraph
  - explanatory_paragraph ...

