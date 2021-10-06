---
author: Jasdeep Singh
categories:
- Software
date: "2021-02-02"
draft: false
excerpt: Code for scrapping Punjabi Tribune website 
featured: true
layout: single
links:
- icon: github
  icon_pack: fas
  name: Code  
  url: https://github.com/jasdeep/farmers-movement-archive-scraper
subtitle: ""
tags:
- github
title: Punjabi Tribune Scraper
---

# Daily News Roundup Generator and Translator
These are the scripts used to aggregate news reports from Punjabi Tribune website daily. Which are then translated into English and Hindi.

## Punjabi Tribune Scraper
Every morning the Punjabi Tribune Archive web page is scraped for news articles of farmers and labourers. These articles are then parsed for details. An xml with newsitems and their details is generated.

The xml is parsed to generate an HTML page with the content of all news items and a text file with all headlines.

## Alternative
Try to iterate the rss feeds of the day and get data by date. That way more data is available.

## Daily Roundup Translator
The text file with data from Punjabi Tribune and SKM Press Release is edited manually and text files with google translations into English, Hindi, and Urdu are generated. Which are then edited and sent to create posts.
