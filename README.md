How it works:
-----------------
This application uses [OpenCV](http://opencv.org/) to find the location of the user's face, then isolate the forehead region. Data is collected
from this location over time to estimate the user's heart rate. This is done by measuring average optical
intensity in the forehead location, in the subimage's green channel alone (a better color mixing ratio may exist, but the 
blue channel tends to be very noisy). Physiological data can be estimated this way thanks to the optical absorption 
characteristics of (oxy-) haemoglobin (see http://www.opticsinfobase.org/oe/abstract.cfm?uri=oe-16-26-21434). 

With good lighting and minimal noise due to motion, a stable heartbeat should be 
isolated in about 15 seconds. Other physiological waveforms (such as 
[Mayer waves](http://en.wikipedia.org/wiki/Mayer_waves)) should also be visible in the raw data stream.

Once the user's heart rate has been estimated, real-time phase variation associated with this 
frequency is also computed. This allows for the heartbeat to be exaggerated in the post-process frame rendering, 
causing the highlighted forehead location to pulse in sync with the user's own heartbeat.

Support for detection on multiple simultaneous individuals in a single camera's 
image stream is definitely possible, but at the moment only the information from one face 
is extracted for analysis.

The overall dataflow/execution order for the real-time signal processing looks like:


Requirements:
---------------

- [Python v2.7 or v3.5+)](http://python.org/)
- [OpenCV v2+](http://opencv.org/)
- Numpy, Scipy


