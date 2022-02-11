---
layout: essay
type: essay
published: true
title: Do Or Do Not - Implementing Organizational Coding Standard
# All dates must be YYYY-MM-DD format!
date: 2022-02-09
labels:
  - Software Engineering
  - Learning
  - Coding Standard
---

## Coding Standards

 <img class="ui centered large spaced right circular image" src="../images/Coding-Standards.jpeg"> 

>What are coding standards? 

>What benefits do they provide?
 
  

Software engineering is a team driven process.  When developing code, other programmers will inevitably review the code for various reasons such as debugging or establishing an understanding of the code itself.  In large organizations, teams may become divided into smaller sub-teams working on multiple areas of the same code.  Working with lengthy and complex pieces of code, a concern would be merging these sections together in the end product.  A typical problem that arises are situations where functions or variables are defined and used in one area, but conflicts with how they are used in another area.  Another problem falls along the lines in debugging.  Situations where each code section is composed in an entirely different manner from one another.  Challenges arise attempting to read, understand, and troubleshoot these areas if needed.  This could become time consuming with numerous teams working under larger code projects, not to mention resources that need to be considered.  To mitigate this we can leverage the use of coding standards.

Coding standards are well defined rules with coding styles that each programmer should follow to maintain uniformity amongst the organization.  Benefits in using coding standards include: improving code readability, maintaining consistency, and maintains cost efficiency.  Code readability is a significant factor to consider as every programmer may offer vastly different programming styles.  Consistency in code promotes maintainability and allows the corrections of deficiencies earlier in the project, saving costs.  Some programmers feel that coding standards is an unnecessary limitation considering freedom and creativity in coding practices.  Others agree that using coding standards is a must.  There are a number of coding style tools such as Editorconfig, StyleLint, or ESLint.  I have recently been introduced to using ESLINT with Intellij. 

## ESLINT with Intellij 

<img class="ui centered medium image" src="../images/ESLINT.png"> 



My initial impression using ESLint with Intellij and it's very picky and selective "green check mark" <img class="ui mini spaced image" src="../images/greencheckmark.jpeg"> was a positive experience.  I feel it is a useful tool that has, and would most likely continue to, help me develop preferable habits with readability of my code.  Feedback patterns I immediately noticed were typical spacing, indentations, or small syntax errors.  In the short time since I have began working with ESLint with Intellij, I already notice and correct errors quicker or that I type my code while keeping in mind the errors I typically see to avoid seeing them at all.

One aspect I would like to see different with ESLint is differentiating errors of preferences and execution errors.  Under time, I immediately notice my attention is drawn to an error and I'd become fixated to changing the error to the infamous "green check mark".  On occasions I feel time is wasted as my train of thought comes to a halt to check red marks only to see it was a word considered "misspelled" by ESLint but is appropriately spelled for the context I need.  

## Overall Thoughts

I agree in using coding standards to promote uniformity amongst a team of programmers.  I feel this would streamline the comprehension of the various coding sections to help reduce the time it takes to decipher each others' work.  Much like I find myself correcting smaller errors that I quickly notice, I trust others would be able to do the same if the coding style is standardized across the team.  Any future project I believe I would search to develop, establish, and promote coding standards.  
