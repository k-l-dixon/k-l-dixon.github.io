---
layout: essay
type: essay
published: true
title: The Power of Design Patterns
# All dates must be YYYY-MM-DD format!
date: 2022-04-27
labels:
  - Software Engineering
  - Design Patterns
---

### Understanding Design Patterns

Software design patterns are considered general, reusable solutions to commonly occuring problems in software design.  Much like the application of an alogorithm in various programming languages that each accomplishes the same or similar tasks.  At a higher conceptual level, design patterns provide a framework of processes developers can be use to handle common problem occurences, a system of systems.  Design patterns are well-proven and substantiated "lessons learned" from predecessors that assist in developmental processes by allowing designers to build upon these trials and tribulations as opposed to "reinventing the wheel" in some cases.  Design patterns are **NOT** concrete pieces of software, but abstractions utilized to "frame" solutions from.

### Elements of Design Patterns

Using design patterns we are able to communicate, identify, implement, and remember *general* solutions to common problems.  To accomplish this, there are four essential elements of design patterns:
>1. The Pattern Name
>> This name is typically a handle used that effectively describes a design problem.  This name should be descrptive in the sense to establish a shared understanding as the goal is to increase a catalog of patterns for the community.
>2. The Problem
>> The explanation and the context of the problem.  Be aware that this description sometimes describes **Symptomatic** problems as opposed to **Systematic** problems.
>3. The Solution
>> Again, **NOT** a concrete design or implementation.  This is an abstract general solution to the problem.
>4. Consequences
>> The results and trade-offs for applying the pattern.  Typically used for evaluating alternatives and for cost/benefits analysis.

### Categories of Design Patterns

Three fundamental groups of design patterns are behavioral, creational, and structural.

>Behavioral - describes the communication between objects of various classes along with the responsibilities and tasks between the objects.  
>> Chain of Responisbility Pattern

>> Command Pattern

>> Iterator Pattern

>Creational - emphasizes the way objects are created such that clients are decoupled from object initialization.   This leveages the creation of objects at runtime as opposed to compile time. Examples include: 
>> Singleton Pattern

>> Prototype Pattern

>Structural - focuses on how to assemble objects and classes into larger flexible structures.  Examples include: 
>> Adapter Pattern

>> Bridge Pattern

>> Composite Pattern

### Design Patterns Used in Practice

In practice, I have experience with using the Singleton Design Pattern.  This design pattern involves using a single class responsible for creating an object and allowing direct access to that object without need to instantiate the object of the class.  Working with BowFolios, we used a class defined as   "ProfileCollection" to create and export the instances of "profiles" to other entities.    


