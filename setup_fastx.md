This page shows you how to setup your fastx linux environment to have access to the FSL program.

**Access FastX** through the remote login link below: <br>
https://fastx.divms.uiowa.edu:3443/

<br>
<br>

**Accessing FSL** <br>
The program we'll use for viewing and analyzing MRI data is called [FSL](https://fsl.fmrib.ox.ac.uk/fsl/fslwiki). The program is installed for you already, but you each need to add "instructions" for the terminal to find it from your home account. These instructions are in a `.bashrc` file.

How to modify your `.bashrc` file to access FSL

*  Click on the terminal icon in your fastx desktop
   *  If unsure what this looks like, hover over the icons in the top left of the screen with your cursor and click on the `MATE terminal` icon
*  At the prompt type `gedit .bashrc`
   *  We've just opened the `.bashrc` file with the text editor program `gedit`
*  Add the following lines to your `.bashrc` file (copy/paste encouraged)
```
export FSLDIR=/opt/fsl
export PATH=${FSLDIR}/bin:\
/opt/mricron/:\
${PATH}
export LD_LIBRARY_PATH=/opt/fsl/extralibs
. ${FSLDIR}/etc/fslconf/fsl.sh
```
*  Click `Save`
*  In the terminal type `source .bashrc`
*  **Did it work?**
   *  In the terminal type `fsl`
   *  You should see a gray menu box pop up


<br>
<br>

**Accessing AFNI** </br>

The AFNI software, version 20.3.01, has been installed on the four FastX nodes. In order for users to run the software, you will need to type the following before running the software.

`source /opt/AFNI/etc/AFNI_setup`

<br>

In addition, before the first time you run the software (and ONLY the  first time), you will need to type:

`/opt/AFNI/etc/AFNI_once_only > /dev/null`

*  **Did it work?**
   *  In the terminal type `3dvolreg`
   *  You should see usage information for this tool

AFNI can be a little resource intensive, so please keep that in mind when using the software.


<br>

**These commands can also be added to your `.bashrc` file so that you can source FSL and AFNI together at once:**

Reminder you can edit this file by opening your terminal and typing `gedit .bashrc`, make edits, then click `Save` in the top right corner of your editor.

```
export FSLDIR=/opt/fsl
export AFNIDIR=/opt/AFNI

export PATH=${FSLDIR}/bin:\
/opt/mricron/:\
${AFNIDIR}/etc:\
/opt/AFNI/etc/AFNI_setup:\
${PATH}

source /opt/AFNI/etc/AFNI_setup

export LD_LIBRARY_PATH=/opt/fsl/extralibs
. ${FSLDIR}/etc/fslconf/fsl.sh
```
