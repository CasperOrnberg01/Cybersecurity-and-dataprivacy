# Final assignment for the project and course - Casper Örnberg NTIS22K 

## Cisco - Introduction to Cybersecurity
![cybersecurity - cisco](cisco.png)
Course was more like just recap of previous knowledge. I've had CCNA courses via Cisco, so there has been briefly from the cybersecurity aspect as well.
Inrtoduction to cybersecurity course had some basics on how to prevent them from happening, and guidance how to protect your and organization data, recognize some threats and common phishing types for example.
Course also had basics of devices related to cybersecurity and technologies.
I can't access the material anymore, since I completed it months ago, but if I recall correctly it was just basics what we've been learning across other courses as well.

<br>
<br>

## Portswigger
![portswigger - dashboard](psw.jpg)
Link to my reflections on portswigger labs: [Portswigger labs - Reflections](Additional_portswigger_labs.md)
<br>
Total portswigger labs completed: 20 (6 mandatory + 14 optional)
<br>
<br>

## The Booking System project
 
### Phase 1
- Setupped Kali linux environment, downloaded the application.
- Kali linux via VirtualBox + docker + Testing with burpsuite + ZaProxy.
- If I recall correctly, everything worked expect the virtualBox just sometimes froze due to the low settings ( storage, memory+ cpu, etc..)
- Most of time definetly took setting up the environment
- What new I learn from this phase was to perform some basic level penetration testing with ZaProxy and to identify vulnerability risks.
### Phase 2
- Performed penetration test with zap to the updated version of app
- Did password hacking attack by cracking passwords with hashcat.
- Learned to crack passwords
- I think most time took figuring out the masks for commands for phase 2 part 1
- on phase 2 part 2 did dictionary attack with burp suite first, then hydra.
- Then non-dictionary attack with burp and hydra.
- From the hashcat, web-interface attacks differ that they are done online. Hashcat ran locally.
- Overall on phase 2 learned to perform different types of attacks and then identify potential fix suggestions to prevent the security risks.
### Phase 3
- Learned on what to focus on authorization testing and how to approach the testing itself.
- Did manual testing via browser, to get familiar with updated application behaviour
- Second test with zaproxy and report.
- Third testing with wfuzz and http commands
- fourth technique was manual code review, where I linked functions to roles.
- Filled in authorization testing table along the process, what focused mostly on role based authorization (Guest/Reserver/administrator)
-Also published the zap report,a brief wfuzz summary and listed what missed from application (delete function in this phase).
- There wasn't particularly any part on this phase what took the most of the time.
### Phase 4
- GDPR compliance checklist for web-based Booking System
- Going through the gdpr checklist, involved alot of manual testing and skimming through the application via web-interface on different role users.
- Also reviewed the database different table structures and what is stored.
- Created Cookie policy, privacy policy and TOS .md files for the page.
- This phase was vital to gain some understading on the personal data, its processing and privacy policy and user consent. Also information on the legal side.
- Personally felt this phase was boring but I understand it's importancy.
### Reflection of the booking system projet
- I liked working with the booking system project, and setting up the environments by myself, I believe it is vital to gain the practical experience on penetration testing. I learned to perform penetration testing with different tools, and also to perform different types of attacks, and for example crack passwrods. What new I learned, was to work with ZaProxy, hashcat, hydra and then gained some additional experience by working with Burp Suite.
  
## Logbook

### Total hours
- 69 hours + (upcoming final exam?)

### Hours per topic
- Lectures + recordings: 19
- Cisco course: 9
- Portswigger: 10
- Booking system phase 1: 10
- Booking system phase 2: 11
- Booking system phase 3: 4
- Booking system phase 4: 4
- Final assingment: 2

### Link to logbook
[Link to logbook](logbook.md)

### Reflection on logbook
- Felt like logbook's purpose was to track the used hours on the course, and maybe estimate how long different subjects and assignments took to complete. Good tool to also analyze what has been done.

## (optional) Feedback
- I personally enjoyed the course, found it really interesting, and liked the approach where students has to set up the testing environment and dependecies by themselves.
- I have no suggestions to improve the course, expect I feel like the reflections on the assingments should be written immediately after their completion, so they are in the best fresh memory. Then they could be just attached for final report.
- It would be nice to have additional courses on cybersecurity, or perhaps change this course to 5 ECTS course.
