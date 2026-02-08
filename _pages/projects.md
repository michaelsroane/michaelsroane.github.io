---
title: Projects
permalink: /projects/
layout: single
author_profile: true
toc: true
---

# Documentation Projects

During my career, I have worked on a variety of technical documentation types, including Release Notes, User Guides, and Internal Procedures. I have included samples of each type below, along with details about each type.

## Release Notes

### Process
Most Release Notes (RN) content derive from Software Engineering tickets created in Jira. New Features come from Stories. Resolved Issues and Known Issues come from Bugs. 

I create the new feature descriptions in the RN after the Software Engineers complete feature development. Concurrently, I document the new feature in the customer-facing technical documentation (e.g., User Guide, Installation Guide, Administrator Guide). 

I create resolved and known issues lists based on the bug tickets in Jira. Resolved issues derive from completed bugs, while known issues derive from open or in progress bugs. As QA starts, I review the bug lists daily. I run specific queries to see the bugs attached to the release and their current status. I meet with the Software Engineering leads and Program Management team to go over any discrepancies and updates. 

### Toolchain
I created the RN as DITA topics. Each section (About, New Features, etc) is an individual DITA topic under one ditamap. I created the ditamaps and dita files in Heretto, our CCMS, and published the RN to our public Documentation Portal from Heretto to Zoomin.

I re-created the topics here in Markdown.

### Challenges
Challenges arise towards the end of the product release lifecycle after the Software Development team completes their development work and the QA team is testing the product. 

During this process, QA creates new bugs that can require additional development work. As new bugs come in, the Resolved Issues and Known Issues lists change daily. Some resolved bugs are added to the RN while other bugs are deferred to later releases and added to the Known Issues list. Depending on the release process, RN can be finalized within one week of the General Availability (GA) release date.

Additionaly, some bugs are labeled incorrectly in Jira, so they are missing from queries and not included in the RN. Communication is the key to finding mislabeled bugs. Engineering and review teams are familiar with each bug recorded in this release and can more easily spot high-value bugs that are missing in the RN. 
 

### Sample
[Sample Release Notes](/rel_notes_example/)

## Procedure (How-To)

### Process
This sample includes a set of individual topics published within a User Guide for a new desktop agent that replaced a legacy agent. This sample includes both concept topics and task topics. 

During the development of the new desktop agent, I worked with the Software Engineering team, the Support team, and the Network Engineering team to finalize the steps required to deploy the new agent on our customers' endpoints. The Network Engineering team and I walked through the configuration update in real-time to follow the written procedure and update the text as needed.

### Toolchain
The original files are DITA topics. I created the original topics in the Oxygen editor and used SVN for version control. I published the ditamaps to PDF and WebHelp transformation scenarios in Oxygen, then uploaded the published files to Salesforce.

I recreated the topics here in Markdown.

### Challenges
The original procedure provided by the Network Engineering team contained vague instructions and assumed an expert level of knowledge. The intended audience was System Administrators, but we wanted to add additional details for use cases where junior-level SAs would complete the configuration. These additions required many new steps. Per our Style Guide, we tried to keep procedures to 4-6 steps, but this procedure required many more steps. After some internal debate, we decided to keep this procedure as one long procedure instead of breaking it up (either into separate procedures or moving more details into sub-steps)

### Documents
Provide a list of documents where I would write procedures: User Guides, Configuraiton Guides, etc.

### Sample
[Sample Procedure](/how_to_example/)

## Procedure (Internal Wiki)

### Process
Technical Publication teams rely on our collective knowledge to create and improve our processes. When we update our tools, we must work together to ensure a quick transition. When one of my Technical Publication teams migrated to a new tool, I was selected as an administrator for the tool and I was responsible for the initial migration of content into the tool. During this process, I learned about the new tool before the rest of the team and became the team's Subject Matter Expert. To get the team up to speed, I created a series of internal procedures in our internal wiki on Confluence. This sample shows one procedure I created.

### Toolchain
I created this procedure in Confluence. The Technical Publications team ceated all internal content on Confluence.

### Challenges
I wrote the internal procedures while I was learning the new tool. I wrote some procedures based on my initial tool usage and discussions with the tool's Solution Architect. As I worked with the tool, the procedures changed constantly as I developed more efficient workflows or as our team guidelines evolved. The constant changes were difficult for some writers to track, because they didn't access the wiki daily. I started to provide daily updates on our team Slack channel to summarize the updates. This led to more page views, which led to more interactions with the other writers, who provided comments and feedback.

### Sample
[Sample Wiki Procedure](/internal_wiki/)