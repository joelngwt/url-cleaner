# url-cleaner
Chrome extension to strip tracking parameters cleanly before requests hit the network

Currently only works for:
- YouTube
    - `si`
- Instagram
    - `igsh`

## How To Install
1. Download the `url-cleaner` folder.
2. Open the extensions page in your Chromium-based browser.
3. Turn on "Developer Mode". It should be a toggle at one of the corners of the page.
4. Press "Load Unpacked" and select the `url-cleaner` folder.

## How To Verify It Works
1. Open DevTools and Prepare the Network Tab
    1. Open a blank tab.
    2. Press F12 to open DevTools.
    3. Switch to the Network tab at the top of the DevTools panel.
    4. Check the Preserve log checkbox in the Network toolbar.

2. Force a Fresh Request
    1. Keep DevTools open. In that same tab's address bar, paste a dirty YouTube URL.
    2. Hit Enter.

3. Inspect the Network Logs
    1. Look at the very top of your Network list.
    2. The Interception: You will see a row for the original request (e.g. `watch?v=dQw4w9WgXcQ&si=TestTrackingID123`).
    3. Under the Status column, it will not say 200 OK. It will say 307 Internal Redirect.
    4. The Clean Request: Immediately below that row, you will see a second request for `watch?v=dQw4w9WgXcQ`. This second request will have a status of 200 OK, meaning YouTube's servers only ever received the cleaned URL.
