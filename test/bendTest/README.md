# Bend Test
This directory contains info about the bend test done on 2018-12-17.

## The Data
The original video and instrumentation data can be found at [this Google Drive link](https://drive.google.com/drive/folders/1316Z5aGJLGGdGO3YifeCQpyrdhxJAECB).

`Gen2Module StressTest1.txt` contains CSV data of the instrumentaiton.
The columns are a little confusingly labelled. 
They *do not* express raw voltages!
- The first column, named "Row", simply contains the row number.
- The second column, named "Time", contains the time (%H:%M:%S %Z).
- The thrid column, named "Voltage_0(Voltage)", contains the center load in kN.
- The fourth column, named "Voltage_1(Voltage)", contains the strain in the "red"/"right" strain gauge 
  and is correctly scaled but not correctly zeroed.
- The fifth column, named "Voltage_2(Voltage)", contains the displacement of the laser extensometer markers.
  Note that the extensometer strayed away from these markers during the test, which is why there are so many jumps in the data.
- The sixth column, named "Voltage_3(Voltage)", contains the strain in the "blue"/"left" strain gauge 
  and is correctly scaled but not correctly zeroed.

## Supplemental Reading
These documents provide some relevant information.

[__Rocket airframe concepts__ by Rick Newlands](http://www.aspirespace.org.uk/downloads/Rocket%20airframe%20concepts.pdf)
covers some introductory intuition-level stuff regarding structures.

[__Aircraft Structures for Engineering Students__ by T.H.G. Megson](https://books.google.com/books/about/Aircraft_Structures_for_Engineering_Stud.html?id=z39Y6CGu7OsC)
is a general textbook on aircraft enginering, which *may* fill in the theory details that Flannigan glosses over.

### Chris Flannigan
Flannigan's work very convincingly *asserts that* his software for modal analysis works, 
but he's a little opaque on the theory and doesn't readily provide the source or even a binary.
- [__Aeroelastic Analysis of Super-Roc Vehicles__ by Chris Flanigan](https://sites.google.com/site/chrisflaniganrocketry/Home/research-and-development/Super-Roc_Simulation.pdf?attredirects=0)
- [__AVOIDING THE BENDS! Why Super-Roc Models Buckle and How to Design for a Successful Flight__ by Chris Flanigan (NAR 17540L1)](https://www.nar.org/wp-content/uploads/2014/08/Avoiding_the_Bends.pdf)
- [__Improved Designs for the D Super-Roc Altitude Contest__ by Chris Flanigan](https://www.apogeerockets.com/education/downloads/Newsletter353.pdf)

[Flannigan's website](https://sites.google.com/site/chrisflaniganrocketry/Home/research-and-development)
also has lots of related information.

## Point Tracking
Joe and Georges used different approaches for point tracking. 
Joe used ImageJ, while Georges used [Tracker](https://physlets.org/tracker/).
[__Manual Tracking__ by Fabrice P. Cordelières](https://imagej.nih.gov/ij/plugins/track/Manual%20Tracking%20plugin.pdf)
serves as a handbook for how to do manual point tracking with ImageJ.

The following `ffmpeg` command can be used to reformat the original videos into a format that ImageJ likes:

```
ffmpeg -i input.mp4 -an -r 1 -pix_fmt nv12 -f avi -vcodec rawvideo output.avi
```
