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
6 patches were selected from the HSC dataset for this test, and the data was put at each of the remote sites.  


## Moving Raw Data into place Yanny

## setting up Butler repositories Yanny
## Determining we have all input data in place Yanny
## Campaign Management and communication Jen
## 3X3 processing across sites – Jen 
## Data Product QA - Yanny




See the [Documenteer documentation](https://documenteer.lsst.io/technotes/index.html) for tips on how to write and configure your new technote.
