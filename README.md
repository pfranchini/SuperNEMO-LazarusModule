# SuperNEMO-LazarusModule

Paolo Franchini 2020 - p.franchini@imperial.ac.uk

SuperNEMO module to resuscitate hits in order to improve the reconstruction in the Tracker.

The module removes tracker hits from the simulated data correspondent to a list of dead cells in the tracker.
The list can be randomly generated or read from a text file.

Input: simulated data with CD bank. \
Output: filtered simulated data with CD bank, to be used in a full reconstruction; list of dead cells killed.

## Build:
```
git clone https://github.com/pfranchini/SuperNEMO-LazarusModule
mkdir SuperNEMO-LazarusModule.build
cd SuperNEMO-LazarusModule.build
cmake -DCMAKE_PREFIX_PATH=<path_Falaise_build> -DGSL_ROOT_DIR=<path_GSL_build> ../SuperNEMO-LazarusModule
make
make test
```

## Configure the module:
There is the way to configure the module, for the name of the output file and the option to use a list of dead cells or a randomized generation, using `LazarusModule.conf` produced in the build directory:
```
# - Module configuration:                                                                                                                                                  
...
```

## Run the module:
```
flreconstruct -i <brio_file_with_calibration_bank.brio> -p LazarusModule.conf
```

## Run the remaining reconstruction:
```
flreconstruct -i <test-output.brio> -p official-2.0.0_from_CAT.conf -o <test-output-reco.brio>
```
