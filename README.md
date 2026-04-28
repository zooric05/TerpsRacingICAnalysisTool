# TerpsRacingICAnalysisTool
This is a lightweight, browser-based telemetry dashboard I put together for motorsports. Basically, it lets you take the raw data from Race capture like  speed, throttle, brake pressure, and GPS coordinates and turns it into interactive track maps and charts so you can see exactly where you're losing or gaining time.

### What it does
You can download the file, save it as .HTML and run it or visit this webpage and run it: 
https://tr-data-analysis-tool.netlify.app/

Compare Multiple Logs: You can load up to two different RC files (that have been converted from .log to .csv) at the same time. You just pick a primary lap and a compare lap, and it overlays their data right on top of each other.
Interactive Track Map: It automatically draws the track layout using your raw GPS coordinates. It color-codes the racing line based on what you're looking at. For example, it can color the track red in heavy braking zones or green where you are flat out.
Manual Lap Slicer: You can use the slicer at the top to drag the start and end sliders (using the arrow buttons for fine-tuning) to highlight a specific part of the track, name it, and save it as a custom lap.
Detailed Charts: It generates line graphs for your speed, throttle position, front and rear brake pressures, gear, RPM, and you can swap in other custom channels to trace.
Automatic Coaching Stats: It does some of the math for you, showing things like how much of the lap you spent at wide-open throttle or coasting, your peak G-forces, and how many distinct braking zones it detected.

### How it works under the hood
This is essentially a single-file web app built with standard HTML, CSS, and vanilla JavaScript. 
First, it uses a library called SheetJS to parse your uploaded CSV or Excel files and turn that raw spreadsheet data into something the code can read. 
Then, it uses Chart.js to actually draw and handle all the line graphs on the right side of the screen.
Finally, for the map, it just uses the standard HTML5 Canvas API. It does the math to figure out the boundaries of your GPS coordinates and draws the track layout and the slice preview colors dynamically, completely from scratch without needing external mapping libraries like Google Maps.

### Data Format Requirements
Make sure your files have standard telemetry headers. Right now, the tool looks for specific column numbers to find things like Latitude, Longitude, Time, Speed, and TPS. If you have added/removed any sensors from RC you will need to change the code. Go to line 325 and add the approprite col# to the respective data it asks for. save and push and all will be well. 

Thank you for your attention to this matter
