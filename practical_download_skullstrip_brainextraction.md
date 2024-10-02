**By the end of this practical you should be able to complete preprocessing on your data with the following steps:** <br/>
* [ ] use FSL's [bet](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki/BET/UserGuide) tool to remove the brain from a T1 image <br/>
* [ ] use FSLeyes to check the output of `bet` <br/> 

<br/> 

**Access FastX** through the remote login: <br>
https://fastx.divms.uiowa.edu:3443/  <br/>
<br/>


**In the terminal move to the folder where our downloaded data is:**<br/>
* A the terminal prompt type: `cd fmriLab`
* Type `ls` and you should see the data you downloaded as a folder named `flankerData_n4`

<br/> 

**Using FSL's `brain extraction tool` to skull-strip:**<br/>
* At the prompt type `fsl`
* Click the "BET brain extraction" button on the FSL menu
* Steps to set up `BET`
  * Click the yellow folder to select your defaced T1 image with skull as your `Input Image` 
  * FSL will automatically fill in the `Output Image` to have the same file name as your T1 with `_brain` at the end
  * Expand `Advanced Options`
     * Select `Output binary brain mask image`
  * Select `Go` to run `BET`
* Example default settings <br/> 
![betDefault](https://github.com/mwvoss/PSY4025_FA23/assets/24663988/b39c96b4-29ba-455d-9135-f74f5b8d2eec)

<br/>

**Checking BET:**<br/>
* Use the GUI menu to open your defaced T1 and brain mask in FSLeyes
* Use the `Opacity` slider to make the mask transparent so you can see the brain image in the background
* Checklist
  * [ ] Top of the brain: does the mask cover the brain and not spill into the eyes or skull?
  * [ ] Bottom of the brain: does the mask "hug" the brainstem or spill into the throat?

<br/>

**Modifying BET settings:**<br/>
* Open or go back to the BET GUI
* An advanced option that always helps: Use the dropdown menu to select `Robust brain centre estimation`
* If your mask was too small or large at the top of the brain, change the `Fractional intensity threshold` 
* If your mask was too small or large at either the top or the bottom of the brain, change the `Threshold gradient`

![betMods](https://github.com/mwvoss/PSY4025_FA23/assets/24663988/5b5a6a4f-fffb-4a25-8920-c1c52e6e6839)


