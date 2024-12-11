+++
title = "Why Obsidian is the Best Note Taking Tool"
description = "My thoughts on why Obsidian is the best note taking tool, period."
slug = "obsidian-note-taking"
tags = ["misc", "obsidian", "tools"]
toc = true
draft = false
date = 2024-12-04
cover = "/images/obsidian-logo.svg"
+++

## What is Obsidian?

Obsidian is "the private and flexible writing app that adapts to the way you think."[^1] It is perfect for journals, notes, project management/brainstorming, and so much more. All pages are written in Markdown format and saved locally to your computer in what Obsidian calls a "Vault". Each Vault is a separate directory and within that directory are your Markdown pages or even more directories to further organize your Vault.

## Why Do I Like It?

I had originally discovered Obsidian because of D&D, to tell the truth. It has _a lot_ of extensibility through official and community developed plugins. One plugin allows you to make "Dataviews" which are really fancy data driven tables. Another enables the use of a completely custom templating language that can trigger when a new note is created. There are lots of really powerful plugins that made DMing for D&D much easier.

But after D&D was over, I had the knowledge of Obsidian and wanted to transfer it over to note taking with doing machines on Hack the Box.

### Using it for Writeups

Once I started this blog and made the decision to try to get into cybersecurity from my current position, I started using it for Hack the Box writeups. I had a hard time getting motivated to actually take notes while hacking a machine, or even remembering. But, using what I learned about Obsidian from my short time DMing, it made it so much easier to get started and actually put thoughts down.

The template I came up with for machines is down below. Don't worry about the strange syntax right now.

There isn't much to say. I decided to draw up a template that would generate a Note that contained all of the important steps of a hack/pentest; reconnaissance, enumeration, exploitation, privilege escalation. There's a section for foothold that I use to put down the steps that I take after I've gained an initial entry into the machine.

Is it the best template? Probably not. But it's what got me motivated enough to actually start, so that has to count for something.

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

There are a few things in here that are not standard Markdown and are added syntax from plugins or Obsidian-specific syntax. I'll quickly go over everything that is not standard Markdown.

