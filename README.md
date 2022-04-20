# Advanced Lane Detection

## How To Run
1. Using the included Shell Script.

`./lane.bash [-d] /path/to/input-video.mp4 /path/to/output-video.mp4`


2. Using Jupyter Notebook included in the project files.
## Detection Pipeline
    1. Get edges positions and directions using Sobel
    2. Applying perspective warping
    3. Detect using sliding windows
    4. Draw lanes
#### Sobel Edge Detection:
    1. Transfer frame from RGB to Gray 
    2. Apply soble magnitude detection on X-axis then use only edges above a certain threshold
    3. Apply soble direction detection for X and Y gradients 
    4. Combine magnitude and direction output
    5. Transfer frame from RGB to HLS
    6. Remove points outside of a certain threshold
    7. Combine points from sobel and HLS 
    8. Setting an area of interest 

#### Perspective warping:
    1. Mapping warping point to source and destination images
    2. Get the perspective transform matrix
    3. Apply warping

#### Sliding windows
    1. Getting image histogram
    2. Get the peaks of leftmost and rightmost quarter of the histogram
    3. Set windows parameters
    4. Looping over windows 
        a. Identify window boundaries in x and y (and right and left)
        b. Identify the nonzero pixels in x and y within the window
        c. Check the number if indices is within a certain threshold, if so fit a second order polynomial
        d. If not use the previous coefficients 
    5. Generate x and y values for plotting


#### Draw lanes 
    1. Create an all zeros image 
    2. Draw lanes in it using fillPoly and polylines
    3. Merge Input RGB image with the result


