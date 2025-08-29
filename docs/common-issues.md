# Common Issues when setting up a Server

## Server install process taking unusually long

Sometimes, this process can "crash", and it will basically run infinitely, you can fix this yourself by [deleting your Server](delete-server.md) and recreating it again.
If it's a Premium Server and this issue occurs, make a ticket in the ticket area under https://billing.wispbyte.com, requesting a fix for this.

## Server not starting

Firstly, make sure you have installed all Packages that your Bot needs, more [here](installing-packages.md).

Secondly, make sure that the `App py file` (or `App js file`, or just `JS file`, depending on your [Server Egg](server-eggs.md) & Panel).
You can find this in the `Startup` Tab of your Server, which is usually located on a top or side panel.
There, simply enter the path to the file that starts your Bot.

## Bot not responding to Commands

This is likely a Rate Limit, more [here](rate-limit.md).
If it's not a Rate Limit, its a code issue.

## Web Server not showing on URL

Make sure you're binding on IP `0.0.0.0`, and port on the assigned port that your Server has.

## Can't type in Server Console

Typing in Console is disabled, except for Minecraft Servers.
