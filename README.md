# SpamThrottleBCC

Burning Crusade Classic WoW addon to remove primarily duplicated messages on busy servers.

To install, click the "Download ZIP" button on the right hand side (above), which will download the SpamThrottleBCC-master.zip file. Inside that ZIP archive there is a folder called SpamThrottle. Copy that folder into the Interface/Addons directory under your main WoW installation.

	Version:	3.0 (BCC)
	Date:		6 July 2021
	Author:		Helltoast-Faerlina (a.k.a. Orukxu, original creator of SpamThrottle)

On many servers the world chat channels are unusable.  On some full servers, many people spam the channel to increase the visibility of their messages (or just be a general nuisance) by making macros and repeating the message once every few minutes.  This means you spend more time reading crap and less time interacting with normal people. I finally got fed up enough with that to update my previous retail version of ST for TBC classic. However I had problems originally with the GUI, so I haven't implemented that - this is the version using command line controls, and with no gold seller filtering (since it isn't needed).

This addon filters numbered channels, i.e. /1 through /99, and also /y so that any individual message is only displayed ONCE.  Repeats are filtered out, as long as the text is identical or very close.  A message is determined to be 'close' based on some heuristics.  It means you will only see unique LFG messages once.  On Faerlina for example this reduces traffic on the LookingForGroup channel by 70% to 80%, and makes the channel readable again.

Any message which is identified to be a duplicate of one sent earlier is "gapped", which means that it is only allowed to be shown once every X seconds - where X is settable by the user.  The default is 120 seconds (2 minutes).

The default is to hide the message entirely so that you never see the repeat.  If you want to see what you are missing, then you can set "color" mode, for which the repeats will be colored dark gray - easy to ignore, and gives you a sense of how bad the spamming problem is on your server.  The author recommends using the hide mode under normal circumstances.

Behavior:
	* Spam is filtered from the numbered channels, i.e. /1 to /99 (which includes the trade channel, the worst offender).
	* Spam on /y (yell) is treated the same as a numbered channel, and is filtered similarly.
	* The filter will not affect /s, whispers, raid/bg, guild chat and so on.
	* It won't filter your OWN messages AT ALL; they will show up as normal, even if you're performing the spam yourself. Shame on you.
	* It does not filter by keyword; but by the content of the message itself.
	* The first time a unique message arrives, it is always shown.
	* It is free-standing and compatible with other spam filters.
	* Repeated messages are allowed every X seconds, where X defaults to 600.  This is user settable.
  * The start of a keyword filtering system is in place. At the moment it will filter any message with "Boost" in it. You will need to go edit SpamThrottle.lua to remove that filter; just remove "BOOST" from the variable that has it.

Usage:
	/spamthrottle, or /st
	Shows whether it is enabled, the current mode and prints a list of valid commands.

	/st off
	Disables the spam filtering, making all spam messages show up as normal.

	/st on
	Enables the spam filter using the last known settings

	/st color
	Colors the spam dark gray to make it easy for the eyes to skip it.

	/st hide
	Completely hides all spam from ever being shown on the screen.

	/st fuzzy
	Enables the fuzzy text matching filter (default).  Filters messages that are very likely repeats, with slight changes only.

	/st nofuzzy
	Disables the fuzzy text matching filter. Only strict text matches of previous messages will be flagged as repeated spam messages.

	/st reset
	Resets the memory to start from scratch - effectively making the program forget all previous messages.

	/st X  (where X is a value between 0 and 10000)
	Sets the gap value for showing repeated messages to X.  Default is 600.
	Larger means less frequent repeats, smaller is useful if you do actually want to see messages again after a short
	interval of not allowing repeats.  Reasonable values are 30 seconds, 60 seconds, up to about 600 seconds.

	The filter defaults to 'hide' mode the first time you run it.
	You are then free to set the filter up to show the spam in dark gray (color mode) if you want to.

	The settings are remembered account-wide (affects all characters).

Changes:
	3.0 (07/06/2021): Initial release of revised original retail version for BCC

