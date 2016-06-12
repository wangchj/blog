---
layout: post
status: publish
published: true
title: Setup TF2 Dedicated Server (Windows)
author:
  display_name: Jeff
  login: admin
  email: cjw39@hotmail.com
  url: ''
author_login: admin
author_email: cjw39@hotmail.com
wordpress_id: 83
wordpress_url: http://codenuggets.com/?p=83
date: '2012-03-02 22:49:46 -0600'
date_gmt: '2012-03-02 22:49:46 -0600'
categories:
- Uncategorized
tags: []
comments:
- id: 43
  author: Ronald Shutt
  author_email: Spieth830@gmail.com
  author_url: http://www.qfhhtzbr.net
  date: '2012-04-04 17:57:50 -0500'
  date_gmt: '2012-04-04 17:57:50 -0500'
  content: Perfectly pent articles, Really enjoyed looking through.
- id: 73
  author: mini crane hire
  author_email: Lamark187@yahoo.co.uk
  author_url: http://cranehire.livejournal.com/
  date: '2012-04-07 21:32:51 -0500'
  date_gmt: '2012-04-07 21:32:51 -0500'
  content: I think  you have mentioned  some very interesting points ,  appreciate
    it for the post.
- id: 84
  author: Verona Zoldak
  author_email: 76Schlabs@yahoo.com
  author_url: http://www.deliciousmark.info/Business
  date: '2012-04-07 21:37:36 -0500'
  date_gmt: '2012-04-07 21:37:36 -0500'
  content: It's actually a nice and useful piece of info. I am happy that you just
    shared this helpful information with us. Please stay us up to date like this.
    Thanks for sharing.
---
Steps to setup a dedicated TF2 server on Windows 7 machine.

1. Install Steam client: <a href="http://store.steampowered.com/about/">http://store.steampowered.com/about/</a>. See note 1 below.
2. Install Server Installer hldsupdatetool.exe which can be installed from  <a href="http://www.steampowered.com/download/hldsupdatetool.exe" target="_blank">http://www.steampowered.com/download/hldsupdatetool.exe</a>
    - The server doesn't need the game installed. hldsupdatetool.exe will install everything needed.
3. Install hldsupdatetool.exe. I installed to C:\Users\Jeff\Applications\HLServer
4. Run hldsupdatetool.exe to install TF2 server in a <em>different</em>directory. `hldsupdatetool -command update -game tf -dir C:\Users\Jeff\Applications\TF2Server`
    
    This is about 5 GB in size so take a while

5. Create and edit `TF2Server\orangebox\tf\cfg\server.cfg`. See cfg file below
6. Run `TF2Server\orangebox\srcds.exe`: `srcds.exe -console -game tf -hostport 27015 +maxplayers 24 +map ctf_2fort`


Note 1: Initially I didn't have Steam client install and I get the message: <a href="http://www.facepunch.com/threads/961459">http://www.facepunch.com/threads/961459</a>. After installing Steam client, the problem is solved.

Config File server.cfg

