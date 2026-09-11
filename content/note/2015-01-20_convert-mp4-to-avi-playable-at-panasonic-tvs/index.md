---
title: 'Convert MP4 to AVI, playable at Panasonic TVs'
author: "Jasdeep Singh"
date: Tue, 20 Jan 2015 08:19:01 +0000
slug: 'convert-mp4-to-avi-playable-at-panasonic-tvs'
draft: false
excerpt: "Gives an ffmpeg command for converting MP4 video files into AVI format playable on Panasonic TVs."
categories: ['ffmpeg', 'Programming', 'technology', 'tips']
---

> ffmpeg -i input.mp4 -s hd720 -vcodec mpeg4 -qscale 0 -ac 2 -acodec mp2 -ar 48000 -ab 192k -f avi -vtag XVID output.avi

_Crossposted from [https://jasdeepsingh.wordpress.com/2015/01/20/convert-mp4-to-avi-playable-at-panasonic-tvs/](https://jasdeepsingh.wordpress.com/2015/01/20/convert-mp4-to-avi-playable-at-panasonic-tvs/)_

---
### Comments:
#### [Abhirath Mahipal](https://csjourney.com/ "abhirath@csjourney.com") - <time datetime="2020-05-17 04:05:39">May 0, 2020</time>

Thanks for this. I could convert it to a format playable on TV but was taking a lot of time and the files were very large.
<hr />
