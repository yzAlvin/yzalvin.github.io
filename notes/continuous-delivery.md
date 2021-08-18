---
layout: post
title: Continuous Delivery
date: 2021-05-13
permalink: /notes/continuous-delivery
---

# Learning Rubric

| Level | Attributes |
| ----- | ---------- |
| L1	| Can explain the benefits of using a service to run your containers. Can get the project running in a service manually. |
| L2	| Can articulate what the various components of your infrastructure achieve. Project can be deployed from a configuration file via the command line. |
| L3	| Can articulate the benefits of having infrastructure as code. Project is deployed from a build pipeline using infrastructure as code concepts. |
| L4	| Articulates the full continuous integration, continuous deployment and continuous delivery concepts and how it impacts the customer. Has implemented automation to deploy software to multiple environments (eg “sit” and “prod”) and can explain the processes used. |

## What is it?
a software development discipline where you build software where you build software in such a way that the software can be released to production at any time.

You are doing continuous delivery when:
* Your software is deployable throughout its lifecycle
* Your team prioritises keeping software deployable over working on new features
* Anybody can get fast, automated feedback on the production readiness of their systems any time somebody makes a change to them
* You can perform push-button deployments of any version of the software to any environmen on demand

The key test is that a business sponsor could request that the current development version of the software can be deployed into production at a moment's notice, and nobody would care/panic.

Continuous delivery is sometimes confused with continuous deployment.

Continuous deployment means that every change goes through the pipeline and automatically gets put into production, resulting in many production deployments every day.

Continuous delivery just means that you are able to do frequent deployments but may choose not to do it, usually due to business preferring a slower rate of deployment. In order to do Continuous Deployment you must be doing Continuous Delivery.

Continuous Integration usually refers to integrating, building, and testing code within the development environment. Continuous delivery builds on this, dealing with the final stages required for production deployment.

## Why

Benefits
* Reduced Deployment Risk
Deploying smaller changes, less to go wrong, easier to fix.
* Believable Progress
if "done" means "developer declares it done" that's less believable than if it's deployed into production
* User Feedback
Biggest risk to any software effort is that you end up building something that isn't useful. The earlier and more frequently you get working software in front of real users, the quicker you get feedback to find out how valuable it really is.



## Who

## When

## Where

## How

You need
* a close, collaborative working relationship between everyone involved in delivery (devops culture)
* extensive automation of all parts of the delivery process, usually a deployment pipeline.

# gocd
## Continuous Delivery 101

### Important Concepts
Agile and Lean
Continous Integration
Integrate code into a shared repository several times a day, each check-in is verified by an automated build, feedback allows teams to detect problems early.
Requires quite a bit of automation.
Gain confidence in code. CI is a prereq to continuous delivery.
Deployment schedule is determined by when people can do work, instead of when business needs software

Continuous Delivery
Automate deployment and testing on prod-like environments.
every build is run through a deployment pipeline
The goal here is to ensure that the software can be deployed at any time simply by clicking a button
THe deployment itself has been tested over and over -> confidence, 
when to deploy value to customers is a business descision, not a technical constraint

Continuous Deployment
no human interaction at all after code commit, if all tests pass it gets deployed immediately
some would say continuous deployment is more rigorous.
Great option for systems you control like web-based applications, but not so much for systems that need to be installed by end-users.
Decide what is an acceptable rate of change for your business when deciding on whether continuous delivery or continuous deployment is your goal

DevOps is a **Culture** 

Deployment Pipeline
Steps the software takes between code commit and production.
Delivery Team -> Commit -> Build and Unit Tests -> Regression Tests -> User Acceptance -> Deploy
Don't accept 'that test always fails' explanations
User Acceptance, continuous delivery and continuous deployment differ here; some one makes a business decision, feature completeness or any other factor.
A good deployment pipeline has many feedback loops along the way. At each stage of the pipeline, verifications are run, if they pass the pipeline continues, if they fail, the team responds appropriately.
Poor quality will never reach production in a well-designed pipeline.

Types of Automated Testing
Unit Tests
* fast
* easy to maintain
* push as much as possible here
* be careful with metrics, not useful unless team is learning basics
* do not fight a framework to make tests fast

Regression Tests
* verify that the entire application actually works
* should be 100% automated
* Does not mean slow, flaky tests
* Don't couple them to small stories or tasks
* Written by programmers, avoid drag-and-drop
* Execute these in parallel

Performance Tests
* Meet specific performance criteria
* Do not leave this phase for last
* Be realistic about your need to reach web-scale
* Utilise production monitoring


Monitoring
You build it, you run it
The team is notified when something is broken
Have a plan to respond quickly
Be thoughtful about monitoring alerts
Keep a database of events


Common Misconceptions
You can't "do" DevOps -> generally don't support the idea of a devOps team
Continuous Delivery and DevOps are not the same thing -> CD is something you do as part of DevOps culture
User testing is still important -> Usability testing, User acceptance testing

### CD Principles and Best Practices
Repeatable Reliable Process
Use the same process everywhere
Keep build logic out of CI/CD tools
Use scripts that are called by build tools

Automate Everything
Regression Testing is often done manually, but should not be
Using modern tools, entire environments can be provisioned automatically, nobody should have to ever login to any environment
Deployment should be completely automated, automation should have logic to use the same script or tools on any environment

Version Control Everything
Application Source Code
Configuration Files
Database Scripts
Documentation

Bring the Pain Forward
Do hard things first
Releasing more often helps manage risk

Done means released
It's not done if it's not live
Deployed != released
Consider methods like feature toggles
Releases are a business decision

Everyone is Responsible
"it works for me" is not valid
Culture change can be hardest
Management support is vital
Be careful with metrics -> goals should be *team* goals.

Decide if you're ready
DO you put everything in version control?
Do you practice continuous integration?

Value Stream Mapping
People from every step
People who actually do the work
Current state
	Process steps
	work from end and work backwards
	Value add time
	Lead time
Map out future state
Provision environments
Start up machines -> run tests -> shut down machines

Avoid prescriptive tools
One size does not fit all
Different products have different processes
People will use something else

You'll need more than one
CD Systems can be complicated
Use more than one source

Common tool categories
Source code management
Orchestration
Configuration management
Testing
Deployment


