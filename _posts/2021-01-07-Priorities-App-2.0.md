---           
layout: post
title: Priorities App 2.0
date: 2021-01-07 11:01:54 UTC
updated: 2021-01-07 11:01:54 UTC
comments: false
categories: apps design
---

<div class="separator" style="clear: both; text-align: center;">

<a href="https://1.bp.blogspot.com/-tyi2ReGsOhQ/XWgyEkUJfFI/AAAAAAAACHI/uEBfG2-aLOkK39fQuDsFoGgaeftjn7-HgCLcBGAs/s1600/Priorities.png" style="clear: left; float: left; margin-bottom: 1em; margin-right: 1em;">

<img border="0" data-original-height="360" data-original-width="360" height="200" src="https://1.bp.blogspot.com/-tyi2ReGsOhQ/XWgyEkUJfFI/AAAAAAAACHI/uEBfG2-aLOkK39fQuDsFoGgaeftjn7-HgCLcBGAs/s200/Priorities.png" width="200" />

</a>

</div>


### Simply manage lists of prioritized items

The second iteration of the Priorities App pushes further the minimalistic UX design and adds a new feature: lists of lists. I presented the motivation behind the app and the design of the first version in a [previous post]({% post_url 2020-08-09-Priorities-App %}). Priorities 2.0 is [available for download on the App Store](https://apps.apple.com/us/app/priorities-sorted/id1469567351).

The home screen looks exactly the same as in the first iteration. The model is completely backward compatible, and users who do not need the lists of lists feature will not even be aware of it. This was a strong design requirement for 2.0.

<div class="separator" style="clear: both; text-align: center; margin-top: 1em; margin-bottom: 1em;">
<a href="https://1.bp.blogspot.com/-KlJqYmNJp88/XtdeCTPRuBI/AAAAAAAAH4k/iJmE92Z-xugXXxboPlgJLlrrT7JHiJMQQCK4BGAsYHg/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2019-11-16%2Bat%2B10.09.06.png" style="margin-left: 1em; margin-right: 1em;"><img border="0" data-original-height="2208" data-original-width="1242" height="320" src="https://1.bp.blogspot.com/-KlJqYmNJp88/XtdeCTPRuBI/AAAAAAAAH4k/iJmE92Z-xugXXxboPlgJLlrrT7JHiJMQQCK4BGAsYHg/s320/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2019-11-16%2Bat%2B10.09.06.png" /></a>
</div>

The new feature is the ability to define&nbsp;inclusion relationships between any one item and any number of other existing items.

<div style="text-align: center; margin-top: 1em; margin-bottom: 1em;">
<a href="https://1.bp.blogspot.com/--nCW_OKUEu4/XtdeDRaQIhI/AAAAAAAAH4s/RZsw2DkxPus0zzhdhKe24jV1oovV7nVHgCK4BGAsYHg/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2019-11-16%2Bat%2B10.09.25.png" style="text-align: center;"><img border="0" data-original-height="2208" data-original-width="1242" height="320" src="https://1.bp.blogspot.com/--nCW_OKUEu4/XtdeDRaQIhI/AAAAAAAAH4s/RZsw2DkxPus0zzhdhKe24jV1oovV7nVHgCK4BGAsYHg/w180-h320/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2019-11-16%2Bat%2B10.09.25.png" width="180" /></a></div>

From a user perspective, this mechanism provides a way to organize items hierarchically.

<div class="separator" style="clear: both; text-align: center; margin-top: 1em; margin-bottom: 1em;">
<a href="https://1.bp.blogspot.com/-y1qWmygLPJU/XzBDDO1xJXI/AAAAAAAAIMk/LR8H9gyOxQIRn9URqOOekbEkWH4Aug4IQCLcBGAsYHQ/s2048/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B11.34.16.png" style="display: inline; margin-left: 1em; margin-right: 1em; padding: 1em 0px; text-align: center;"><img border="0" data-original-height="2048" data-original-width="1152" height="328" src="https://1.bp.blogspot.com/-y1qWmygLPJU/XzBDDO1xJXI/AAAAAAAAIMk/LR8H9gyOxQIRn9URqOOekbEkWH4Aug4IQCLcBGAsYHQ/w184-h328/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B11.34.16.png" width="184" /></a>
</div>

Technically, it only amounts to a display/navigation convenience, as the underlying model is still a single master list of items.&nbsp; In practice an item can be a "subitem" of any existing item. This also means that the same item can appear in multiple other items.


### Search, add remove, create

While there is still a "create" button displayed when searching for an item from the root list, this is only to preserve the user flow from the last version. The new streamlined model for adding items ties into searching:

When in search mode:

- the first section lists all the matching sub-items in alphabetical order,

- the next section lists all the existing matching items that are not currently subitems; each item has an action button to be added as sub-item,

- the last section offers a "Create and Add Item" button automatically set to the search string

The suggested flow is for the user to look for the item they want to add, and create it if it does not exist yet. The creation is done in context, as the item is automatically registered as a sub-item of the list in which the user searched for it.

<div class="separator" style="clear: both; text-align: center; margin-top: 1em; margin-bottom: 1em;">
<a href="https://1.bp.blogspot.com/-8Ct9jyJ3ivg/XzBEM209-TI/AAAAAAAAINA/QPzcsvDkCCYOS1rBEHC7IisSaMbjw4PoACLcBGAsYHQ/s2048/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.17.08.png" style="clear: left; display: inline; float: left; margin-bottom: 1em; margin-right: 1em; padding: 1em 0px; text-align: left;"></a><a href="https://1.bp.blogspot.com/-tAbTQDOQcUk/XzBELz0F81I/AAAAAAAAIM0/_AU5bVibRFg4uUjqd-gBTTbMlnjdLKwnwCLcBGAsYHQ/s2048/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.16.23.png" style="clear: left; display: inline; margin-bottom: 1em; margin-right: 1em; padding: 1em 0px;"><img border="0" data-original-height="2048" data-original-width="1152" height="320" src="https://1.bp.blogspot.com/-tAbTQDOQcUk/XzBELz0F81I/AAAAAAAAIM0/_AU5bVibRFg4uUjqd-gBTTbMlnjdLKwnwCLcBGAsYHQ/w180-h320/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.16.23.png" width="180" /></a><a href="https://1.bp.blogspot.com/-4z_LCAdw1uM/XzBELqcpcDI/AAAAAAAAIMw/u1LVFvCl92AOfMqmez9tdRdgin_cDHYrQCLcBGAsYHQ/s2048/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.16.42.png" style="clear: left; display: inline; margin-bottom: 1em; margin-right: 1em; padding: 1em 0px;"><img border="0" data-original-height="2048" data-original-width="1152" height="320" src="https://1.bp.blogspot.com/-4z_LCAdw1uM/XzBELqcpcDI/AAAAAAAAIMw/u1LVFvCl92AOfMqmez9tdRdgin_cDHYrQCLcBGAsYHQ/w179-h320/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.16.42.png" width="179" /></a><a href="https://1.bp.blogspot.com/-8WEC8S45-Iw/XzBEL2ma4bI/AAAAAAAAIM4/Ci2nnADUHXUoaqhfMrq6OsAv6v0iA2B2gCLcBGAsYHQ/s2048/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.16.48.png" style="clear: left; display: inline; margin-bottom: 1em; margin-right: 1em; padding: 1em 0px;"><img border="0" data-original-height="2048" data-original-width="1152" height="320" src="https://1.bp.blogspot.com/-8WEC8S45-Iw/XzBEL2ma4bI/AAAAAAAAIM4/Ci2nnADUHXUoaqhfMrq6OsAv6v0iA2B2gCLcBGAsYHQ/w180-h320/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.16.48.png" width="180" /></a><a href="https://1.bp.blogspot.com/-8Ct9jyJ3ivg/XzBEM209-TI/AAAAAAAAINA/QPzcsvDkCCYOS1rBEHC7IisSaMbjw4PoACLcBGAsYHQ/s2048/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.17.08.png" style="clear: left; display: inline; float: left; margin-bottom: 1em; margin-right: 1em; padding: 1em 0px; text-align: left;"></a><a href="https://1.bp.blogspot.com/-oRsibeiXDiQ/XzBEMsv35rI/AAAAAAAAIM8/P_FW0Y2GxoIWmgJ7Bi1Ep6OxJF0cTbcdgCLcBGAsYHQ/s2048/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.17.01.png" style="clear: left; display: inline; margin-bottom: 1em; margin-right: 1em; padding: 1em 0px;"><img border="0" data-original-height="2048" data-original-width="1152" height="320" src="https://1.bp.blogspot.com/-oRsibeiXDiQ/XzBEMsv35rI/AAAAAAAAIM8/P_FW0Y2GxoIWmgJ7Bi1Ep6OxJF0cTbcdgCLcBGAsYHQ/w180-h320/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.17.01.png" width="180" /></a><a href="https://1.bp.blogspot.com/-8Ct9jyJ3ivg/XzBEM209-TI/AAAAAAAAINA/QPzcsvDkCCYOS1rBEHC7IisSaMbjw4PoACLcBGAsYHQ/s2048/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.17.08.png" style="clear: left; display: inline !important; margin-bottom: 1em; margin-right: 1em; padding: 1em 0px;"><img border="0" data-original-height="2048" data-original-width="1152" height="320" src="https://1.bp.blogspot.com/-8Ct9jyJ3ivg/XzBEM209-TI/AAAAAAAAINA/QPzcsvDkCCYOS1rBEHC7IisSaMbjw4PoACLcBGAsYHQ/w180-h320/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.17.08.png" width="180" /></a><a href="https://1.bp.blogspot.com/-15XDfLNEyjs/XzBENOMwTQI/AAAAAAAAINE/3hP74o90YWIHSXDUl3AddFz0G-fkOOcGgCLcBGAsYHQ/s2048/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.17.27.png" style="clear: left; display: inline; margin-bottom: 1em; margin-right: 1em; padding: 1em 0px;"><img border="0" data-original-height="2048" data-original-width="1152" height="320" src="https://1.bp.blogspot.com/-15XDfLNEyjs/XzBENOMwTQI/AAAAAAAAINE/3hP74o90YWIHSXDUl3AddFz0G-fkOOcGgCLcBGAsYHQ/w180-h320/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.17.27.png" width="180" /></a><a href="https://1.bp.blogspot.com/-oRsibeiXDiQ/XzBEMsv35rI/AAAAAAAAIM8/P_FW0Y2GxoIWmgJ7Bi1Ep6OxJF0cTbcdgCLcBGAsYHQ/s2048/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2020-08-09%2Bat%2B18.17.01.png" style="clear: left; display: inline; float: left; margin-bottom: 1em; margin-right: 1em; padding: 1em 0px; text-align: left;"></a>
</div>

### Edit

The item view offers an edit mode for the user to update the item's name and description, and to manage the sub-items:

- the first section lists all current sub-items with an action to remove as sub-item of the current item (this does not delete the item from the general pool or from other items where it is currently a sub-item),

- the second section lists all existing items that are not currently sub-items, with an action to add as sub-item,

- in search mode, the first two sections only display matching items in the relevant category, and the last section offers a "Create and Add Item" button automatically set to the search string

<div class="separator" style="clear: both; text-align: center; margin-top: 1em; margin-bottom: 1em;">
<a href="https://1.bp.blogspot.com/-uAuwLp-OTZY/XtdeDgrNbjI/AAAAAAAAH4w/qdd3cFypad0ZE05ZRuvBL99gzUafGWRLgCK4BGAsYHg/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2019-11-16%2Bat%2B10.09.30.png" style="margin-left: 1em; margin-right: 1em;"><img border="0" data-original-height="2208" data-original-width="1242" height="320" src="https://1.bp.blogspot.com/-uAuwLp-OTZY/XtdeDgrNbjI/AAAAAAAAH4w/qdd3cFypad0ZE05ZRuvBL99gzUafGWRLgCK4BGAsYHg/s320/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2019-11-16%2Bat%2B10.09.30.png" /></a><a href="https://1.bp.blogspot.com/-6IG0YiRbTTw/XtdeEJeKZjI/AAAAAAAAH40/dh0pc5FIYTYiOyC-69QSGNVGmeDHdts7ACK4BGAsYHg/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2019-11-16%2Bat%2B10.09.43.png" style="margin-left: 1em; margin-right: 1em;"><img border="0" data-original-height="2208" data-original-width="1242" height="320" src="https://1.bp.blogspot.com/-6IG0YiRbTTw/XtdeEJeKZjI/AAAAAAAAH40/dh0pc5FIYTYiOyC-69QSGNVGmeDHdts7ACK4BGAsYHg/s320/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2019-11-16%2Bat%2B10.09.43.png" /></a>
</div>

Adding or removing an item from a list of sub-items does not destroy the item itself - this is done by tapping the bin icon in the top left of the item edit screen, and requires confirmation as this is a destructive operation. A deleted item will be removed from all sub-item lists in which it appears.

### Simplify!

Updating the priority of an item is best done in place while browsing the list, by swiping left or right.

<div class="separator" style="clear: both; text-align: center; margin-top: 1em; margin-bottom: 1em;">

<a href="https://1.bp.blogspot.com/-cAYvgPvufbo/XtdeEvTh9lI/AAAAAAAAH44/oSqVMtLgnh4cEKmFacjJwPrSB6AdGaz4gCK4BGAsYHg/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2019-11-16%2Bat%2B10.16.12.png" style="margin-left: 1em; margin-right: 1em;"><img border="0" data-original-height="2208" data-original-width="1242" height="320" src="https://1.bp.blogspot.com/-cAYvgPvufbo/XtdeEvTh9lI/AAAAAAAAH44/oSqVMtLgnh4cEKmFacjJwPrSB6AdGaz4gCK4BGAsYHg/s320/Simulator%2BScreen%2BShot%2B-%2BiPhone%2B8%2BPlus%2B-%2B2019-11-16%2Bat%2B10.16.12.png" /></a>

</div>

The pretty(?) but redundant and space-filling custom control featured in the first version's item view makes way for the sub-item list in this new version.

### Summary

This version introduces a new feature, some simplification. Since the app design relies so much on finding and using the search, the main question remains whether those features are easily discoverable by a first time user. As for the next steps, SwiftUI enters the scene and everything is up for rethinking.

[Priorities](/priorities) is [available for download on the app store](https://apps.apple.com/us/app/priorities-sorted/id1469567351).
