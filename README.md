# Repository for Higgs mass diphoton analysis.
This package has been forked from musella/diphotons. In order to have it run fully, you need [flashgg](https://github.com/cms-analysis/flashgg) package. For now, though, we are only interested in the category optimization part. This can be run independently from flashgg. Instructions on how to do so are in the following.
## Checking out the code
In order to avoid a weird behavior of the package, a proper combination of CMSSW release and scram architecture must be chosen. Please find below a set of instruction to properly set up your environment.
```
SCRAM_ARCH=slc7_amd64_gcc493 				//set up proper scram arch
export SCRAM_ARCH
cmsrel CMSSW_7_6_7					//set up proper CMSSW release
cd CMSSW_7_6_7/src
git clone https://github.com/fiemmi/diphotons		//clone the repo
cd diphotons
git checkout Hgg_mass_IHEP				//checkout to IHEP branch
scram b -j 20 Utils/ RooUtils/				//you only need these two dirs for category optimization
							//Ignore flashgg-related warnings
```
## Running the code
Please find below a set of instructions to run the category optimization.
```
cd Utils/macro
./categoryOptimizationMultiDim.py --load  optimize_dipho_TaoUL2017_StdHgg_TaoTestDDQCD.json --infile /eos/cms/store/user/jtao/MassInterference/CMSSW_10_6_8/MiniTree/New_MCpp_DataDriven_QCD_SFs_sEoEWgt_2DpTWgt.root --sigfile /eos/cms/store/user/jtao/MassInterference/CMSSW_10_6_8/MiniTree/output_sig125_NewTreeName.root --outdir myOutput --label myOutput >& myOutput.log
```
