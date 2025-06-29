# 3X3 Multisite Production

```{abstract}
This RTN will describe the process that we have taken to prove that we can process data at multiple sites, bring data back to a central location for calibration, redistribute the out puts and continue the production.  These tests are a proof of concept for multisite production for LSST and are a key first step in understanding the process, and where we need to focus our development.
```

## Purpose of running this test  Jen
In order to run a full years worth of data from the LSST camera, while also keeping up with the nightly data production we will need to use the data facilities in France (IN2P3) and the UK Rutherford (RAL) and Lancaster (LANCS). The test we ran as our proof of concept was to take 6 patches of the sky from the HSC dataset.  Placed the data for 2 patches at each of the 3 sites.  We have a well defined pipeline of data that we run that has a combination of running on individual patches, and then doing overall calibration, and then goes back to running the individual patches.  We excersise this at 1 site on a bi weekly basis while testing the software stack.  This test is being done to do a proof of concept, that we can run data in this manner, and to help us to find any holes in our logic early in the process so we can better design a way of automating this enite process.  It should be noted that we moved the biweekly pipeline software validation to the remote sites early in January 2025 to free up cores at the USDF and to familiarize ourselves with running data remotely and moving output datasets back to the USDF and injesting them into the USDF butler.

The steps for doing this are outlined in this RTN.  
1) determine what data needs to be placed at each Data Facility
2) move the data to each of the data facilities using Rucio and injest that data in to the local Butlers
3) Verification that all data is in place
4) setting up the processing yamls for remote production
5) running the data at all 3 sites, bringing intermediate outputs back to the USDF for calibration and distributing the calibrated outputs to the remote sites and continuing production then bringing the final outputs back to the USDF for validation.


## What data are we using
@brian; How did you pick the fields that we are using for the 3X3?  I can give the fields and insert pretty pictures but where they "randomly selected" or did you have a reason for picking those particular fields?  Or maybe I just put this question into the rtn and let you answer it
6 patches were selected from the HSC dataset for this test, and the data was put at each of the remote sites. The patches at the sites overlap with the patches that are at that site but not with the patches at the other sites.  This proceedure allows us to excersise the process of moving the data and verifying that we understand what 

We used the pipeline diagrams https://tigress-web.princeton.edu/~lkelvin/pipelines/current/drp_pipe/HSC/DRP-Prod/ to determine what inputs we needed to have on disk at each site, and what data needed to be moved between sites for the calibration steps, and after calibration what data needed to be moved back to the sites to continue processing.  We also talked to pipelines to deterimine what the minimum dataset outputs needed to be moved back to SLAC for validation.

## Moving Raw Data into place Yanny

## setting up Butler repositories Yanny
## Determining we have all input data in place Yanny
## Campaign Management and communication Jen
For Production, we used the standard RC2 pipline setup that we use for weekly validation with different data queries to the butler to grab the correct patches out of the butler. 
These setups are tested and variables are smoothed out in weekly testing over a small dataset.
We used bps to submit jobs to the PanDa workload management system. At this point we do not have the steps daisy chained together yet so between each step the Production team took time to look at and understand outputs and any potential errors or problems that might occur and give feedback to the pipeline teams.  Communication with the pipeline teams and between the production team and the sites happened over SLAC and numerous Zoom calls.


## 3X3 processing across sites – Jen 
Six patches were picked out for our multi site test.  Two patches were placed at each site.  Steps1, Step2a and Step2b are run on a patch by patch basis and ran independently at each of the three sites.  Step2c is an overall calibration step so the required outputs from the previous steps were moved to SLAC using RUCIO, and injested into the central butler database and overall calibration was run.  The needed outputs were moved back to the remote sites using RUCIO and injested into the remote butlers. Then Step2d, Step2e, Step3, Step4 and Step5 are run.  The outputs are moved back to SLAC for the final overall calibration and the metrics were run at the remote sites and brought back. 
## Data Product QA - Yanny


<figure>
  <img src="figures/sixtract.png" />
  <figcaption> These are the six tracts chosen for the 3x3 test </figcaption>
</figure>


See the [Documenteer documentation](https://documenteer.lsst.io/technotes/index.html) for tips on how to write and configure your new technote.
