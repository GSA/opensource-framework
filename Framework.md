---
layout: default
nav: main
title: Open Source Framework
---
### GSA Open Source Framework

### Background
It is critical that GSA’s applications and services protect sensitive information and keep systems secure. Open sourcing code provides many benefits including lower cost, faster fixes, and greater flexibility. An additional benefit of opening source code lies with engaging stakeholders such as end users, third parties, and other government agencies. Engaging these stakeholders, seeking their feedback, and collaborating with them leads to a higher quality product. Programs within GSA may be reviewing or actively planning to open-source code within their programs. Some will decide not to release code for public consumption while other programs will decide that it makes good sense to provide code to the user community and set up feedback loops. In general, consistent with the [U.S. Digital Services Playbook] (https://playbook.cio.gov/#play13), the default should be open source.

When the decision has been made to open source code a primary factor to consider is striking a balance between openness, security and privacy considerations. This is not to say that closed source is inherently more secure than open source but that as part of the release process this balance must be achieved. This balance is best achieved by establishing procedures to make source code and documentation public and open for comment guided by the risk profile and security standards that govern the organization.
This document proposes a framework to be used as guidance for programs that have weighed the risks and benefits and have chosen the path of open sourcing software.

The framework consists of these areas:
- Licensing
- Scoping what is to be open-sourced
- Risk Profile
- Tools, Procedures, and Enforcement Methods
- Communications

### GSA-specific open-source overview
Refer to 18F's [write-up] (http://18f.github.io/open-source-program/pages/policy_documents/) on increased implementation of open-source projects government-wide for more background on what other government agencies are doing in this space. Here is a [page] (http://18f.github.io/open-source-program/pages/policy_documents/) specifically for open-source policies. Also GSA,in an Instructional Letter, [CIO IL-14-03](http://gsa.gov/portal/mediaId/195155/fileName/CIO_IL-14-03_Information_Technology_(IT)_Integration_Policy_(Signed_on_July_24__2014)_(With_live_links).action), states that [18F’s open-source policy] (https://github.com/18F/open-source-policy/blob/master/policy.md) is best practice for developing Open-Source Software (OSS).

### Open Source Projects
At the start of designing a new service or feature, the project team lead should engage the appropriate privacy, security, and legal officer(s) to discuss the type of information collected and the type of code developed, how it should be secured, and how it may be used and shared. The project should also be utilizing an accepted software development lifecycle where security is foundational in the architecture and design of the software. Architectural designs will go through a security review process such as conforming to currently supported technologies and proven design and configuration standards.Many open source project developers will utilize existing open source software products when designing the tool or the service. A detailed list of all open source tools must be maintained in the case that a vulnerability is discovered so that it can be traced to which tool or module of the open source software is affected. 
Plan to apply automated scanning for such vulnerabilities as specified by the Security Content Automation Protocol (SCAP), which provides specific standards from which security policies can be evaluated and to enable automated vulnerability management. For example, GSA uses [Nessus] (http://www.tenable.com/products/nessus-vulnerability-scanner) to implement automated security capabilities based on the SCAP method. Nessus is an open-source network vulnerability scanner that uses the Common Vulnerabilities and Exposures architecture for easy cross-linking between compliant security tools.

### Licensing 
In general, works of the United States Government are not entitled to copyright protections in the United States. See 17 U.S.C. § 105. Accordingly, works of the United States Government and works on behalf of the Unites States Government performed by government contractors, should be declared to be in the Public Domain. Further works funded and performed by government contractors should, in general, be considered as work by the Government and therefore be in the Public Domain. (As a best practice, such works should be licensed with a CC0 license, which ensures that the work is in the Public Domain worldwide). The current version of the CC0 license is 1.0. Refer to [creativecommons.org] (https://creativecommons.org/) for the most recent version of the license.

Project documentation for works that are not of the United States Government should unambiguously declare the license under which the project is distributed (e.g, General Public License (GPL), MIT License (MIT)) and that any code publicly posted in association with the project (e.g., pull requests, code comments) must be licensed under the same terms. The most common license are GNU and MIT [opensource.org] (http://opensource.org/licenses). To accommodate code contributions, consider adding a `CONTRIBUTION.md` stating that contributors agree to license their work in the same manner, in the root of the repository in addition to the `LICENSE.md` (best practice is not not edit the license file and to add an addtional file with specifics on contributing to the project). In addition, GitHub will add a link to that file at the top of the forms for issues and pull requests, so potential contributors will be informed that the repository has a contribution policy. Under this approach, it's a good idea to reference both documents in `README.md`. 

In addition to licensing, the program should consider if any of the content to be open sourced should be copyrighted or trademarked. Materials such as a program logo may have to be copyrighted or phrases such as program name and other intellectual property may need to be trademarked.

### Scoping what is to be Open Sourced
An Open Source plan should clearly state the scope of the services, APIs, workflows, interfaces, modules, extensions, and associated code base that is to be open sourced. When designing and architecting features the team should specify whether the implementation of the feature will be open sourced or if it would only be limited to a front end. For example, an entire API implementation including all supporting components such as data.gov can be open and accessible to all. In this example the team gives the public access not only to the data but to the APIs themselves. As a program evaluates the scope of what it will open source, it should delineate criteria for out of scope based on the nature, requirements, and sensitivity of the program in general.  

In an agile environment, it may be useful to approach the Program Backlog with the intent of designating features or stories as either open source-eligible or to be maintained as closed, based on risks inherent to design. This approach enables product managers and sprint teams to understand up front whether or not their efforts should be subject to additional design considerations and security review criteria, not already specified in the Federal Security requirements, specific to the open source requirements.  It’s advisable to plan to build and document software in a modular fashion, to maximize the potential value of the open source code.

### Risk Profile
As with any software development project, a risk management plan must be developed to identify where the potential vulnerabilities are and what the likelihood of the vulnerability occurring is, and choose whether to accept or mitigate the risk. The program’s risk management should specifically address the areas of risk associated with an open-source project such as; the process of creating and maintaining a public branch of the code, the licensing of the code, and independent verification of the public code itself. A key process to building a secure service is to comprehensively test and certify the components in each layer of the technology stack for security vulnerabilities, and then to re-use these same pre-certified components for multiple services. Although a component is pre-certified, periodic testing of that component is necessary to ensure it is validated and not subject to any new vulnerabilities.

The biggest concern most organizations have with using Open Source is that often times there is no one entity taking the lead for security assurance. However as a counter-weight one of the benefits of utilizing Open Source is that the code is open and accessible so an organization can run security scans that are required and appropriate for that environment. 

## Principles of Open Source Software Risk Management
Never at any time should configuration information such as IP addresses, etc. be published to the public. An organization's open-source plan will need to specifically address what tools and procedures will be employed to create and manage risk associated with the public branch of the code. Here are specific areas to pay attention to when determining what comprises the public branch of the code:
Physical configuration - including items behind reverse proxies firewalls
Code logic - this includes logic and/or business rules that are not for public consumption. For example, no hard coded rules that would expose information that is not appropriate for the public. Another example is hard coding an item that requires elevated access to view.
Code and Data - the code must be scanned and virus-free. There should be no vulnerability that would create a loophole. For example usernames, machine names, keys, passwords should not be revealed in the code or in the data. Careful attention must be paid to not release PII information to the public. 
Consistently track all the software libraries and versions that are utilized in the environment. This way when a vulnerability is discovered there is one source to go to see what areas of the project could be affected
Establish a security audit process ensuring the code is free of security errors such as inadequate buffer protection, poor input validation, session management problems, etc.
Coding standards must be developed to assure implementation consistency and streamline review processes
Operations scanning - security scanning can be inherited from traditional security review processes

The open-source plan must specify the use of and employ the tools and procedures described above to ensure that no one can use the code to access unauthorized information. Open sourced code must be devoid of proprietary information or specific data access channel or protocol information.

### Tools, Procedures, and Enforcement Methods
The Open Source Management Plan should include definitions of procedural review gates that code must pass through in order to be released to the public. Without a mechanism to validate compliance to policy, having a policy for acceptable open source usage isn’t very effective. Before the code is published there are many enforcement methods such as establishing standards, architectural reviews, and branching strategies. 

If you have a security or verification step in your software development life cycle, add a step to that process to check for compliance to the open source policy. If this type of step doesn’t exist today, you can either create that gate or do periodic compliance checks. In some instances, if appropriate for the project (such as with highly experienced teams and a change that has minimal risk but would benefit the project if it were expedited ), code may be released to the public without prior review. Periodic checks and testing should nonetheless be included to ensure compliance with policy.

## Branching Strategy with Versioning Tools (Git and Github)
A Program may choose to split its project(s) code base for the purpose of enforcing protection of sensitive code. A typical use case may entail a Program internally creating a separate, tailored code repository for code to reside that will be open sourced. This repository would be maintained and reviewed by the appropriate controls, and serve as the source from which a publicly hosted remote (repository) is pushed and synced. Locally hosted/development branches would derive from and/or merge to the Master and/or Production, but would not ever be pushed to the local or remote open branches. So enforcement essentially becomes a bi-product of the branching strategy and the due diligence applied to the designated “open” code repository before it’s pushed to its public, remote repository on Github. Please see section below on Github Usage.

An Open Source plan should define the mechanisms or review procedures that code is subject to before being approved for open release.

That is to say,  local coding would be executed within local repositories and Program Increments (PI) (a PI is a discrete period of development time for the Agile Release Train that equates to a release cycle, that is, usually 4 increments and 12 weeks) are released into a Common Repository. A PI is when a release is executed, the code to be shared publically eventually goes into a Public Repository. Another way to accomplish this is to publish changes to a staging branch on a rolling basis and merge after periodic reviews.

Ideally working software code pushed to production will be published to a public repository as near to real time as possible. If however, there is a general concern regarding the sensitivity of code or code stability, there may be additional lead time required to validate the fitness of the code for open source.

A notional structure of the relationship of repositories to individual sprint team output is depicted below in the Scaled Agile Framework (SAFe) graphic below.  In this example each PI would  be released as a public branch of code.

<SAFE grapic here>


###Github Usage
What is Github?
GitHub is a third-party website that offers code repositories that developers can use to collaborate on software development projects in real-time. GitHub also provides social networking features that allow developers to follow open source projects, share code and learn how code changes are made throughout the development process. GitHub is so named because it utilizes the open source version control system (VCS) known as Git. There are many videos on how to use Github on [YouTube] (https://www.youtube.com/results?search_query=github) and on [Github] (https://github.com/).

## GSA's Account on GitHub
GitHub offers free public repositories for open source projects as well as subscription-based private repositories for closed projects. The GSA has created an organization account with GitHub, which includes a limited number of private repositories and unlimited public repositories. All GSA staff are encouraged to use GSA’s agency GitHub account for their projects if the account meets security, branding and other needs. There are valid reasons, however, not to use the GSA account:

1. A program office will benefit from having their own branding (including organization avatar, contact email, URL, etc.), rather than the generic GSA logo and contact information.
2. A program team may have multiple repositories that are less confusing to stakeholders and contributors to group together, without being lost in a sea of generic GSA repositories.
3. A program team may have higher security needs for particular repositories that merit a narrower range of user accounts with access to those repositories than those authorized to access @GSA repos.
4. A program team may wish to administer permissions for outside contributors differently than @GSA at large.
5. A program team may desire more flexibility in how they work, without needing to seek permission from @GSA Owners or Administrators to create and administer teams.

More guidance on when exactly to use the @GSA account is coming soon.

### Communications
Establishing a Community of Interest for the open source project is vital to its success. It works both ways; having an engaged community reviewing and commenting on code serves as an incentive to develop high quality code and the distributed model provides for rapid discovery and patching of bugs.

Simply making the code public is not enough. Open source developers want to get behind a cause. If they contribute, what will their code be used for in a six months or a year? As a result, open source project documentation (readme) commonly includes five primary pieces of information:

1. A project mission statement, philosophy, or goal
2. A features and requirements list, or long-term project roadmap, 
3. The status of the project (active development, beta, etc.)
4. How to submit an issue/feature request or contribute a fix/enhancement, and the licensing associated with any contributions to the repository; and
5. Licensing information

Internally to the project, procedures for handling community feedback must be established. Organizations may want to consider establishing a communications plan specifically for the open source projects. Communication activities related to keeping a Community of Interest involved and active may differ from communication plans that are geared to a general program.

Additionally, depending on the nature of the project, alternative channels of communication (such as blogs, social media, and meetups) should be used to highlight certain projects. 


We would like to hear from you. To let us know what you would like to see next, [click here](https://github.com/GSA/opensource-framework/issues).
