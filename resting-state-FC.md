# Hands-on Practical for Resting-state Functional Connectivity

For this hands on lab practice, we will be using data from sub-001 that you downloaded and processed for the previous block. 

They should be located at `~/fmriLab/flankerData_n4/`, and you should be able to navigate to it by doing `cd ~/fmriLab/flankerData_n4`.   

You should also have the "skull-striped T1 image" saved under `~/fmriLab/flankerData_n4/sub-001/anat/` 


## What you will learn from this lab practice
- How to replicate this famous finding from Biswal 1995 
<img width="293" alt="practical-rsfc_biswal-map" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/edb6edaf-b0dd-4c3a-a3c5-367613ffaa8b">


- Understand how to preprocess fMRI data for resting-state functional connectivity analysis
- Understand how to extract and input a "seed" timeseries to search for brain regions that show resting-state connectivity with this "seed" region of interest.


## Step 1, preprocess resting-state fMRI data
We will use the steps you learned from last block to preprocess the resting-state data.

- Let's use FEAT again to set up preprocessing
    - Go to the subject folder and launch FSL
        * `cd ~/fmriLab/flankerData_n4/sub-001/func`
        * `fsl`
    - In FSL GUI, open 'FEAT FMRI analysis'
        - Define scope of 'First-level analysis' to 'Preprocessing' at the top of the GUI
        - Select `sub-001-task-rest_bold.nii.gz` as input 4D. 
        - Set output to `~/fmriLab/flankerData_n4/sub-001/func/rest_rmot.feat`
        - We will delete the first 4 volumes in `Delete volumes`
        - Leave the High pass filter cutoff (s) to 100s

    - Go to the Pre-stats tab. We will do the following preprocessing
        - Motion correction with `MCFLIRT`
        - Select `BET`
        - Spatial smoothing of 6 mm
        - select `Highpass`

    - Go to the Registration tab, do the following:
        - Select `Main Structural Image`
        - Select the "brain extracted" T1 as the main structural image 
        - Change to normal search and 12 DOF
        - For standard space, change to normal search and 12 DOF 

- Hit Go!

- We then need to manually do "low-pass" filter. That is because FEAT does not support it (only does highpass). We have to do it via command line in the terminal.
  - Now open the terminal, move to the `rest_rmot.feat` folder you just made: `cd ~/fmriLab/flankerData_n4/sub-001/func/rest_rmot.feat`
  - Note, this might not work if you didn't save rest_rmot.feat under sub-001, in that case you have to find our where you saved it.
  - Then run this command:
`fslmaths filtered_func_data.nii.gz -bptf -1 2.5 filtered_func_data.nii.gz`
- Here we are doing lowpass filtering of 0.08 hz. 
    - the `-bptf` option expects a high-pass sigma and a low-pass sigma, which can be caluclated by
    - `highpass_sigma = 1 / (2.35 * TR * HP_freq)` (we use "-1" because we already highpassed the data)
    - `lowpass_sigma = 1 / (2.35 * TR * LP_freq))` (remember TR is 2s)
    - If interested in an explanation for this, see here: https://www.jiscmail.ac.uk/cgi-bin/webadmin?A2=fsl;fc5b33c5.1205 


## Step 2. Locate a seed region of interest in fsleyes 

- Stay in the preprocessed output folder `~/fmriLab/flankerData_n4/sub-001/func/rest_rmot.feat/`

- Locate the right motor cortex
  - Use fsleyes to open up the preprocessed structural image
     - `file`, `add from file`, goto `reg`, select `highres`
  - Also add the `filtered_func_data` 
  - In the Overlay list panel, select filtered_func_data image 
  - To navigate to the right motor cortex, enter the following x y z coordinate for scanner anatomical space: \
x=34 (top row), y=-12 (middle row), z=24 (lower row)

<img width="1468" alt="Screen Shot 2023-11-16 at 9 45 47 AM" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/b6db0faf-87f5-4029-b6d2-2fd30e92719d">


## Step 3. Create a functional connectivity seed map using fsleyes and save it as a nifti file. 

  - With your cursor on your seed mask, go to `View` -> `Timeseries`
  - With your cursor still on your seed mask, go to `Tools` -> `Seed correlation (Pearson)` - what do you see?!
  - Notice we now have a new image in our Overlay list, and we can explore it's range and distribution to understand it more
  - Based on the distribution, what would be a reasonable threshold to try to replicate the seed map at the start of the tutorial?
  - **Save your seedmap** in an image by clicking on the disk to the left of the image name in your Overlay list. Your saved image will end in `.nii.gz` which is a "nifti file" that you can open again in fsl later.

<img width="1461" alt="Screen Shot 2023-11-16 at 10 14 25 AM" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/adff8702-7621-45bd-a832-ea2b6bae9e5d">

## Step 4. Threshold your functional connectivity seed map 
   - Below is an example of steps in fsleyes for thresholding your seedmap to keep only the voxels with the strongest correlation to your seed.

<img width="1082" alt="Screen Shot 2023-11-17 at 10 43 29 AM" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/2409f38b-9bc7-469f-8ad2-f0c743135937">


## Technical Assignment. Run the same seed analysis for the "task state" by using the flanker data  
   - Replicate all the steps above with sub-001 but use their flanker data as input (`sub-001_task-flanker_bold.nii.gz`)
   - I suggest you name your .feat folder something distinct, like `flanker_rmot.feat`
   - Create a seed map for the right motor cortex, that you threshold at r>.70 like above, and display your timeseries in fsleyes
   - Overlay your seedmap from resting state, threshold at r>.70, and display the map in a different color
   - Are they more similar or different than you expected and why?
  
   - With your task timeseries and thresholded seedmaps from rest and task in view, save your work by taking a screenshot with these steps:
       - Applications -> Accessories -> Scroll down to `Screenshot`
       - Select a region -> use your cursor to select your fsleyes display
       - Save your map as: `hawkid_rmot_seedmaps.png` 
       - Upload this `.png` file to ICON to turn in your technical assignment

<br/>
<br/>
<br/>


