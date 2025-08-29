# Rate Limits

https://discord.com/developers/docs/topics/rate-limits

## What is a Rate Limit?
A rate limit in the context of discord (or in general, any website), is when the website blocks you (IP) temporarily from accessing their endpoints.
Rate limits are enforced to prevent abuse such as spam or DOS attacks.

## Causes for a Rate Limit
Spamming the API at huge quantities.

For example, if you send 500 requests per second to any of Discord's Endpoints, you will occasionally get smaller ratelimits, like 3 seconds, 5 seconds, around that, but after some time, you will get fully ratelimited, meaning you are ratelimited on all API Endpoints, these ratelimits usually last one or a few hours.

> [From https://discord.com/developers/docs/topics/rate-limits]
> "All bots can make up to 50 requests per second to our API. If no authorization header is provided, then the limit is applied to the IP address. This is independent of any individual rate limit on a route. If your bot gets big enough, based on its functionality, it may be impossible to stay below 50 requests per second during normal operations."

This applies for requests made with both Bot tokens and User tokens as authorization, although requests made with User tokens are considered selfbotting.

## Cloudflare Rate Limit

These Rate Limits are triggered when your Bot makes to many invalid HTTP requests (401, 403, or 429), the current limit for this is 10,000 per 10 minutes, so around 16-17 per second.

> [From https://discord.com/developers/docs/topics/rate-limits]
> "If your bot gets temporarily Cloudflare banned from the Discord API every once in a while, it is most likely not a global rate limit issue. You probably had a spike of errors that was not properly handled and hit our error threshold."

## How do I know if i'm ratelimited?

Most Discord Libraries show a distinct message in the console in case of a ratelimit;

For Python (discord.py), this would look something like:
`discord.errors.HTTPException: 429 Too Many Requests (error code: 0): You are being rate limited.`
Or anything that includes `429`, as this is the HTTP error code for "Too Many Requests"

For Node.js (discord.js), the library doesn't show ratelimit messages like discord.py does.
But there is some other factors on which you can (likely) identify a ratelimit, such as;

Your Bot's `client.on("ready",)` event not firing.
Bot not responding to Commands or to other Events that it should respond to.

## But I didn't do anything?
No worries, if your Bot on your Server gets ratelimited, it is most likely due to someone else on the same Node, that is hosting some sort of Nuke / Spam Bot.
Since the Node has one primary IP, this IP is shared across all Servers on that Node, this is also why ports are needed, every port is a different Server.

## What can I do about it?
Generally, nothing.
If you think that you were the one that caused the ratelimit, try to identify the cause in your code and optimize it so it doesn't spam Discord.

## When will it be over?
Global ratelimits usually last 1 to 3 hours, rarely it might be longer.
If it takes over / close to a day, Wispbyte usually does something to mitigate it, such as changing the Node's IP, but this is not guaranteed.
