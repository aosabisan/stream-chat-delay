KICK DELAYED CHAT
=================

An on-stream chat box for Kick that holds every message for a few seconds
before showing it. If AutoMod or a moderator deletes the message during that
wait, or the sender is banned or timed out, it never shows up on your stream.

If you use Streamer.bot, your Twitch and YouTube chat can show in the same
box. Those show right away, since Twitch and YouTube already hold back
flagged messages before anyone sees them. Messages can also fade
away after a set time.

Normally, Kick chat overlays show a message the instant it's sent, so
anything AutoMod removes a moment later has already been seen on stream.
This fixes that.


INSTALL (about 2 minutes)
-------------------------

1. Unzip this folder and put it somewhere it can stay, like your Documents
   folder. (Don't run it from inside the zip file.)

2. Double-click SETUP.html. It opens in your web browser.

3. Follow the steps on that page:
     - Type your Kick channel name and click "Find my chatroom".
       (No Kick? Tick "I don't stream on Kick".)
     - Optional: turn on Twitch & YouTube through Streamer.bot.
     - Pick your delay, how long messages stay, and other settings.
     - Click "Copy link", then add a Browser source in OBS and paste the
       link into the URL box (with "Local file" unticked).

That's it. Type something in your chat to check it works.


TWITCH & YOUTUBE (OPTIONAL)
---------------------------

This part needs Streamer.bot, already connected to your Twitch and/or
YouTube account.

1. In Streamer.bot, open Servers/Clients -> WebSocket Server.
2. Tick "Auto Start", then click "Start Server".
   Leave Address 127.0.0.1, Port 8080 and Endpoint / as they are.
3. Keep Streamer.bot open while you stream.

Kick chat always comes straight from Kick, not through Streamer.bot,
because only Kick's own connection reports when AutoMod deletes a message.
So you won't see Kick messages twice.


GOOD TO KNOW
------------

- Don't move or rename the folder after setup. If you do, open SETUP.html
  again and copy the new link into OBS.

- Delay: 3 seconds catches nearly all AutoMod deletions. When Kick's servers
  are slow, AutoMod can take longer, so pick a longer delay if you want to
  be extra safe. The trade-off is that on-screen chat runs further behind.

- Want to see it without going live? Add &test=1 to the end of the link in
  OBS. Fake messages appear, and every 4th one (a Kick message) gets "deleted" and should
  never show.

- The coloured dot before each name shows where it came from: green is
  Kick, purple is Twitch, red is YouTube.

- Changing the look: open kick-delayed-chat.html in Notepad. The colours,
  font and size are near the top, under "Look of the chat". Save, then in
  OBS open the source's properties and click "Refresh cache of current page".


TROUBLESHOOTING
---------------

Red box saying "Chat disconnected — reconnecting..."
  Kick sometimes changes the key its chat uses. The overlay tries to find
  the new key by itself. If the box stays, find the new key and add it to
  the end of your OBS link:
      &key=NEWKEY

Red box saying "Couldn't find the chatroom"
  The link is missing your chatroom number. Open SETUP.html again and copy
  a fresh link.

Twitch or YouTube messages don't show up
  Check that Streamer.bot is open, its WebSocket Server is started, and
  it's connected to your Twitch/YouTube account. To see what's wrong, add
  &debug=1 to the end of your OBS link. If you turned on a password in
  Streamer.bot's WebSocket settings, open SETUP.html again and enter it.

Nothing shows up, and there's no red box
  Make sure "Local file" is unticked in the OBS source, and that the
  delay has passed after a message is sent.


NOTE
----

This uses the same live chat connection Kick's own website uses. It isn't
an official Kick feature, so a future Kick update could affect it.
