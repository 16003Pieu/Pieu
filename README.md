This folder contains 2 raster elevation files and 1 raster landcover file,
and was created to run the subgrid preprocessor code over multiple datasets.

# Step 0: Download data from git-lfs
You will need to download the data from git-lfs before running the code.

```commandline
git lfs fetch
git lfs pull
git lfs checkout
gunzip fort.14.gz
```

Alternatively, you can clone the data from github from from local desktop cmd.
You have to have github installed in your desktop from the [site for windows](https://git-scm.com/downloads/win)

```bash
git clone https://github.com/waterinstitute/adcirc-subgrid.git
```
For the first time you would have to input your git user id and password.

There should be 3 tif files:
0. 2021_CCAP_J1139301_4326.tif --> Landuse file to be used in both runs
![Screenshot](images/landcover.png)
1. galveston_13_mhw_20072.TIF  --> digital elevation model for one section of the region
2. galveston_13_mhw_20072.TIF  --> digital elevation model for another section of the region
![Screenshot](images/dem1_2.png)




# Step 1: Run Preprocessor Pass 1

Run subgrid preprocessor with `input.yaml` as input. This will use one of the
dem files, landcover file, and mesh file to build a subgrid lookup table.

# Step 2: Run Preprocessor Pass 2

Run subgrid preprocessor with `input_update_existing.yaml`. The updated yaml
contains an extra optional input line called "existing subgrid" where you
add the filepath of the existing subgrid. Running the preprocessor code again
will use the second dem file, landcover file, and mesh file to build and
updated lookup table with subgrid values for the first and second dem included.

## NOTE
  - The code will not overwrite the existing subgrid data, so use the highest priority datasets first.
  - It is recommended that you use a different name for the updated subgrid table to keep track of everything.
