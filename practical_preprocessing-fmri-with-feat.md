

**Open the FEAT GUI:**<br/>
*  If FSL menu still open, let's move to the `FEAT FMRI analysis` menu
*  If FSL menu closed, in terminal type `fsl` and click on `FEAT FMRI analysis`


**Define scope of `First-level analysis` to `Preprocessing` at the top of the GUI:**
<br/> 
![preprocessing_feat-set-preprocessing-only](https://github.com/mwvoss/PSY4025_FA23/assets/24663988/309dafec-e7dc-4ff5-99f8-2250e61a3b7e)
<br/>
<br/>

**Data tab in FEAT GUI:**<br/>
*  On the `Data` tab, click `Select 4D data` and select your subject's fMRI flanker data
*  For example, subject sub-001's functional flanker data is in the `func` folder and named `sub-001_task-flanker_bold.nii.gz`
*  Set the `Output directory` as that subject's `func` folder
*  Name your output folder `flanker.feat` like the example below
*  Do not delete volumes or change the high-pass filter <br/>

![InputOutput](https://github.com/mwvoss/PSY4025_FA23/assets/24663988/e1589a1e-d2c6-4b78-9574-11ce9e980d97)


**Pre-stats tab in FEAT GUI:**<br/>
*  Keep MCFLIRT on with the default reference volume
*  Keep slice-timing as `None` here
*  Keep BET brain extraction on for the functional data (yellow box means 'on')
*  Set spatial smoothing to 6 mm
*  Keep the highpass filter on 
*  Do not turn on MELODIC ICA data exploration
<br/>

![PreStats](https://github.com/mwvoss/PSY4025_FA23/assets/24663988/53de9dd7-3b9c-4242-bd3c-85f8f704760a)



**Registration tab in FEAT GUI:**<br/>
*  Select `Main structural image` to open that window
*  Set your skull-stripped `_brain` image that you skull-stripped as the main structural image
*  Change search options to `Full search` and `12 DOF` <br/>

![Registration](https://github.com/mwvoss/PSY4025_FA23/assets/24663988/830efd78-6083-461b-bb4a-e9dbbaf91084)


**When you've set registration, click `Go`** <br/>

An html file should pop up in your browser, showing a log of the analyses progress. For preprocessing output, we will focus on `Registration` and `Pre-Stats`. As it's running let's locate and talk through the output.  <br/>

![sub001_preproc](https://github.com/mwvoss/PSY4025_FA23/assets/24663988/3acb5253-d7d8-42f9-a840-872ef54c8935)


<br/>

**On your own: complete sub-002 and sub-003. Results for registration and motion are shown below as a check of your output.**<br/>

<img width="930" alt="sub002" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/1264adb2-645b-48a4-b5c7-e70cc1af419c">

<br/>
<img width="929" alt="sub003" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/603157fb-b521-4b82-81d6-7e4d6b55551d">


<br/>
