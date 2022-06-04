---
title: Tissue Branch Tracker
logo: /media/logos/btrack_logo.png
categories: [Tracking,Tissue,Skeletonization]
---

<img src="/media/icons/Btrack.png" width="250"/> 

BTrack is a Fiji plugin for tracking growing branches of tissue in 2 and 3D using generic skeletonization implementation of imglib2.

## Installation

1.  Click {% include bc path="Help | Update..." %}.
2.  Click the *Manage update sites* button.
3.  Select the *BTrack* update site in the list.
4.  Click *Close* and then click *Apply changes*.
5.  Restart Fiji.
6.  Launch the plugin with {% include bc path="Plugins | Tracking | BTrack" %}.

## Usage

### Tissue Detection

BTrack is a tool to analyse the growth of branched tissues. A time-lapse can be analysed with this plugin. The file format can be any format readable by Fiji/Bioformats (.tif, .nd2, ... ). To run the tracker select {% include bc path='Plugins|BTrack|Tissue Tracking'%}

A panel to input the Raw and Segmentation files will open. In addition, a csv file containing the information about the end point locations, could be imported instead of the Segmentation file by using the “Reload Saved Budpoints” option. 
{% include img src="/media/plugins/btrack/welcome.png" %}



#### Microscope Parameters
The Raw image metadata contains the information about the camera pixel size and the time calibration. If this information is not present in the metadata the users can modify the text field with the correct values. These values are used to output the final velocity calculation in these units.

#### Main Panel
After completing the selection of the Raw image, as well as the segmentation image (binary/integer labelled) or the optional csv file press the button supplied in the "Done Selection" panel area. At this stage the boundary points of the tissue are computed from the Segmentation image, if the csv file was also inputted the skeleton end points at their respective time frames will be displayed together with the Raw image. A second panel containing computational and interactivity option will open.
{% include img src="/media/plugins/btrack/main.png" %}


#### Interactivity Options


**Dynamic slider display**

At this step the user can only see the view of the input timelapse at the specific timepoint indicated by the slider embedded into the panel. Moving the slider will interactively update the image along with the overlay of the chosen timepoint.


**Deselect and select end points**
First, press the button “Skeletonize buddies” to start with the analysis. The program will use the binary /integer labelled image to obtain the skeleton end points. The progrees in the computation analysis is shown by hte progress bar, which is updated along with the time text field next to the time slider. During this calculation step all the unnecessary options in the plugin will be frozen. At this stage the user can only set the directory path to save the results. This calculation step is skipped if a csv file is provided before the skeletonization operation.


After th computation is done the found skeleton end points are displayed in pink. The users can add new points by clicking "a" on the keyboard and a new point will be created at the clicked location. By clicking "Shift + a", it will deselct the closest point to the click and the color will change from pink to red. The final pink-coloured dots can be saved in a csv file by pressing “Checkpoint Save”. This csv file can be uploaded in the next session using the previously mentioned “Reload Saved Budpoints” option. 
#### Tracking Options

**Interactive track selection**

After the skeletonization operation is complete the users can use the Kalman Filter selection panel to perform the tracking of growing branch tips. These parameters include the search radius and the number of timepoints that a gap can have between two tracks that will be linked. 
After selection of the parameters, the table shows the found tracks. Selecting a track from the table, a timelapse image with just the selected track will open a yellow circle will appear in the clicked pink dot in the main image. Alternatively doing a "Shift+Left" click near a pink dot also opens the timelapse image displaying the track of that branch end. The table is highlighted with color green when the mouse position in the image corresponds to the closest track in the table.

#### Save Options

The users can either save one track at a time or can choose to save all the tracks at once. The saved information includes text files containing velocities for each track, and an image that contains the dot locations in ech timepoint for all the tracks. This final image is used in the later analysis to localize the final end of a branch in a growing tissue.

## Citation

Please note that BTrack is available through Fiji, and is based on a publication. If you use it successfully for your research please be so kind to cite our work:

## Authors

Lead programmer, Mantainer: [Varun Kapoor](/_pages/people/kapoorlab.md)
Contributor, Debugger: [Claudia Carabana](/_pages/people/claudiacarabana.md)

## References

[^1]: J. Munkres, "Algorithms for the Assignment and Transportation Problems", Journal of the Society for Industrial and Applied Mathematics, 5(1):32–38, 1957 March
