---
title: "Posts Manager AI"
date: "2020-01-21"
layout: single
tags:
- Bugs
categories:
- Notes
---


# Posts Manager AI

**Posts Manager AI** is a bot that works on managing posts by:
 1 - Removing Duplicated Posts
 2 - Removing Bad Posts ( Swear words )
 3 - Sets the Rate of Trendy of each post

**The Important Phase**:
  Before "Phase 1, Phase 2, Phase 3" it goes through a phase at which it gets
  data to learn from so i create 25 posts, 10 posts with bad words, 10 posts
  with trendy words, 5 posts duplicated. Then i teach the post by saying
  that is bad, duplicated, trendy, trendy and bad, etc.
  so i've got some data to start with then it goes through the 3 phases
  and saves its own data to teach itself.

**Phase 1**:
  Firstly it checks similarty between each post by each letter and each word 
  ( My " Arabic Posts " work around as you can't use python to read arabic words)
  Then it checks for the most voted / answered post and removes the other one

**Phase 2**:
  Secondly it checks each letter and tries to make up a combination by removing any
  Symbols in it so "F@@CK" becomes "FCK" and it is similar with "FUCK" and it checks
  the word in WikiDictionary to check if it is a good word so "KFC" is similar but
  it is a word that refers to a restaurant so it doesn't consider it as a bad word
  and it adds it to an array so it don't check it again.
  
**Phase 3**:
  Thirdly like the system of reddit votes, it checks the words of the post and trendy posts
  if they are similar the website shows that post first but before that it goes to phase 1
  and phase 2 so if it has any bad word it is removed before showing up first and it also
  checks if the duplicated of post is in the trend, if not it saves it in an array to learn
  from it so similar posts won't show first as it will be similar to trendy posts but not trendy
  
