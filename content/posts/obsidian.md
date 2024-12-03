+++
title = "Why Obsidian is the Best Note Taking Tool"
description = "My opinion on why I think Obsidian is the best note taking tool, period."
slug = "obsidian-note-taking"
tags = ["misc", "obsidian", "tools"]
toc = true
draft = false
date = 2024-12-01
cover = "/images/obsidian-logo.svg"
+++

## What is Obsidian?

Obsidian is "the private and flexible writing app that adapts to the way you think."[^1] It is perfect for journals, notes, project management/brainstorming, and so much more. All pages are written in Markdown format and saved locally to your computer in what Obsidian calls a "Vault". Each Vault is a separate directory and within that directory are your Markdown pages or even more directories to further organize your Vault.

## Why Do I Like It?

I had originally discovered Obsidian because of D&D, to tell the truth. It has _a lot_ of extensibility through official and community developed plugins. One plugin allows you to make "Dataviews" which are really fancy data driven tables. Another enables the use of a completely custom templating language that can trigger when a new note is created. There are lots of really powerful plugins that made DMing for D&D much easier.

But after D&D was over, I had the knowledge of Obsidian and wanted to transfer it over to note taking with doing machines on Hack the Box.

## Using it for Writeups

Once I started this blog and made the decision to try to get into cybersecurity from my current position, I started using it for Hack the Box writeups. And, allow me to share my existing writeup template that I use.

```obsidian
---
boxName: <% tp.file.title %>
tags: []
---
> [!metadata|metadatatable]-
>
> | Field | Value |
> |------|------|
> | **Topics** | `INPUT[inlineList:tags]` |
> | **OS** | `INPUT[inlineSelect(option(Windows), option(Linux)):os]` |
> | **Programs** | `INPUT[inlineList:programs]` |
> | **HTB Difficulty** | `INPUT[Difficulty][:difficulty]` |
> | **Rating** | `INPUT[Difficulty][:rating]` |
> | **User Own** | `INPUT[toggle:userOwned]` |
> | **Root Own** | `INPUT[toggle:rootOwned]` |
> | **Quick Notes** | `INPUT[textArea:quickNotes]` |

# `VIEW[{boxName}]`

## Reconnaissance

## Enumeration

### Port xx

### Port xx

## Foothold

## Exploitation

## Privilege Escalation

## Lessons Learned
```

There are a few things in here that are not standard Markdown and are plugins that are found in Obsidian. I'll quickly go over everything that is not standard Markdown.

**<% tp.file.title %>**
This is the Templater plugin I mentioned earlier that has its own language. This tells Obsidian to insert the Note/file title upon creation. I do this in combination with another plugin I won't go over (but will put in a master list at the bottom for those that want it) that lets me enter the file name before it's created.

**> [!metadata|metadatatable]-**
This just creates a collapsible (noted by the "-" at the end) callout with the name metadata and a class of "metadatatable" that adds some additional styling. I can't remember if the additional styling is through Meta Bind or not, but I want to say not. This is just standard Obsidian markup, but isn't found in Markdown.

**INPUT[...]**
Any of the fields in the table that start or look like this are the [Meta Bind](https://www.moritzjung.dev/obsidian-meta-bind-plugin-docs/) plugin.

## References

[^1]: [Obsidian website](https://obsidian.md/)
