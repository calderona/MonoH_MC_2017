# README:


## 1. Create the gridpacks using the 2017 configuration

See the documentation here: https://github.com/cms-sw/genproductions/tree/master/bin/MadGraph5_aMCatNLO/cards/production/2017/13TeV/monoHiggs/Zp2HDM/

```
git clone git@github.com:cms-sw/genproductions.git
cd genproductions/bin/MadGraph5_aMCatNLO/
```

For Zprime_A0h_A0chichi:

```
cp cards/production/2017/13TeV/monoHiggs/Zp2HDM/Zprime_A0h_A0chichi/genGridpack_2HDM.py .
cp -r cards/production/2017/13TeV/monoHiggs/Zp2HDM/Zprime_A0h_A0chichi/cards/* cards/. 
python genGridpack_2HDM.py
```

input cards are now generated in the cards directory

TEST your gridpacks:

```
cd CMSSW_7_1_30/src
cmsenv
tar xvf xxx.tar.xz
./runcmsgrid_LO.sh 5000 $RANDOM 1
```

## 2. Run the step0: produce root file that contains LHE objects

```
cmsRun step0.py tarball=xxx.xz outputFile=test.root maxEvents=10 
```



## 3. Run the step1: hadronize the output of step0 (decay modes)

Take your hadronizer from Configuration/GenProduction/python/ThirteenTeV/monoHiggs and copy it to the step1.py file

Here I took the WW decay:

```
cmsRun step1.py 
```

