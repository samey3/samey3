# Calibrating and operating a (not-yet multispectral) imager

As part of my work in developing a multispectral Integrated Vision System (IVS), I am first aiding in the development of a capability-demonstration product. This product will demonstrate the functionality of our future multispectral imager and serve as a test bed for future development. In particular, I'm working on the software development of this product using Allied Vision's Manta G-235 camera as my 'tool' of choice, as it will be later incorporated into the demo product along with another imager.

## The hardware
To control the imaging cameras, I am using Seeed Studio's ODYSSEY board running Windows 10. This allows us to utilize Window's remote desktop feature to control the board over WiFi when out in the field.

![Odyssey](odyssey.png?raw=true "Odyssey")

The cameras themselves are from Allied Vision. The first is the previously mentioned Manta G-235 which is the main tool used in the development of the software. The Manta G-235 will be used primairily to image in the visible spectrum using a set of filters that will be placed in front of it via a rotating filter wheel. The second camera is Allied Vision's Goldeye short-wave infrared (SWIR) InGaAs camera which will also utilize it's own set of filters, however this one is currently in pieces so using it will have to wait.

![Manta G-235 camera](camera.jpg?raw=true "Manta G-235 camera")

In addition to the computer and cameras, Spectralon panels are also needed to calibrate the cameras. Spectralon panels are essentially flat panels with a known reflectivity, and are essential to being able to calibrate our cameras. I utilize a set of these panels when working with the cameras: 10%, 50%, and 99% reflectivity. Shown here is an image of the 50% reflectivity panel:

![50% Spectralon panel](panel.jpg?raw=true "50% Spectralon panel")

## Calibrating the camera
To obtain an optimal image, the camera must be calibrated for the lighting conditions that it is expected to be in when used in the field, and will not work well for any other conditions that it was not specifically calibrated for. The camera may be calibrated by tweaking the gain and exposure time values in such a way that the pixels located on the Spectralon panels reach a desired value. For example if using the 50% reflectivity panel, we may want the pixels on the Spectralon panel to be "50% of the way between black and white". E.g. if the max pixel value is 8-bits (2^8 = 256), we want to scale al of the pixels so that the average values of the ones on the panels are about 128. To do this, a process for finding the gain and exposure time can be found as follows:
 
Calibrated for light, light
Calibrated for light, dark
Calibrated for dark, dark




![Calibrated image](calibrated_image.png?raw=true "Calibrated image")

Then, mention how it calibrates, show the flowchart. Mention how we need sliders to initially get a viewfinder image, position the spectralon, select filter (which will move wheel), then calibrate. A post-calibration image can then be taken (show one?)

Mention that once this is done for all the filters, you would then run the operation software for the in-flight stuff. If you're calibration was correct and you're not operating in too-different conditions, your images comeout good. Show example for calibrating in the dark, and then lights come on (overexposed image).

Image of camera, spectralon panel, calibration software, operation software,
flowchart, tiff images (uncalibrated, calibrated)