```
// Team Fortress 2 Server Configuration File, To be used with TF2 only!


// Server Name
hostname "Team Fortress 2"

// Rcon Cvars
rcon_password "" //Set's remote control password
sv_rcon_banpenalty 15 //Number of minutes to ban users who fail rcon authentication
sv_rcon_log 1 //Enable/disable rcon logging.
sv_rcon_maxfailures 3 //Max number of times a user can fail rcon authentication before being banned
sv_rcon_minfailures 5 //Number of times a user can fail rcon authentication in sv_rcon_minfailuretime before being banned
sv_rcon_minfailuretime 10 //Number of seconds to track failed rcon authentications

// Server Password
sv_password "" // Password protects server

// Server Cvars
mp_allowspectators 1 //Toggles whether the server allows spectator mode or not
mp_autocrosshair 0
mp_autoteambalance 1 //Toggles server autoteambalance
mp_bonusroundtime 5 //Time in seconds after round win until round restarts
mp_chattime 5 //amount of time in seconds players can chat after the game is over

mp_decals 1
mp_defaultteam 1
mp_disable_autokick 1 //Prevents a userid from being auto-kicked
mp_enableroundwaittime 1 //Enable timers to wait between rounds.
mp_fadetoblack 0 //fade a player's screen to black when he dies
mp_falldamage 5 //Amount of damage players sustains from a fall
mp_flashlight 0 //Toggles flashlight on or off
mp_footsteps 1 //Toggles footsteps on or off
mp_forcecamera 0 //Restricts spectator modes for dead players
mp_forcerespawn 0
mp_forcerespawnplayers 1 //Force all players to respawn.
mp_forcewin 1 //Forces team to win
mp_fraglimit 0
mp_idledealmethod 2 //Deals with Idle Players. 1 = Sends them into Spectator mode then kicks them if they're still idle, 2 = Kicks them out of the game
mp_idlemaxtime 1 //Maximum time a player is allowed to be idle (in minutes)
mp_maxrounds 3 //max number of rounds to play before server changes maps
mp_teams_unbalance_limit 2 //Teams are unbalanced when one team has this many more players than the other team. (0 disables check)
mp_teststalemate 0 //Test the stalemate mode. Parameter: <0/1>. If 1, the map will reset at the end.
mp_time_between_capscoring 5 //Delay between scoring of owned capture points.
mp_timelimit 20 //game time per map in minutes
mp_winlimit 10 //Max number of rounds one team can win before server changes maps
sv_allow_color_correction 1 //Allow or disallow clients to use color correction on this server.
sv_allow_wait_command 0 //Allow or disallow the wait command on clients connected to this server.
sv_allowdownload 1 //Allow clients to download files
sv_allowupload 0 //Allow clients to upload customizations files
sv_alltalk 0 //Players can hear all other players, no team restrictions
sv_alternateticks 0 //If set, server only simulates entities on even numbered ticks.
sv_autosave 0 //Set to 1 to autosave game on level transition. Does not affect autosave triggers.
sv_bonus_challenge 0 //Set to values other than 0 to select a bonus map challenge type.
sv_cacheencodedents 1 //If set to 1, does an optimization to prevent extra SendTable_Encode calls.
sv_cheats 0 //Allow cheats on server
sv_clearhinthistory 0 //Clear memory of server side hints displayed to the player.
sv_consistency 1 //Whether the server enforces file consistency for critical files
sv_contact "" //Contact email for server sysop
sv_downloadurl "" //Location from which clients can download missing files
sv_enableoldqueries 1 //Enable support for old style (HL1) server queries
sv_pausable 0 //Is the server pausable.

// Lan or internet play, Server region cvars
sv_lan 0 //Server is a lan server ( no heartbeat, no authentication, no non-class C addresses )
sv_region 255 // Region Codes: 0 - US East coast, 1 - US West coast, 2 - South America, 2 - South America, 3 - Europe, 4 - Asia, 5 - Australia, 6 - Middle East, 7 - Africa, 255 - world

//server Logging
sv_log_onefile 0 //Log server information to only one file.
sv_logbans 1 //Log server bans in the server logs.
sv_logblocks 0 //If true when log when a query is blocked (can cause very large log files)
sv_logecho 0 //Echo log information to the console.
sv_logfile 1 //Log server information in the log file.
sv_logflush 0 //Flush the log file to disk on each write (slow).
sv_logsdir "logs" //Folder in the game directory where server logs will be stored.

//Server Rates
sv_maxcmdrate 0 //(If sv_mincmdrate is > 0), this sets the maximum value for cl_cmdrate.
sv_maxrate 20000 //Max bandwidth rate allowed on server, 0 == unlimited
sv_maxreplay 2 //Maximum replay time in seconds
sv_maxupdaterate 100 //Maximum updates per second that the server will allow
sv_mincmdrate 0 //This sets the minimum value for cl_cmdrate. 0 == unlimited.
sv_minrate 0 //Min bandwidth rate allowed on server, 0 == unlimited
sv_minupdaterate 30 //Minimum updates per second that the server will allow
```

References:<br />
<a href="http://forums.srcds.com/viewtopic/5439">http://forums.srcds.com/viewtopic/5439</a><br />
<a href="http://wiki.teamfortress.com/wiki/Dedicated_server_configuration">http://wiki.teamfortress.com/wiki/Dedicated_server_configuration</a>

