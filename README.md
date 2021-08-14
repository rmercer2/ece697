## WiFi Access Point Mapping and Embedding
Rebecca Mercer  
UW-Madison ECE Masters in Machine Learning and Signal Processing Capstone  
ECE 697 Final Project  
 
This is the code base associated with my final capstone project. This project aims to build a network of campus WiFi access points from time series data.
The concept of multidimensional scaling is utilized to discover spatial relationships between access points from temporal data.   

On a data set of one day of campus data and another of one week of campus data I process the data and experiment with various methods of measuring the proximity of access points to create dissimilarity matrices. The results of MDS that are visualized vary depending on how the dissimilarity of points is measured.  

To run multidimensional scaling and visualize the results follow these instructions:  
- Option 1:
  - download: MDS_test_OneDay.ipynb, buildings_dissimilarity_mat.csv, building_names.csv, and scaled_buildings_dissimilarity_mat.csv
  - follow the directions to run within the notebook
  - when visualizing the result you may change the building names in the test vector to any valid building name (see 'building_names.csv')
  - you will be able to visualize the results of building dissimilarity matrix using one day of campus data
  - these dissimilarity matrices used are for average times between: access points, buildings, and buildings scaled
- Option 2:
  - download: MDS_2021_04_01_week.ipynb, ds_mat_b_avg.csv, ds_mat_b_min.csv, ds_mat_b_avg_scaled.csv, ds_mat_b_min_scaled.csv, and ds_mat_labels_b.csv
  - run parts 1 and 2 in the file (imports and function defintions and the training and visualization of MDS results)
  - I do not recomment trying to run any of the access point matrix parts on your local machine
  - in running these parts you will notice the differences in computing the dissimilarity matrix and its affect on the results
  - you may change the test vector to an array of any set of buildings in the 'building_names.csv' file

The notebooks working with one day of data are as follows:
- DataPreprocessing_OneDay.ipynb 
  - takes the raw data and uses SQLite to create 'associations_times.csv'
- DissimilarityMat_OneDay.ipynb uses 'associations_times.csv'  and 'locations.csv' and computes:
  - Average Building Time Apart Matrix: buildings_dissimilarity_mat.csv
  - Building Labels: building_names.csv
  - Average Building Time Apart Scaled Matrix: scaled_buildings_dissimilarity_mat.csv 
  - Subset of Average Access Point Time Apart Matrix: test_dissimilarity_mat.csv
  - Access Point Labels: test_ids.csv
- MDS_test_OneDay.ipynb
  - runs with sample dissimilarity matrices produced above
  - calculates MDS embeddings using Scikit-learn MDS functions
  - Visualizes the results with labels and coloring to make results easier to interpret

The notebooks working with one week of data are as follows:
- DataPreprocessing_2021_04_01_week.ipynb 
  - takes the raw data and uses SQLite to create '2021_04_01_week_associations_times.csv'
- DissimilarityMat_OneDay.ipynb uses '2021_04_01_week_associations_times.csv'  and 'locations.csv' and computes many different versions of dissimilarity matrices including:
  - 'ds_mat_b_avg.csv'
  - 'ds_mat_b_min.csv'
  - 'ds_mat_b_avg_scaled.csv'
  - 'ds_mat_b_min_scaled.csv'
  - and the labels for visualizing ds building mats and ds access point mats
- MDS_2021_04_01_week.ipynb
  - runs MDS on various dissimilarity matrices and visualizes the result
  - five main parts of this file:
   - 1) defining the functions: normalize_data, mds_embeddings, get_cmap, display_b_results, and display_ap_results
   - 2) BUILDING TO BUILDING (get results of MDS on each variation of dissimilarity matrix, visualize the results on a set of buildings (this test set can be changed to random indices or any building names from the building_names.csv))
   - 3) ACCESS POINT TO ACCESS POINT (these results failed, but code included to see how would be done)
   - 4) TEST only using a subset of ACCESS POINT TO ACCESS POINT 
   - 5) TEST only using a subset of BUILDING TO BUILDING


Note: the data preprocessing and dissimilarity matrices for one day and one week are unique and to only be run once in creating files for MDS notebooks. 
MDS notebooks can take other dissimilarity matrices and labels following similar form.  
The MDS notebooks for one day and one week have different methods for visualization since they have different forms.


