---
title: Wordpress Authentication
sidebar: cyclr_sidebar
permalink: wordpress-connector.html
tags: [connector]
---

# Wordpress #

Wordpress Connector Setup
-------------

<h2 id="authentication" class="intercom-align-left">Authentication</h2><p class="intercom-align-left">In order to allow Cyclr to connect to your WordPress site’s API, you must install the&nbsp;<a href="https://wordpress.org/plugins/rest-api-oauth1/" target="_blank" rel="nofollow noopener noreferrer">WordPress REST API – OAuth 1.0a Server</a>. This gives your site the ability to securely authenticate API use.</p><h3 class="intercom-align-left">Register Cyclr as an application</h3><p class="intercom-align-left">Once you have installed the plugin, open WordPress and go to:</p><p class="intercom-align-left">Users &gt; Applications &gt; Add New</p><p class="intercom-align-left">The values needed to add your app are:</p><ul><li>Name: Cyclr</li><li>Description: this is a free text area</li><li>Callback:&nbsp;<a href="https://my.cyclr.com/connector/callback" target="_blank" rel="nofollow noopener noreferrer">https://my.cyclr.com/connector/callback</a></li></ul><p class="intercom-align-left">Your setup should look something like this:</p><div class="intercom-container intercom-align-left"><img src="https://downloads.intercomcdn.com/i/o/31974713/d488ee6aae31f45cffce57ad/wordpress-cyclr-api-authentication.png"></div><p class="intercom-align-left">When you add your Consumer, you will be presented with your Client Key and Client Secret.</p><div class="intercom-container intercom-align-left"><img src="https://downloads.intercomcdn.com/i/o/31974914/05ce67e3bbc4a345ab5fbe0c/wordpress-oauth-credentials.png"></div><p class="intercom-align-left">(Yours will be different to the screenshot).</p><h3 class="intercom-align-left">Authenticate WordPress in Cyclr</h3><p class="intercom-align-left">With the above correctly setup, install the WordPress connector in Cyclr and provide the Client Key and Client Secret along with your website’s URL.</p><div class="intercom-container intercom-align-left"><img src="https://downloads.intercomcdn.com/i/o/31975330/cabaf455edcdca9ab134b2c8/wordpress-auth.png"></div><p class="intercom-align-left">Click the Next button and you will be prompted to sign into WordPress. Do this and then authorize Cyclr and you can now begin to use your WordPress site’s API.</p>