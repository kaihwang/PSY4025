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

