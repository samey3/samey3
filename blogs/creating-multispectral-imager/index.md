# Calibrating and operating a (not-yet multispectral) imager
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;As part of my work in developing a multispectral Integrated Vision System (IVS), I am first aiding in the development of a capability-demonstration product. This product will demonstrate the functionality of our future multispectral imager and serve as a test bed for future development. In particular, I'm working on the software development of this product using Allied Vision's Manta G-235 camera as my 'tool' of choice, as it will be later incorporated into the demo product along with another imager.

## The hardware
 To control the imaging cameras, I am using Seeed Studio's ODYSSEY board running Windows 10. This allows us to utilize Window's remote desktop feature to control the board over WiFi when out in the field.

![Odyssey](odyssey.png?raw=true "Odyssey")

The cameras themselves are from Allied Vision. The first is the previously mentioned Manta G-235 which is the main tool used in the development of the software. The Manta G-235 will be used primairily to image in the visible spectrum using a set of filters that will be placed in front of it via a rotating filter wheel. The second camera is Allied Vision's Goldeye short-wave infrared (SWIR) InGaAs camera which will also utilize it's own set of filters, however this one is currently in pieces so using it will have to wait.

![Manta G-235 camera](camera.jpg?raw=true "Manta G-235 camera")

In addition to the computer and cameras, Spectralon panels are also needed to calibrate the cameras. Spectralon panels are essentially flat panels with a known reflectivity, and are essential to being able to calibrate our cameras. I utilize a set of these panels when working with the cameras: 10%, 50%, and 99% reflectivity. Shown here is an image of the 50% reflectivity panel:

![50% Spectralon panel](panel.jpg?raw=true "50% Spectralon panel")

## Calibrating the camera

![Calibration program](temp_calibration_program.png?raw=true "Calibration program")

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;To obtain an optimal image, the camera must be calibrated for the lighting conditions that it is expected to be in when used in the field, and will not work well for any other conditions that it was not specifically calibrated for. The camera may be calibrated by tweaking the gain and exposure time values in such a way that the pixels located on the Spectralon panels reach a desired value. For example if using the 50% reflectivity panel, we may want the pixels on the Spectralon panel to be "50% of the way between black and white". E.g. if the max pixel value is 8-bits (2^8 = 256), we want to scale all of the pixels so that the average values of the ones on the panels are about 128. To do this, a process for finding the gain and exposure time can be found as follows:

![Calibration flowchart](flowchart.png?raw=true "Calibration flowchart")
 
The software I developed lets the user select the filter and camera, and calibrate it using the process seen in the flowchart above. While the filter wheel and filters are not ready to be used yet, the camera may be used as-is. Once calibrated (using the 50% panel with a 50% pixel goal value), the camera was able to produce the following image in the lab room with the lights on:

![Calibrated image](calibrated_image.png?raw=true "Calibrated image")
Calibrated for light, light

However after turning the lights off and capturing another image, the following image was produced:

Calibrated for light, dark

As mentioned earlier, a camera calibrated for one set of conditions will not work for another. But in order to deal with this, we can just recalibrate the camera for the new conditions and capture another image, and it should appear much better:

Calibrated for dark, dark

Similarly now that we calibrated for a dark room, if we switch the lights back on the images produced will be overexposed:

Calibrated for dark, light

Before going out in the field we will have calibrated and produced numerous settings that may be loaded for any particular filter, and this will allow us to deal with varying lighting conditions.


## The in-field software
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Now that the camera may be calibrated for a variety of conditions, all that remains is to actually use it for a purpose! The camera operation software I developed allows both of the cameras to switch between filters and the calibrated settings associated with them on demand to deal with the various lighting conditions we might encounter. By controlling it through remote desktop, the chosen camera will use the currently selected filter and calibration settings, capture images, and save these for for immediate or later analysis.

![Operation software](operation_software.png?raw=true "Operation software")
