The `run_analysis.R` script performs the data preparation and processes it according to the 5 steps required described in the course project’s definition.

1. Download the dataset
Happens from line 3 to 12 in the script. If the file is not available, it will download from the web and unzip it to process the data.

2. Assign the data to the corresponding variables
The variables `features`, `activities`, `subject_test`, `x_test`, `y_test`, `subject_train`, `x_train` and `y_train` were retrieved from the main folder from the files `features.txt`, `activity_labels.txt` and all the corresponding files from the `test` and `train` folders.

3. Merge the train and test data
- Merging `x_train` and `x_test` into `x` by using `rbind()` in line 25;
- Merging `y_train` and `y_test` into `y` by using `cbind()` in line 26;
- Merging `subject_train` and `subject_test` into `subject` by using `rbind()` in line 27;
- Merging all data (`x`, `y` and `subject`) into `merged_data`by using `cbind()` in line 28.

4. Extract only the measurements on the mean and standard deviation for each measurement
`tidy_data` is created by subsetting `merged_data` and selecting the columns `subject`, `code` and the measurements on the mean and standard deviation for each measurement.

5. Use descriptive activity names to name the activities in the data set
The numbers in code column of the `tidy_data` are replaced with corresponding activity taken from second column of the `activities` variable.

6. Label the data set with descriptive variable names
- `code` column in `tidy_data` renamed into `activities`;
- All `Acc` in column’s name replaced by `Accelerometer`;
- All `Gyro` in column’s name replaced by `Gyroscope`;
- All `BodyBody` in column’s name replaced by `Body`;
- All `Mag` in column’s name replaced by `Magnitude`;
- All start with character `f` in column’s name replaced by `Frequency`;
- All start with character `t` in column’s name replaced by `Time`.

7. Create a second, independent tidy data set with the average of each variable for each activity and each subject
- `final_data` gets created by sumarizing `tidy_data` taking the means of each variable for each activity and each subject, after groupped by subject and activity;
- Export `final_data` into `final_data.txt`.  
