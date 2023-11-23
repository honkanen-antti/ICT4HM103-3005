# Secure Software Development
What to keep on mind when building applications in modern era. This writing presents my personal opinions about the subject matter as a coding project manager with over decade of experience.

## Disclaimer
This is not exhaustive list nor contains technical details and instructions how to avoid vulnerabilities completely. Purpose of this writing is to give some food for thought when working with software projects.

## Simplified life cycle of a software
1. Need for solution arises
2. Specifying the problem
3. Designing the solution
4. Implementing solution
5. Testing the implementation
6. Running acceptance testing to implementation
7. Deploying/installing the solution, AKA starting the production use
8. Maintaining the solution
9. Solution comes obsolete and gets removed

In Agile world development runs in increments so steps 2-8 run multiple times and basically for each iteration the steps 2-8 are run. Below you can see intentionally provocative picture how cost of fixing vulnerability increase by each step. The earlier the vulnerability is added to solution and later it is discovered, the more it will cost to fix it.

![Picture 1. Cost of fixing serious vulnerability](/cost-of-fix.png)

## Specification phase
- What is the problem we are trying to solve?
- What kind of data does the system has?
  - Does it need to be protected?
  - What kind of protection is needed?
- Are there laws or regulations that we need to follow?
- Keep the most important thing the most important thing.
- Good news is that you are only making specifications for the new system, so it cannot be hacked in this phase.

## Design phase
- Software and hardware architecture.
  - Where and how we will install this?
  - Who owns the hardware we run the application on?
  - Where it will be physically?
  - What components we are going to use (case cloud native application)?
- Data visibility
  - What fields are visible to who.
- What kind of users we have?
- Production use already on mind.
  - How things will look like when we are maintaining the solution?

## Implementation and testing
- 3rd party libraries and packages.
  - Speed up the process, but increase complexity.
  - Usually by default prevents injections!
  - Dependencies and their dependencies
    - npm package manager and companions.
  - How to make sure packages we use are secure?
- OWASP Top 10 is pretty big thing.
- What kind of guidelines we follow for secure development?
  - What kind of tests are required for the code before they can be merged?

## Acceptance testing and deployment
- Final opportunity for security testing
  - If we are lucky, includes penetration testing by 3rd party.
  - If we are not that lucky, does some shareholder has experience from penetration testing?
- Who are going to test the solution and how?
- Do we have automated tests available?

## Production use and maintenance
- Monitoring normal use and abnormalities.
  - What is normal and what is abnormal?
  - When something crashes, how do we notice it and recover from it?
- Security updates
  - How do we see when update is released to packages we use?
  - How often do we install updates?
- What kind of backups we are using?
  - How can we restore the system when something goes wrong?
  - Disaster recovery is key here!

## Good practices, insights and final words
Good practices:
- Build automation:
  - Automatically scanning vulnerabilities from source code and libraries used.
  - Automatically testing (not just testing the use cases, but also security).
- Start with security/Security first thinking all the time.
  - Try to think like attacker.
- Educate all the parties involved about cyber security.
  - Not exhaustive training, but raising awareness goes a long way.
- Penetration testing is a real thing.
- Also pipelines (building and deployment) need to be secured.

Conclusion:
- Security needs to be on mind in every phase.
- Security is everyone’s job and everyone’s responsibility.
- Having at least one developer in the team with interest/experience in cyber security increases security a lot.
- Don’t just trust, get a proof that things are enough secure.
- There is no such thing as perfectly secure system, every system has a flaw (most likely even many). Accept that and aim for the enough secure system.

## References, inspiration and other related links
- Katakri: https://um.fi/documents/35732/0/Katakri+-+2020_1218.pdf/ab9c2d4a-5031-3670-6743-3f8921dce8c9?t=1608302599246
- Tran, D. 2023. Secure Software Development: https://www.perforce.com/blog/sca/best-practices-secure-software-development
- OWASP Top 10: https://owasp.org/www-project-top-ten/
