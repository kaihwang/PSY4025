**By the end of this practical you should be able to:** <br/>
* [ ] use the FEAT GUI to create a group-level map of task-related BOLD activation <br/>
* [ ] locate and understand results using the html reports and fsleyes <br/>
<br/>

**Access FastX** through the remote login: <br>
https://fastx.divms.uiowa.edu:3443/  <br/>
<br/>

**Prerequisite**: Before you start group analysis, you should have `flanker.feat` output folders that you created for sub-001, sub-002, and sub-003. 
<br/>
<br/>

**Group analysis GUI**: Our group analysis will determine the average activation across subjects for each of our contrasts that we made within-subjects (e.g., con>baseline, neu>baseline, inc>baseline, errors>baseline, inc>nue, con>neu).
*  In terminal, move yourself to your data folder by typing `cd ~/fmriLab/`
*  Type `fsl` and click on `FEAT FMRI analysis`
*  In the top-left menu, select `Higher-level analysis`: <br/>
![group-analysis_feat-higher-level-button](https://github.com/mwvoss/PSY4025_FA23/assets/24663988/2c8c866a-2440-40ee-8c9e-46720748132c)
<br/>


**Set input and output on `Data` tab**:<br/>
*  Keep default of `Inputs are lower-level FEAT directories`
*  Keep `Number of inputs` to 3, because we have 3 subjects 
*  Click to `Select FEAT directories` and select each of your `flanker.feat` folders: <br/>
<img width="582" alt="featGroupInput" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/9b0f73d1-e26b-45ca-88de-1409dc11c3e9">


*  Keep `Use lower-level copes` as default, these are the six contrasts we set for the single-subject analyses
*  Specify output directory to be in derivatives with the name `group_n3`: <br/>
<img width="438" alt="featGroupOutput" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/f24b4bed-9b64-43bc-8da9-4097405df1e3">
<br/>


**Setup group model on `Stats` tab**: <br/>
*  Select `Fixed effects`, which computes an average generalizable to only this set of participants. This is most appropriate if you have less than 10 subjects.
*  Select `Model setup wizard` and keep the default of `single-group average` and click `Process`: <br/>
![group-analysis_feat-model-setup-wizard-single-group](https://github.com/mwvoss/PSY4025_FA23/assets/24663988/73f3499e-e7a0-49d8-9230-672126567699)

<br/>

**Our group model**: Now what does the red line represent?<br/>
![group-analysis_feat-group-model](https://github.com/mwvoss/PSY4025_FA23/assets/24663988/74ff39e2-c4eb-4f3c-a372-221d0e05c311)

<br/>

**Post-stats tab**: all settings here can stay as default.
<br/>

**Click `Go`**: 
*  An html output report will come up in your browser, or you can find it in the output folder you specified
*  Once done, navigate to `Results` and click on `Lower-level contrast 3 (inc)`
*  You should see the map below: <br/>
<img width="738" alt="incActivation" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/106c6699-9fa1-4beb-b3cc-270640bed30e">

<br/>

*  Click on the image in the html report, let's talk about the table you see below: <br/>
<img width="1381" alt="clusterTable" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/4b0d867b-d917-4851-a358-f9ba51c8b2a2">

<br/>
<br/>

* Just like with single-subject analyses, we can also use `fsleyes` to view the results more interactively:
    * Use the html report to locate the directory where the activation maps are on your computer
    * Use the terminal to move yourself there: e.g., `cd ~/fmriLab/flankerData_n4/group_n3.gfeat/cope3.feat/`
    * Open `fsleyes` through the terminal with settings for viewing FEAT output: `fsleyes -ad /opt/fsl/data/standard/MNI152_T1_2mm_brain.nii.gz thresh_zstat1.nii.gz`
    * Change your color scale to orange->yellow
    * Show your cluster table by selecting: View-> Layouts -> FEAT Mode
    * Clicking on the buttons with arrows in the column labeled `Z Max location` will move your cursor to the location of that peak in brain activation. 
    * See information from neuroanatomy atlases by selecting: Settings -> Ortho View 1 -> Atlas panel
    * You should see a display like below in `fsleyes`. 
![Screen Shot 2023-11-07 at 6 31 22 AM](https://github.com/mwvoss/PSY4025_FA23/assets/24663988/ef5c0331-7284-48da-971f-f40444daa13c)

<br/>
<br/>

For your next fMRI task analysis technical assignment, you will need to complete the single-subject task analysis for sub-004 and create a new group analysis that includes all subjects in your dataset (sub-001, sub-002, sub-003, sub-004)



