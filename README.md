chatlogger plugin for Big Brother Bot (www.bigbrotherbot.net)
=============================================================

By Courgette


Description
-----------

This plugin logs to database and/or file all clients' messages (chat, team chat, private chat).
Forum : http://www.bigbrotherbot.com/forums/index.php?topic=423


Installation
------------

 * copy chatlogger.py into `b3/extplugins`
 * copy plugin_chatlogger.ini into into your config directory
 * create the chatlog table in your database importing the `chatlogger.sql` file.
 * update your main b3 config file with :
```
<plugin name="chatlogger" config="@conf/plugin_chatlogger.xml"/>
```

NOTE : if you are using the censor plugin, make sure the chatlogger plugin is loaded before the censor plugin or you
won't log any messages containing censored words.


Changelog
---------

28/07/2008 - 0.0.1
 - manage say, teamsay and privatesay messages
 
14/08/2008 - 0.1.0
 - fix security issue with player names or messages containing double quote or antislash characters (Thx to Anubis for report and tests)
 - option to setup a daily purge of old messages to keep your database size reasonable
 
13/09/2008 - 0.1.1
 - in config, the hour defined for the purge is now understood in the timezone defined in the main B3 config file (before, was understood as UTC time)
 - fix mistake in log text

7/11/2008 - 0.1.2 - xlr8or
 - added missing 'import b3.timezones'

22/12/2008 - 0.2.0 - Courgette
 - allow to use a customized table name for storing the
   log to database. Usefull if multiple instances of the
   bot share the same database.
   Thanks to Eire.32 for bringing up the idea and testing.
   
11/04/2011 - 0.2.1 - Courgette
 - update the sql script to use the utf8 charset

16/04/2011 - 1.0.0 - Courgette
 - can log to a file instead of logging to db (or both)
 - requires B3 1.6+ 

01/09/2011 - 1.1.0 - BlackMamba
 - log commands to db

01/09/2011 - 1.1.1 - Courgette
 - refactoring to reduce code duplication
 - better test coverage
 - update authors credit

12/09/2011 - 1.1.2 - Courgette
 - start without failure even if the plugin is loaded before the admin plugin
 - do not fail to handle SQLite database errors

20/12/2011 - 1.1.3 - Courgette
 - fixes #2 : Error DELETE FROM cmdlog WHERE msg_time (thanks to Mariodu62)

03/03/2012 - 1.2 - OliverWieland
 - add new setting max_age_cmd

09/08/2012 - 1.3 - Courgette
 - now also log events EVT_CLIENT_RADIO, EVT_CLIENT_CALLVOTE and EVT_CLIENT_VOTE when available

12/08/2012 - 1.3.1 - Courgette
 - gracefully fallback on default values when part of the config is missing

18/08/2013 - 1.3.2 - Courgette
 - plugin config file is now a .ini file