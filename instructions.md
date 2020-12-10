# Downloads
Note: In Hospital(s), try to bypass your corporate (wired) internet; usually  
it will block any attempt by Matlab / EEGlab to download anything.  
You will get best mileage downloading via your own Android Hotspot.  
Alternatively, buy a Wifi Stick and connect to the Guest Network.



**Download EEGLAB**  
https://sccn.ucsd.edu/eeglab/downloadtoolbox.php


**EELAB Extensions**  
https://sccn.ucsd.edu/eeglab/plugin_uploader/plugin_list_all.php  
(but File -> Manage extension would also work)  
- FileIO
- BvaIO
- eegplot_w


**Download CWL-EEG-fMRI Toolbox** (EEGLAB extension)  
https://www.nitrc.org/projects/cwl_eeg_fmri/


**Download CWL-EEG-fMRI Data** (EEG & fMRI Data)  
https://www.nitrc.org/projects/cwleegfmri_data/



# Requirements
```matlab
>> ver
-----------------------------------------------------------------------------------------------------
MATLAB Version: 9.3.0.713579 (R2017b)

Operating System: Linux 5.7.10-arch1-1 #1 SMP PREEMPT Wed, 22 Jul 2020 19:57:42 +0000 x86_64
Java Version: Java 1.8.0_121-b13 with Oracle Corporation Java HotSpot(TM) 64-Bit Server VM mixed mode
-----------------------------------------------------------------------------------------------------
MATLAB                                                Version 9.3         (R2017b)
EEGLAB Toolbox to process EEG data                    Version -           see     
Signal Processing Toolbox                             Version 7.5         (R2017b)
```
Whenever Matlab upgrades, sometimes a routine called by (any) toolbox might not work anymore and things break. I cannot guarantee operation on R2020; but I hope that R2017b is recent enough - it includes fixes for a crash when I upgraded from Matlab 2011b to 2017b.



# Workflow
1. Remove MRI Gradient Artifact
    - there are more optimal and less optimal methods (!)
    - a syncbox is essenial, or if this is lacking; the Method of Sonia Goncalves (*Clinical Neuropysioloy, 2007*) is probably the best one.
2. Downsample (1000 Hz or 500 Hz are both good for the CWL-correction)
3. Fix the Channel Position(s)
4. Filterings:
    - low-pass (can try different settings! -- maybe ~ 45/70?)
    - high-pass (can also try different settings -- usually > 1)
5. Check the signals in the CWLs - do they look good?
6. Run the CWL Correction
7. Rationale for of those parameters
    - windows -> adaptive
    - window Length -> enough to capture some BCGs!
    - delay value -> increases/decreases model fit; might overfit (!)
8. Compare with the situation outside of the MRI scanner and see if you're happy
9. Identify the bad bits (channels/times), take care of those in follow-up.
10. 'Re-emergent' power at higher frequences - see (8)

# Advantages
- Adaptive
- No need to mark the ECG, where precise timing might often be crucial and is labor-intensive.
- Capabiliy to check motion in separate channels
- The Correction is typically quite fast

# Alternative approaches


