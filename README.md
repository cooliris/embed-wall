Cooliris Embed Wall
==========

# About

The Embed Wall was developed to enable web publishers to present photo and video content using the Cooliris Wall user interface, using a Flash-based widget. The widget fetches a collection from a supported source, and enables users to browse, view, and play slideshows of the photos and videos.

Originally, web publishers pointed at a centrally-hosted version of the Embed Wall SWF. While the product is no longer maintained, many web properties continue to depend on it, so we are making the SWF available for self-hosting to smooth the transition to a more modern web experience.

**On March 1, 2015 the centrally-hosted version of the Embed Wall will stop working. Please use the following information to self-host the Embed Wall before this time.**

### Warning

We recommend that you transition your experience to use modern web standards as soon as possible. If you continue to use the Embed Wall, please consider the following:

* The Embed Wall is no longer supported.
* The Embed Wall does not work on mobile browsers, as it was built on Adobe Flash.
* `api://` URLs may stop working at some point, since they depend on hardcoded API keys.
* `http(s)://` URLs referencing self-hosted Media RSS feeds are more reliable.

# Self-Hosting Guide

## Embed Codes

If you are currently using an embed code, you need to change the SWF URL to point at a self-hosted copy:

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

#### Hosted Walls

If you used Cooliris Express to generate an embed code, make sure that the `flashvars` in your embed code uses a `feed=…` parameter. If your embed code uses a `z=…` parameter, then you are using a centrally-hosted wall. Centrally-hosted walls will stop working on March 1, 2015. See the above warning about `api://` URLs.

## JavaScript

If your page uses JavaScript to add interactivity to the wall, you can continue to do so by self-hosting the JavaScript bridge in addition to the SWF.

1. Host [cooliris.swf](cooliris.swf) and [cooliris-embed.js](js/cooliris-embed.js) at URLs on your web server.
2. See [the JavaScript HTML example](js/example.html) for an example of how to initialize the JavaScript bridge with a self-hosted copy of the Embed Wall SWF and JavaScript files. The ordering is important:
  1. Include `cooliris-embed.js` to set up the `cooliris` global object.
  2. Set the `onEmbedInitialized()` callback to register for user interaction events.
  3. Insert the Embed Wall into the page. In the example, the `embedWall()` function uses the SWFObject library.
  4. Use the `cooliris.embed` API as before.

## Help

We hope that the above information gets you up and running independently. If you have questions or feedback, please direct them to <team@cooliris.com>. While the Embed Wall is no longer officially supported, we will do our best to answer your questions through the transition period, which ends on March 1, 2015.

