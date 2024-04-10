---
title: OBS Studio
layout: home
# has_children: true

typora-copy-images-to: ./images
typora-root-url: ./../
---
# {{ page.title }}

## OBS layout for talking head + slides videos

For perfect wallpaper blending, PowerPoint slide background should be a 1920x1080 render of the 1680x945 crop area of the canvas wallpaper.

![talking-head-with-slides-layout](/obs/images/talking-head-with-slides-layout.png)



## Preflight check for recording meetups

- [ ] Microphones: set gain on Anker receiver to +6
- [ ] Microphones: line of sight between mics and receiver - receiver can't be "backstage"
- [ ] Microphones: remember to press record on the receiver!

## Scale Factors for Video Frame Sizes

| Ratio | Fraction |3840px|2160px|1920px|1080px|1280px|1024px|720px|
|-|-|----|----|----|----|----|----|---|
|0.9|  9/10|3456|1944|1728|972|1152|921.6|648|
|0.875|  7/8 |3360|1890|1680|945|1120|896|630|
|0.85| 17/20|3264|1836|1632|918|1088|870.4|612|
|0.825| 33/40|3168|1782|1584|891|1056|844.8|594|
|0.8|  4/5 |3072|1728|1536|864|1024|819.2|576|
|0.775| 31/40|2976|1674|1488|837|992|793.6|558|
|0.75|  3/4 |2880|1620|1440|810|960|768|540|
|0.725| 29/40|2784|1566|1392|783|928|742.4|522|
|0.7|  7/10|2688|1512|1344|756|896|716.8|504|
|0.675| 27/40|2592|1458|1296|729|864|691.2|486|
|0.65| 13/20|2496|1404|1248|702|832|665.6|468|
|0.625|  5/8 |2400|1350|1200|675|800|640|450|
|0.6|  3/5 |2304|1296|1152|648|768|614.4|432|
|0.575| 23/40|2208|1242|1104|621|736|588.8|414|
|0.55| 11/20|2112|1188|1056|594|704|563.2|396|
|0.525| 21/40|2016|1134|1008|567|672|537.6|378|
|0.5|  1/2 |1920|1080|960|540|640|512|360|
|0.475| 19/40|1824|1026|912|513|608|486.4|342|
|0.45|  9/20|1728|972|864|486|576|460.8|324|
|0.425| 17/40|1632|918|816|459|544|435.2|306|
|0.4|  2/5 |1536|864|768|432|512|409.6|288|
|0.375|  3/8 |1440|810|720|405|480|384|270|
|0.35|  7/20|1344|756|672|378|448|358.4|252|
|0.325| 13/40|1248|702|624|351|416|332.8|234|
|0.3|  3/10|1152|648|576|324|384|307.2|216|
|0.275| 11/40|1056|594|528|297|352|281.6|198|
|0.25|  1/4 |960|540|480|270|320|256|180|
|0.225|  9/40|864|486|432|243|288|230.4|162|
|0.2|  1/5 |768|432|384|216|256|204.8|144|

Microphone settings for YouTube videos

Yeti stereo microphone over USB.



1. Adjust the physical mic: gain to 100%, pattern to cardiod:
   ![yeti-volume-settings-small](/obs/images/index/yeti-volume-settings-small-1712791911729-11.jpg)

2. Set recording level in Windows audio settings to 50%:

   ![image-20240411002851295](/obs/images/index/image-20240411002851295.png)

3. Adjust levels in OBS until shouting/clapping into the mic just clips the top of the red.

4. Add compression using default settings.

