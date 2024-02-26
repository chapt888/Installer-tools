# Installer Tools

I made these simple tools to help with our installs as most of the installs in our current are have bad service across the main 3 carriers.

This process is heavy, time consuming, and at times impossible to accomplish when need when heading to or on jobs.
1. Load up Vision main page which sometimes results in a login page loop that requires Force closing browser to resolve
2. Load up Calendar
3. Load up Schedule Spot

This is not too bad at most times, however if we want to see where that HH is, fiber assigned to customer, or the rough distance of cable we need. We must now:
4. Load workflow
5. Load the Map view in the workflow

Step 5 is what takes the longest especially with poor service.

The following two tools were what we used to speed up and try to make our installs run smoother

## Webpages
---
I created this set of webpages to be able to quickly access the needed information for an install.

The following information is included on each install page:
- Name
- Address
- Phone Number
- Fiber Color
- Footage
- Screenshot of Map View from workflow
- Link to Vision account
- Link to Vision Install

The index page is just a simple calendar of the installs for the week. When you click on an install just brings up the page for that install. I created this in a few mins on the weekend and would spend time on the weekend populating the pages for the installs for the week. However due to the amount of time this ended up taking, even though speeding up installs, I was at a net loss for time and effort and stopped using it.

## IOS Shortcut
---
I created this to replace the Webpages. Its a simple ios shortcut that figures out the current time and day, reads a json and finds the appropriate link to workflow for the current install. When I tap an nfc tag in the install vehicle it brings up the workflow that we are currently working on to cut out the extra loading and navigating. The json is just a plaintext file i host on my webserver.

Images show the actual Shortcut however this is the process just to explain what I was doing with it.

- Get Morning or Afternoon
    - Get Current hour with `H` from UTS #35
    - Using if statement convert to 1 (Morning) or 2 (Afternoon)
- Get Current Day
    - Get Current Day of the week with `c` from UTS #35
- Combine variables to get install slot variable
    - `Day|Hour`
    - ex: Monday Afternoon Slot is `22`
- Pull json from `workflow.chapman.network/json.txt`
- Convert json to Dictionary
- Using key get value which is the link for that install
- Go to link

When installs for the week are scheduled I copy and paste the workflow link into the json file. From here we can at least quickly get the address or enter and ont without going through the process to get there. These processes dont take long in a office or lab setting but in the field with bad signal makes a big enough difference to go through the effort and time to make these tools.

## Request
---
We are just looking for a simple, light weight, and easy to work with installer page or app. Other platforms provide this decently such as what we use on the wireless side.

- Lightweight
- Easy to load when we have bad internet connection
- Details needed for install are displayed simply and easy to read

Possibly something like a static page that populates the information for the install and does a final query at the beginning of the install window since details rarely change by that point. That way we can load a page that has minimal queries, js, or elements that are required to load to view the information. Possibly all the information I listed above on a single page without dropdowns, modals, or popups. Doesnt need to look amazing just need something simple that works. Mobile friendly is extremely important as we do almost all our interfacing with vision on our phones or cellular iPad.

An IOS app would be nice that one data populates for an install, that data is held by the client so we have something to work with if we have no service. The only thing we actively would need net for is entering ont and assigning an IP which can be done ahead of time if we know service is not available at said location.