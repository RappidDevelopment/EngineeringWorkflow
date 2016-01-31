<a name="http://rappiddevelopment.com">![logo](http://rappiddevelopment.com/media/image/logo-no-background.png)</a>
# RappidDev's Engineering Workflow
Website: [rappiddevelopment.com](http://rappiddevelopment.com)

### Purpose 
Here at Rappid Development headquarters, we mainly use GitHub, JIRA and Jenkins to help us to build software. We try to be as collaborative as possible and sometimes, keeping business stakeholders, product owners, developers, and testers all in sync during the software development lifecycle can be a tough task.  

We have deeply integrated these tools togther to bring all parts into one streamlined process. Issues in JIRA are automatically updated and transitioned based on a developer's work in Git; JIRA understands all branches, commits, pull requests and build/deployment statuses. Every issue is kept up to speed automatically, and developers, code reviewers, testers and business stakeholders can easily track core code changes, build statuses and prior pull requests. This ensures smooth handoffds between engineers and leads to better results, delievery times and higher quality software. 

This document outlines that process and can act as a reference for all team members.

## Table of Contents
* Developers - 
	* [Working a Ticket](#working-a-ticket)
	* [The Backlog & Failed Columns](#backlog)
	* [Branching Scheme](#branching-scheme)
		* [Stories](#story)
		* [Defects](#defect)
		* [Technical Stories](#tech-story)
	* [Automatic Transitions](#auto-transitions)
	* [Commit Conventions](#commit-conventions)
		* [Comment](#comment)
		* [Log Time](#log-time)
		* [Mark Subtask Done](#transition)
* ~~Testers~~ (Coming Soon)
	* ~~Testing a story~~~
	* ~~Writing a story defect~~
	* ~~Writing test cases~~
* ~~Product Owners~~ (Coming Soon)
	* ~~Creating a ticket~~
	* ~~Creating acceptance critera~~
* ~~C.I Information~~ (Coming Soon)
	* ~~Builds~~  
	* ~~Environments~~
	* ~~Deploying a build~~

## <a name="working-a-ticket"></a>Working a Ticket
Our Kanban board
![kanban-board](https://raw.githubusercontent.com/RappidDevelopment/EngineeringWorkflow/7d177c542f5743cea6340a42865509eebd1591a6/Screenshots/RDKanbanBoard.png)
Regardless if the project is using Scrum or Kanban, the board is where all work for the project is visualized. Tickets are never really assigned to anyone; the  team of developers pick them up as the project advances. 

### <a name="backlog"></a>The Backlog & Failed Columns
The *backlog column* is home to tickets ready to be worked, but that have not been started yet. These tickets contain a *definition of ready* and have the business requirements, acceptance criteria and implementation details outlined and understood.  

The *failed column* is home to tickets that have been implemented, but haven not passed code review, testing or acceptance from a product owner. There shoud be an explaination as to why the ticket failed.

To start developing, select a ticket from either column.

There are three types of tickets that can land in the backlog:  
1. **Story** - captures the description of a feature from an end-user perspective.  
2. **Defect** - a problem found after the story (functionality) has been accepted.  
3. **Technical Story** - focused on non-functional stories, for example: security, performance, or scalability related.  

### <a name="branching-scheme"></a>Branching Scheme 
![git-flow](https://raw.githubusercontent.com/RappidDevelopment/EngineeringWorkflow/d6405089483de476348fae8fb66377c73d95d08c/Screenshots/gitflow-diagram.png)
We normally follow a feature branching pattern. There are two main branches:  
* Master - current production code  
* Develop - code for next production release  
**Every ticket in [the backlog](#backlog) gets it's own branch.** Create a branch for the ticket you are working on and follow this convention.  

#### <a name="story"></a>1. Story branching convention
```  
feature/<ticket-number>
```
For example, let there be JIRA ticket WR-112  
```
$ git checkout -b feature/WR-112
```  
#### <a name="defect"></a>2. Defect branching convention 
```  
defect/<ticket-number>
```
For example, let there be JIRA ticket WR-78
```
$ git checkout -b defect/WR-78
```
#### <a name="tech-story"></a>3. Technical Story branching convention
```
technical/<ticket-number>
```
For example, let there be JIRA ticket WR-356
```
$ git checkout -b technical/WR-356
```
## <a name="auto-transitions"></a>Automatic Transitions
Once your branch is created, push it to the remote server.  
This automatically transitions the ticket from the *backlog* or *failed* columns to *in-progress*.  
Creating a pull-request for the branch will move the ticket to *code review*. The pull-request being merged will move the ticket to *testing* and the pull-request being closed will move the ticket to *failed*.
## <a name="commit-conventions"></a>Commit Conventions
JIRA supports **smart commits**. Smart commits allow you to log time, comment and transition a ticket.  
The general rule of thumb at Rappid Development is **branch for tickets, commit against subtasks**.  Commit messages should follow this standard.
#### <a name="log-time"></a>Log Time
```
<subtask-number> #time 1h 30m
```  
```
WR-113 #time 1h 30m  
```  
#### <a name="comment"></a>Comment
```
<subtask-number> #comment Updating README.md. Changes ready for review. #time 1h 30m
```  
```
WR-113 #comment Updating README.md. Changes ready for review. #time 1h 30m  
```  
#### <a name="transition"></a>Mark Subtask Done
```
<subtask-number> #done #comment Updating README.md. Changes ready for review. #time 1h 30m
```  
```
WR-113 #done #comment Updating README.md. Changes ready for review. #time 1h 30m  
```  



