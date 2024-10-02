**By the end of this practical you should be able to:** <br/>
* [ ] create and understand a model of task-related BOLD signal in the FEAT GUI <br/>
* [ ] understand how to test for activation differences between conditions <br/>
* [ ] locate and view the activation maps in fsleyes <br/>
<br/>

**Access FastX** through the remote login: <br>
https://fastx.divms.uiowa.edu:3443/  <br/>
<br/>

**Create model of task-related BOLD signal in FEAT:** <br/>
*  In terminal, move yourself to your data folder `cd ~/fmriLab/`
*  Type `fsl` and click on `FEAT FMRI analysis`
*  Now instead of `Preprocessing` select `Statistics` in the drop-down menu at the top, like so: 
![single-subject_feat-set-statistics-only](https://github.com/mwvoss/PSY4025_FA23/assets/24663988/0f29a30a-e7e1-4b98-93ff-71b03263af36)

<br/>
<br/>

*  Then select `Input is a FEAT directory` and navigate to `sub-001`'s `flanker.feat` directory: <br/>
<img width="580" alt="featInput" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/87959e8f-1637-4937-b3fe-8bc0b77c7b2e">
<br/>

<br/>
<br/>

*  Move to the `Stats` tab, first turn on `Add additional confound EVs` and then select the `outliers.txt` file in your `beh` folder as shown: <br/>
<img width="578" alt="inputOutliers" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/d4e1ccb6-998a-49ae-a690-db9652d3e7fc">
<br/>
<br/>
<br/>

*  Next, click on `Full model setup`. Set up your model using tabs for each explanatory variable (EV) like shown below: <br/>

EV1: <br/>
<img width="420" alt="EV-con" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/3e3e2b63-4ddc-4034-97fa-e5ed76bfeaa3"> <br/>
<br/>
<br/>

EV2: <br/>
<img width="424" alt="EV-neu" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/8837262b-edf5-406d-b0d1-219f97360c3b"> <br/>
<br/>
<br/>

EV3: <br/>
<img width="421" alt="EV-inc" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/c3492c2e-fb3f-4438-9801-f7454e46f2ad"> <br/>
<br/>
<br/>

EV4: <br/>
<img width="420" alt="EV-errors" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/8560cd5f-34c5-4ef7-90ae-7692bde43083"> <br/>
<br/>
<br/>

*  After setting up the EVs, stay in the `Full model setup` window and go to the `Contrasts & F-tests` tab. Set up the contrasts as below. Click `Done` when setup complete. <br/>
<img width="424" alt="taskContrasts" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/9af5a33b-4a12-4073-97b2-af3eeb9f18b6">

<br/>
<br/>
</br>

* After completing the `Full model setup` you will get your task model! <br/>
<img width="587" alt="taskModel" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/3449ea40-1033-4476-83ec-646d37af9df9">

<br/>
<br/>

* The last tab in the FEAT GUI is `Post-stats`. We will leave the defaults on for now. The settings here are most relevant when we get to group-level analyses.

<br/>
<br/>

* Click `Go`. When it's finished, the results will appear within your `flanker.feat` directory. Your html report will then include output of brain activation maps as previewed below.<br/>
<img width="976" alt="featReport" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/7027b602-436c-4fc9-bbf0-a85f65d86307">

<br/>
<br/>

* Using `fsleyes` will allow us to view the results more interactively:
    * Use the html report to locate the directory where the activation maps are on your computer
    * Use the terminal to move yourself there: `cd ~/fmriLab/flankerData_n4/sub-001/func/flanker.feat/`
    * Open fsleyes through the terminal with settings for viewing FEAT output: `fsleyes -ad filtered_func_data.nii.gz stats/zstat1 stats/zstat2 stats/zstat3`
    * In the fsleyes menu, select `View` -> `Layouts` -> `FEAT mode` 
    * You should see a display like below in `fsleyes`. 
    * Clicking on the buttons with arrows in the column labeled `Z Max location` will move your cursor to the location of that peak in brain activation. Give it a try!
<br/>
<br/>

<img width="1460" alt="fsleyesFEAT" src="https://github.com/mwvoss/PSY4025_FA23/assets/24663988/8d10b01a-da7b-4e2f-927e-80f9e6281810">

<br/>
<br/>


* Once you've completed all the steps above for `sub-001`, repeat for `sub-002` and `sub-003`. Example PDFs for their FEAT activation reports will be on our course ICON site. Before next class, you should have statistical maps for the same contrasts, in the SAME order, for all subjects.

