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
  - The servers that run the document management system could be subject to a physical attack, e.g. someone pulling the hard drive out of it. 
  This could also take the form of a denial of service attack, if the attacker destroyed or damaged the servers after gaining physical access to them.
  - An attacker could mount a denial of service attack by flooding the server with so many fraudulent requests that it cannot respond to legitimate requests.
  - The confidential information could be leaked by a disgruntled insider.
  An adversary might even be able to egg the leaker on or persuade them to leak the documents.
  - Another likely attack is compromising the computer or credentials of user with legitimate access to the confidential information.
  This is often done via phishing or other social engineering attacks.
  If the user has a weak password, his or her credentials could be compromised by guessing.
- Countermeasures:
  - One countermeasure against network mounted attacks is to ensure that the server is only accessible over the company's internal network and not over the internet.
  The downside to this countermeasure is that lawyers may need access to documents when at home or traveling. 
  This can be mitigated by allowing access to the internal corporate network via VPN.
  - To defend against physical attacks, the servers should be in a locked room, and the hard drives should be encrypted. 
  Access to the room should be limited to trusted admins.
  Since physical access to servers is pretty infrequent, the cost of this seems reasonable.
  This countermeasure could be taken one step further by requiring multiple admins to be present, but that extra cost seems excessive.
  - To avoid compromise of administrator credentials or user credentials, passwords should be required to meet a complexity policy.
  It needs to ensure passwords are essentially unguessable but not so complicated that they are impossible to remember.
  - A countermeasure to mitigate against insider leak attacks is to carefully control permission to access documents on a per-user basis and log all accesses to confidential documents.
  The policy for granting access to documents needs to be made as painless as possible (e.g. when a lawyer is assigned to a project, the person who sets the assignment automatically gives them access to the relevant documents).
  The cost of logging accesses is minimal and provides a good deterrence against leakers.
  - As a countermeasure to the compromise of user accounts, users with access to sensitive information should be required to use two factor authentication to log in to the document management system.
  The cost of deploying two factor authentication is substantial, but since phishing attacks are so common, I think it is justified.
  To reduce the cost, lawyers that don't require access to confidential information should not be required to use a second factor.
  - Any copies of the documents residing on the lawyers' personal computer should be encrypted at rest.
  Since this can be done transparently, the cost should be minimal.
  This protects against some types of compromise of users' computers.

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

