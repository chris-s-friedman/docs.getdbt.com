---
title: "New IDE with performance and reliability improvements"
id: "ide-improvements-beta.md"
description: "Adding IDE performance and reliability improvements"
sidebar_label: "Enhancement: New IDE performance and reliability improvements"
tags: [Aug-16-2022, v1.1.52]
---

Building code on the dbt Cloud integrated development environment (IDE) should be seamless, and the tool that you’re using should not add more distractions to the data work that is often already confusing and difficult. 

The Classic IDE currently has severe performance and reliability issues. It takes a long time to start up the IDE, and the interactions (saving or committing) are slow.

Our focus is on performance and reliability, particularly around the following four metrics:

- Spinner time for cold start = Time that you see a spinner in a brand new session.
- Spinner time for hot start = Time that you see a spinner when you resume an existing session (return within 3 hours).
- Time to save = Time between saving a file and the IDE being ready for edit.
- Time to git = Time between making a commit and the IDE being ready for edit.

**Improvements:**

To address the issue, we rebuilt the IDE and made some significant architectural changes to the way we work. These changes will help improve the IDE performance and reliability:

- Your IDE spinner and interaction time will be faster, regardless of the size of your dbt project.
    - Instead of fetching and downloading all the contents for the files during any change, the IDE only needs the file tree/name. This means that starting up the IDE should no longer depend on the size of the dbt project (the larger the project, the slower it is). This also helps make the interaction with the IDE (saving files and committing changes) more snappy.
- Your IDE spinner time will be quicker and you can access it without needing to wait for the rpc server to finish getting ready.