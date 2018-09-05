# Using Wireshark Filters
One of the most important feature sets in Wireshark is its filter capabilities, especially when you're dealing with files that are significant in size. Capture filters can be set before the fact, instructing Wireshark to only record those packets that meet your specified criteria.

Filters can also be applied to a capture file that has already been created so that only certain packets are shown. These are referred to as display filters.

Wireshark provides a large number of predefined filters by default, letting you narrow down the number of visible packet with just a few keystrokes or mouse clicks. To use one of these existing filters, place its name in the Apply a display filter entry field (located directly below the Wireshark toolbar) or in the Enter a capture filter entry field (located in the center of the welcome screen).

There are multiple ways to achieve this. If you already know the name of your filter, simply type it into the appropriate field. For example, if you only wanted to display TCP packets you would type tcp. Wireshark's autocompleting feature will show suggested names as you begin typing, making it easier to find the correct moniker for the filter you're seeking. 

Another way to choose a filter is to click on the bookmark-like icon positioned on the left-hand side of the entry field. This will present a menu containing some of the most commonly-used filters as well as an option to Manage Capture Filters or Manage Display Filters. If you choose to manage either type an interface will appear allowing you to add, remove or edit filters.

You can access previously-used filters by selecting the down arrow

<!--stackedit_data:
eyJoaXN0b3J5IjpbODMzNzY0MjEwLDE3MzU4NzQxMTRdfQ==
-->