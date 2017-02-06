---
author: "Marcin Biegała"
categories:
  - Code
date: "2017-02-06T03:35:31+02:00"
description: ""
title: "HSTS - Where are 2 hours of my life?"
type: "post"
---
I was moving few of the sites I manage to HTTPS lately. I've messed up on one of the sites and I had to revert back to plain HTTP.  
Ok, so I revert hosting configuration, enter url into Chrome address bar and.... Chrome shows errors and I see my site address over https. 
Refresh, same thing.  
Hard refresh, still same.  
Remove "s" from "https" in the address bar, still same situation.  
"Aha! I have to have htaccess redirect on server" - no.  
That made me scratch my head.  
Coffee, few google searches and I've found culprit.  
Let us welcome [HSTS](https://en.wikipedia.org/wiki/HTTP_Strict_Transport_Security).  

HSTS is a new security policy that let's website creators force client browser to load given page only over secure connection. If SSL certificate is not available or is not valid, it will show error and won't load a page at all.  
We turn on HSTS, by sending the `Strict-Transport-Security` header with response from the server (and my server obviously did that).  
So first time I've loaded my page over https while setting things up in the first place, Chrome got this new header and remembered that this particular page should be only accessed over HTTPS. That way, even when I've disabled certificate, Chrome was redirecting me to secure connection.  

So how to fix that?  
Enter `chrome://net-internals` in your Chrome address bar, on the menu on the left select `HSTS` and somewhere in the middle of this page you should see `Delete domain` section. Just put your domain name in the input box, and you're good to go!  

Hope you'll find it usefull and loose a bit more time (and hair) that I did :)
