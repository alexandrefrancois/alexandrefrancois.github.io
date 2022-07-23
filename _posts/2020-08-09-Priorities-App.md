---           
layout: post
title: Priorities App
date: 2020-08-09 10:08:49 UTC
updated: 2020-08-09 10:08:49 UTC
comments: false
categories: apps design
---

<div class="separator" style="clear: both; text-align: center;">

<a href="/Priorities/assets/images/priorities-logo.png" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;">

<img border="0" data-original-height="360" data-original-width="360" height="200" src="/Priorities/assets/images/priorities-logo.png" width="200" />

</a>

</div>

## Simply manage a list of prioritized items

With a little bit of free time on my hands, I decided to get up to date on how to make an iOS app from scratch in Swift and publish it in the App Store (as a paying App, which turned out to be an interesting experience in itself). This blog post is about the motivation behind the app and the design of the first version (well, technically version 1.2 - [Download on the App Store!](https://apps.apple.com/us/app/priorities-sorted/id1469567351)).

### A list of prioritized items?

I have been thinking for a long time about a simple app to facilitate my grocery/essentials shopping: I always buy the same basic items (milk, bread, cheese, tomatoes, chicken, yogurt, etc.), all I need to know when I am shopping is which items I will need again soon (or urgently). When I realize I will need something soon, I need a simple way to find the item (if already in the list) and put it back in the list of things to get. If it's a new item, I should be able to add it easily, and not have to add it again in the future.

Until now I have been using Apple's Reminders app but I cannot automatically prioritize items and I cannot search, so it is not well suited for this approach. There is very likely some list app out there that can do what I need, but in this case I wanted to design my own.

### Priorities

The app defines items characterized by a name (string) and optional details (other string), and a priority level. There are 4 priority levels: low, medium, high and critical. The prioritized list only shows items that are at priority critical, high and medium, sorted by decreasing level of priority (and alphabetically by name in each priority level). For my shopping I think of medium as "get some if on sale," high as "we're running out soon," and critical as "we needed some yesterday."

<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody><tr><td style="text-align: center;"><a href="/Priorities/assets/images/priorities1-prioritized-list.png" style="margin-left: auto; margin-right: auto;"><img border="0" data-original-height="1600" data-original-width="900" height="320" src="/Priorities/assets/images/priorities1-prioritized-list.png" width="180" /></a></td></tr><tr><td class="tr-caption" style="text-align: center;">Prioritized list</td></tr></tbody></table>

### Lower Priority

When shopping, I look at the prioritized list. When I get an item on the list, I swipe left to lower its priority back to low (which removes it from the list).

<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody><tr><td style="text-align: center;"><a href="/Priorities/assets/images/priorities1-change-priority.png" style="margin-left: auto; margin-right: auto;"><img border="0" data-original-height="1600" data-original-width="900" height="320" src="/Priorities/assets/images/priorities1-change-priority.png" width="180" /></a></td></tr><tr><td class="tr-caption" style="text-align: center;">Change priority with a swipe</td></tr></tbody></table>

### Search and Create Items

When I need more of something, I search the list of existing items (pull down to reveal the Search bar and tap in it). I can see the list of all items sorted alphabetically.

<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody><tr><td style="text-align: center;"><a href="/Priorities/assets/images/priorities1-search.png" style="margin-left: auto; margin-right: auto;">
<img border="0" data-original-height="1600" data-original-width="900" height="320" src="/Priorities/assets/images/priorities1-search.png" width="180" />
</a></td></tr><tr><td class="tr-caption" style="text-align: center;">Search existing items or browse alphabetically</td></tr></tbody></table>

If I type something in the search, the list gets restricted to items whose name contains the search string. I am also presented with a "create item" button that uses the search string as the initial name for the new item. If the item I am looking for already exists, I can simply swipe right and select a higher priority level for the item. I can also adjust the priority by tapping on the item and changing the priority in the item view.

<table align="center" cellpadding="0" cellspacing="0" class="tr-caption-container" style="margin-left: auto; margin-right: auto; text-align: center;"><tbody><tr><td style="text-align: center;"><a href="/Priorities/assets/images/priorities1-create-edit.png" style="margin-left: auto; margin-right: auto;"><img border="0" data-original-height="1600" data-original-width="900" height="320" src="/Priorities/assets/images/priorities1-create-edit.png" width="180" /></a></td></tr><tr><td class="tr-caption" style="text-align: center;">Create or edit an item</td></tr></tbody></table>

If I tap the button to create a new item, I get to the item view where I can edit the name, details and set the item's priority. The item view also offers the option to delete the item entirely but that would be a rare occurrence for me since I don't want to have to create it again next time I need it.

### And that's it!

These are the basic operations - all that's needed to capture the requirements stated at the beginning.

[Priorities](/priorities) is [available for download on the app store](https://apps.apple.com/us/app/priorities-sorted/id1469567351).