# SUPREME
SUPREME: A cancer subtype prediction methodology using Graph Convolutional Neural Networks

---

### How to run SUPREME?

Run `SUPREME.py` after generating the proper input data.

**User Options**

- Adjust the following variables (lines 2-6):
  - `base_path`: the path to SUPREME github folder
  - `dataset_name`: the data folder name in `base_path` including required input data for SUPREME run
  - `node_networks`: list of the datatypes to use (should have at least 1 datatype)
  - `features_to_integrate`:  list of the datatypes to integrate as raw feature
  - `addRawFeat`: *True* or *False*: If *True*, raw features from listed datatypes in `features_to_integrate` will be integrated; if *False*, no raw features will be integrated.

- Adjust the following hyperparameters (lines 8-13):
  Those hyperparameters are designed only for quick check. While running SUPREME for the real data, use the default values, or manually adjust them.
  - `max_epochs`: maximum number of epoch (default is 500.)
  - `min_epochs`: minimum number of epoch (default is 200.)
  - `patience`: patience for early stopping (default is 30.)
  - `learning_rates`: list of values to try as learning rate (default is [0.001, 0.01, 0.1].)
  - `hid_sizes`: list of values to try as hidden layer size (default is [16, 32, 64, 128, 256, 512].)
  - `xtimes`: the number of SUPREME runs for each hyperparameter combination (default: 10, should be more than 1.) 

---

#### How to generate input data for SUPREME?
- `base_path` should contain a folder named `dataset_name` (called as *data folder* afterwards). 
- `node_networks` will have the list of the datatype names that will be used for SUPREME run. These names are user-defined, but should be consistent for all the file names.
- In the *data folder*, there should be one label file named `labels.pkl` with the shape of  
  > torch.Size([{*sample size*}])

and the type of  

  > <class 'torch.Tensor'>
- In addition, the *data folder* will contain two '.pkl files per datatype.
  - `{datatype name}.pkl`: 
  - `edge.list_{datatype name}.pkl`:
- The *data folder* might have a file named `mask_values.pkl` if the user wants to specify test samples.
  - `mask_values.pkl`:
