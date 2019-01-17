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
  We may occasionally be attacked with zero-day exploits (i.e. those that target previously unknown vulnerabilities).
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
  It needs to ensure passwords are essentially un-guessable but not so complicated that they are impossible to remember.
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
- Scenario: Grading
- Assumptions:
  - Students submit code electronically
  - The grade is based entirely on how whether its output matches that of a reference solution on a series of test cases
  - The source is compiled by the grading program using a student-supplied Makefile
  - The students are particularly malicious and won't necessarily follow instructions about where to write on the file system, etc.
  - I'm not considering the challenge of identifying plagiarism in submitted code.
- Assets:
  - The gradebook
  - The test cases and their solutions
  - Student's submissions
  - The grading infrastructure
  - My credentials for accessing the grading infrastructure
- Threats:
  - The following threats come from the fact that I'm essentially running code provided by a potentially malicious actor, which is a dangerous strategy:
	  - The student's submission reads and somehow publishes the test cases, compromising the project for next year
	  - The student's submission reads the files containing the correct solution and outputs their contents instead of computing the solution
	  - The student's submission overwrites files on the grading computer
	  - The student's submission never terminates and consumes lots of CPU or memory (e.g. they just submit a Bitcoin miner).
  - A student could try to steal another student's solution
- Countermeasures:
  - Grading should be done on a different machine than the one that stores the gradebook.
  This probably means I need a dedicated grading machine, but I wouldn't want to do all this on my personal machine anyways, which is where I store the gradebook.
  - Compiling and running the student's code should be done in a very unprivileged user account (the running account).
  Since it typically should be very obvious to the professor what types of permissions (disk, network, etc.),
  these restrictions pose a very small cost to valid submissions.
	  - The running account should not have network access or should have network access restricted to allowed IP addresses.
	  - The running account should not have access to the solution files.
	  - The running account should only have write access to a very small subset of the file system.
  - The grading process should monitor the compilation and execution processes and terminate them after a reasonable time-out limit expires.
  As long as the time-out is reasonable, I think students will understand the justification for this policy.
  - The grading machine should only allow access via the my SSH keys, which are protected with a password.
  This makes it very difficult for a student to log into the grading infrastructure.
  The downside is that I can only log in from computers I set up in advance, meaning I'm locked out if they all break,
  but as long as I have at least two computers, I'm willing to accept this. 
  - Students' submissions should be timed, and any submission that runs substantially faster than should be possible should be flagged to manual review.

## Problem 3
- Scenario: My car doesn't have a remote to unlock the doors, so I'm building a device that can press the unlock button on the passenger side door when it receives a command from my phone over Bluetooth.
I'm currently using a challenge-response protocol like this:
1. When the phone detects that it is in range of the microcontroller, it initiates a Bluetooth connection to the microcontroller.
1. The microcontroller responds with a random nonce.
1. The phone computes HMAC(_k_, nonce || command) and sends it back along with the command.
1. The microcontroller also computes HMAC(_k_, nonce || command). If it matches what the phone supplied, it executes the command.
- Assumptions:
  - My phone and the microcontroller in the car are not compromised.
  - If it's substantially easier for an attacker to break into my car by smashing the window, they won't bother with attacking the remote unlocker.
  - The attacker cannot hotwire my car, so the value of what they get by breaking in is just the value of what I keep in my car, which is less than $2000. 
  - The attacker won't attempt to break into my car while I'm at my car.
  - It's important for the protocol to be low-power for the microcontroller, since it is battery-powered.
  - The key _k_ is shared between the phone and microcontroller but is otherwise secret. 
  - The random number generator for the nonce is good.
- Assets:
  - Whatever I'm storing in my car, which may include my laptop or luggage
  - Other things they can take from the car itself, e.g. the sound system
  - My phone, which contains the code and encryption keys
  - The secret key _k_
  - The microcontroller itself
- Threats:
  - An attacker with a Bluetooth sniffer could record connection attempts and replay them.
  - An attacker could perform a man-in-the-middle attack, having one device pretend to be the microcontroller to my phone and another device pretend to be my phone to the microcontroller.
  - An attacker could break my car's window and press the unlock button
  - An attacker could steal my phone and use it to unlock the car
- Countermeasures:
  - Realistically, I can't justify many countermeasures, since I expect most attackers would just go for the window.
  I'm not willing to pay a large price in power consumption for a more sophisticated protocol.
  - The protocol itself defends against replay attacks by using the nonce.
  If the phone just sent the key in plaintext and an attacker sniffed it, they could lock and unlock my car as much as they wanted without leaving a trace.
  - The easiest way to defend against practical man-in-the-middle attacks is to require user input on my phone to unlock the car.
  This wouldn't eliminate man-in-the-middle attacks, but it would only make them possible when I press the button, which is when I'm near my car.
  I don't think the cost of pulling out my phone, opening the app, and pressing a button is worth it to defend against this.
  Instead, I plan to have the phone app send a toast notification whenever it sends an unlock message.
  Although when I see the message, it is too late to stop the attack, at least I can be aware if it is happening.
  - I don't know much about countermeasures to avoid having my window broken.
  I suppose the common sense one is not to leave valuable-looking objects in plain sight.
  - I very rarely allow my phone out of my sight except in secure places like my apartment.

