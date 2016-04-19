Cooliris Embed Wall
==========

Hello

The Embed Wall is no longer supported, and the centrally-hosted copy is no longer available. Since some web properties still use it, we are making the SWF available for self-hosting to smooth the transition to alternative solutions.
![Embed Wall](images/screenshot.jpg)
The Embed Wall was developed to enable web publishers to present photo and video content using the Cooliris Wall user interface. The Embed Wall fetches photos and videos from a supported source, and enables users to browse, view, and play slideshows.
### Caution

We recommend that you transition to a modern solution based on web standards. If you continue to use the Embed Wall, please consider the following:

* The Embed Wall is implemented using the Adobe Flash plugin, and therefore does not work on mobile browsers or desktop browsers without the Flash plugin.
* We cannot guarantee that the Embed Wall will continue to work properly, due to its integration with third-party services that may change. In particular, `api://` URLs for Facebook, Flickr, Picasa, and YouTube depend on hardcoded API keys, and will stop working at some point.
* `http(s)://` URLs referencing Media RSS feeds are relatively reliable, since they do not depend on API keys.

# Self-Hosting Guide

## Embed Code

If you are using an embed code, change the SWF URL to point at a self-hosted copy:

1. Host [cooliris.swf](cooliris.swf) at a URL on your web server.
2. Replace the `http://apps.cooliris.com/embed/cooliris.swf` link in the embed code with your URL.
3. In your embed code, change `allowScriptAccess` to `never`:
```html
<object id="…" classid="…" width="…" height="…">
  <param name="movie" value="http://{YOUR URL}/cooliris.swf"/>
  <param name="allowFullScreen" value="true"/>
  <param name="allowScriptAccess" value="never"/>
  <param name="bgColor" value="…"/>
  <param name="flashvars" value="feed=…"/>
  <param name="wmode" value="opaque"/>
  <embed type="application/x-shockwave-flash"
    src="http://{YOUR URL}/cooliris.swf"
    width="…"
    height="…"
    allowfullscreen="true"
    allowscriptaccess="never"
    bgcolor="…"
    flashvars="feed=…"
    wmode="opaque">
  </embed> 
</object> 
```

#### Centrally-Hosted Walls

If you used the Cooliris Express tool to generate an embed code, make sure that the `flashvars` in your embed code uses a `feed=…` parameter. If your embed code uses a `z=…` parameter, then you were using a centrally-hosted wall. If you were using a Media RSS feed, you can change your embed code to point directly at it (e.g. `flashvars="feed=http://your/media.rss"`).

## JavaScript

If your page uses the JavaScript API for deeper integration with the Embed Wall, you can continue to do so by self-hosting the JavaScript bridge alongside the SWF.

1. Host [cooliris.swf](cooliris.swf) and [cooliris-embed.js](js/cooliris-embed.js) at URLs on your web server.
2. See [the JavaScript HTML example](js/example.html) for an example of how to initialize the JavaScript bridge with self-hosted SWF and JS files. The include order is important:
  1. Include `cooliris-embed.js` to set up the `cooliris` global object.
  2. Set the `onEmbedInitialized()` callback to register for user interaction events.
  3. Insert the Embed Wall into the page.

The `cooliris.embed` API should continue to work as before.
