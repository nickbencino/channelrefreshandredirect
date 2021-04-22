# channelrefreshandredirect
Refresh a channels video page and redirect when a video is added (requires tampermonky)

# Instructions
1. Install TamperMonkey (available on most browsers)
2. Visit the video page of the channel you want to monitor. (https://www.youtube.com/channel/UC8wXpVINhSENNMCiXYMAROg/videos)
3. Click the TamperMonkey icon and select "create new script"
4. Select all the test and paste in the code below


            // ==UserScript==
            // @name         PabloRefresher
            // @namespace    http://tampermonkey.net/
            // @version      0.1
            // @description  Get in on Pablos Picks
            // @author       Nick Bencino
            // @match        https://www.youtube.com/channel/UC8wXpVINhSENNMCiXYMAROg/videos
            // @icon         https://www.google.com/s2/favicons?domain=youtube.com
            // @grant        none
            // ==/UserScript==

            (function() {
                'use strict';
                 const latestVid = document.querySelector('#details h3 a');
                 const latestStoredVid = localStorage.getItem('latest video');

                 if (latestVid.innerHTML === latestStoredVid) {
                   location.reload();
                 } else {
                   localStorage.setItem('latest video', latestVid.innerHTML);
                   window.location.href = latestVid.href;
                 }
            })();
