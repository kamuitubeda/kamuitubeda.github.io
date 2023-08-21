---
title: "3 Keys for Debugging Laravel on Linux Server"
date: 2023-08-21T12:24:56+07:00
description:
draft: false
authors: []
description: ""

tags: []
categories: []
series: []

hiddenFromHomePage: false
hiddenFromSearch: false

featuredImage: ""
featuredImagePreview: ""

toc:
  enable: true
math:
  enable: false
lightgallery: false
license: ""
---

Debugging errors in a Laravel application might seem tricky, especially when the errors don't show up on your website. But don't worry, there's a simple way to tackle this. Here's a step-by-step guide to help you debug your Laravel app, even if you're new to it.

Step 1: Turning on Debugging
-----------------------------
When something goes wrong in your Laravel app, the first thing you should do is turn on the debug mode. It's like flipping a switch that helps you see what's happening behind the scenes. Here's how you can do it:

Open a file named .env in your project folder and find the line that says APP_DEBUG=false. Change false to true like this:
```
APP_DEBUG=true
```
If you can't find it in .env, look for a file called app.php in a folder named config. Open that file and find the line 'debug' => env('APP_DEBUG', false),. Change false to true there.

Step 2: Checking Laravel Logs
-----------------------------
Sometimes, even with debug mode on, you might not see the exact error on your webpage. That's okay! Laravel keeps a log of what's happening in a file. Here's how to find it:

Go to the storage folder in your project directory and look for a folder named logs. Inside that, you'll find a file called laravel.log. Open it and look for error messages. They might look complicated, but they're like clues that tell you what's wrong.

Step 3: Looking at Web Server Logs
-----------------------------
If the error is still a mystery, there's one more place to check: your web server's error logs. Here's how you can find them:

-   If you're using Apache: Look for a file called error.log in a folder named apache2 under /var/log. The full path will be something like /var/log/apache2/error.log.
-   If you're using Nginx: Check for a file named error.log in a folder named nginx under /var/log. So, the complete path would be something like /var/log/nginx/error.log.

These logs might sound intimidating, but they're like a secret diary your server keeps. They can give you valuable information about what went wrong.

So, if you're ever stuck with errors in your Laravel app, just follow these three steps: turn on debugging, check Laravel logs, and explore web server logs. With a bit of patience and practice, you'll be a pro at finding and fixing errors in no time!