**<% tp.file.title %>**
This is the [Templater](https://silentvoid13.github.io/Templater/introduction.html) plugin I mentioned earlier that has its own language. This tells Obsidian to insert the Note/file title upon creation. I do this in combination with another plugin I won't go over (but will put in a master list at the bottom for those that want it) that lets me enter the file name before it's created.

**> [!metadata|metadatatable]-**
This just creates a collapsible (noted by the "-" at the end) callout with the name metadata and a class of "metadatatable" that adds some additional styling. I can't remember if the additional styling is through Meta Bind or not, but I want to say not. This is just standard Obsidian markup, but isn't found in Markdown.

**INPUT[...]**
Any of the fields in the table that start or look like this are the [Meta Bind](https://www.moritzjung.dev/obsidian-meta-bind-plugin-docs/) plugin. These `INPUT`s create input (duh) fields that let me add additional metadata to my note for things such as how difficult the box is rated on HTB, if I owned it, etc. Having this metadata in every note then enables me to create a Home Dashboard that has many Dataviews of all the different kinds of metadata. It's really powerful.

**VIEW[{boxName}]**
This is Meta Bind again. It binds that heading to whatever the frontmatter property `boxName` is.

### Example Dataview

Here is an example code fence for one of the Dataviews I have in my Home Dashboard.

```dataview "Example"
TABLE file.ctime AS "Created On", join(tags, ", ") AS Tags, os AS OS, programs AS Programs, difficulty AS Difficulty, rating as Rating, userOwned AS "Owned User", rootOwned AS "Owned Root", quickNotes as Notes
FROM "Hack the Box"
```

This may look somewhat like SQL and you'd be right. It's DQL, or [Dataview Query Language](https://blacksmithgu.github.io/obsidian-dataview/queries/structure/). It allows you to create massive tables of data with really short queries like this. At the time of writing this, here's a small screenshot of what this generates from my Vault.

![obsidian dashboard](/images/obsidian-dashboard.png)

## Taking Better Notes

Having the ability to quickly generate this template, while still being able to modify it on the fly (thanks to Obsidian pages just being Markdown), I feel I'm taking much better notes as a result. Not only is it easy, but it's more motivating to me to have something already somewhat written up that I can just _start_ with. When I first got into hacking, I had a hard time just getting started taking notes and documenting my process. This makes it so much easier.

The [writeups](/tags/writeup) I've done are posted here too if you want to take a look!

## The King of Note Taking

In my opinion, Obsidian is the undisputed King of note taking. It absolutely has some things that may not make it for you, but for me, it's perfect. It's extensible, powerful, and just plain fun to use. I can't recommend it enough. However, let's look at some of the good and bad.

### The Good

**Obsidian is incredibly fast.** It's fast at loading, fast at searching, and fast at rendering. It's just fast. Links to other notes and links to headings within notes are instantaneous. It's just a joy to use. Not only that, but let's say you have several notes that contain a link to one other note. That link is in a lot of places. If you change the name of that note, Obsidian will automatically update all of those links. It really helps with organization and keeping notes consistent and up-to-date.

**The Obsidian-specific syntax is really useful.** I sort of alluded to this earlier, but Obsidian has some specific syntax that is not found in the Markdown spec. One feature lets you link to other notes by using a double bracket syntax like `[[note name]]`. This is really powerful and makes linking notes together a breeze. It has [other](https://help.obsidian.md/Editing+and+formatting/Obsidian+Flavored+Markdown) syntax too like defining a block that can be referenced using the same double bracket notation anywhere in your Vault.

**The plugins!** Again, like I've somewhat already mentioned, Obsidian is very extensible with its abundant community driven plugins. There are plugins for everything from templating to creating custom tables to even creating custom views of your notes. It's really powerful and makes Obsidian a very versatile tool. Not only that, but even the official plugins are really good. There's a plugin to show a graph view of your notes and how they're linked together, slash commands from within a note, show all outgoing links from a note, and more.

**It's incredibly customizable.** Besides the plugins to customize and extend functionality, the UI and general user experience is also very customizable. You can add custom themes that completely change the look of the editor, you can include custom CSS snippets, and more.

### The Bad

**With great power comes great responsibility...or something.** While I've mentioned how powerful and extensible Obsidian is...it comes at a cost. There is some amount of programming literacy required. Though, it is not much and there are plenty of resources to help you get started. But, if you're not comfortable with programming or scripting, it may be a bit daunting and I'd totally understand someone being turned off because of this.

**It's not free.** Obsidian is free to use, but some of the more advanced features do cost money (looking at you [Sync](https://help.obsidian.md/Obsidian+Sync/Introduction+to+Obsidian+Sync) and [Publish](https://help.obsidian.md/Obsidian+Publish/Introduction+to+Obsidian+Publish)). For the serious note taker that wants to have their Vaults accessible across all of their devices (even mobile) and visible online, these features are available but not necessary at all.

**Obsidian isn't the only one that does all this.** While I have only been using Obsidian for a short time, I have heard that other note taking apps like [Roam Research](https://roamresearch.com/) and [Notion](https://www.notion.so/) do similar things. I've never used Roam Research, but I have used Notion and I do like it. But it isn't its own standalone application like Obsidian is that can be installed on your PC.

## Conclusion

I won't sugarcoat it. I love Obsidian. I love it for note taking for Hack the Box and I even love it for general note taking. It's powerful, extensible, and just plain fun to use. I can't recommend it enough. If you're looking for a note taking app that is fast, powerful, and fun to use, Obsidian is the one for you.

## Plugins I Use

I use quite a few more than this but these are the essentials in my opinion.

- [Templater](https://silentvoid13.github.io/Templater/introduction.html)
- [Meta Bind](https://www.moritzjung.dev/obsidian-meta-bind-plugin-docs/)
- [JS Engine](https://github.com/mProjectsCode/obsidian-js-engine-plugin)
- [Quick Add](https://github.com/chhoumann/quickadd)
- [Advanced Tables](https://github.com/tgrosinger/advanced-tables-obsidian)
- [Dataview](https://github.com/blacksmithgu/obsidian-dataview)

## References

[^1]: [Obsidian website](https://obsidian.md/)
