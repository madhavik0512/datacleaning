This run_analysis.R performs the cleaning and and analysis of data after acquiring it using five steps provided in the project.

1. **Download the dataset**
  * dataset is downloaded and extracted by the link provided in the project.
2. **Assigning variables to datasets**
  * **features <- features.txt** : 561 rows and 2 columns\
   It contains features provided by the device which come from accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and       tGyro-XYZ.
  * **activies <- activity_labels.txt**: 6 rows and 2 columns\
   It contains list of six activites which the volunteer performs mapped by their labels.
  * **subject_test <- test/subject_test.txt** 2947 rows and 1 columns\   
   It contains the test data of volunteer subjects.
  * **x_test <- test/X_test.txt** 2947 rows and 561 column\
   It contains the recorded features of the test data.
  * **y_test <- test/y_test.txt** 2947 rows and 1 column\
   It contains the activity code labels of test data.
  * **subject_train <- train/subject_train.txt** 7352 rows and 1 columns\   
   It contains the train data of volunteer subjects.
  * **x_train <- train/X_train.txt** 7352 rows and 561 column\
   It contains the recorded features of the train data.
  * **y_test <- test/y_test.txt** 7352 rows and 1 column\
   It contains the activity code labels of train data.
3. **Merging train and test dataset into one dataset**
  * rbind the subject_test and subject_train dataset.
  * rbind the X_test and X_train dataset.
  * rbind the y_test and y_train dataset.
  * cbind the above three dataset into one dataset called the Merged_Data.
4. **Extracting only the variables containing mean and standard deviation**
  * A new dataset TidyData is extracted having 10299 rows and 88 columns by selecting columns subject, code and the columns        containing mean and standard deviation("std").
5. **Using actual activity names instead of label code**
  * Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of the           activities variable.
6. **Appropriately labels the data set with descriptive variable names**
  * code column in TidyData renamed into activities
  * All Acc in column’s name replaced by Accelerometer
  * All Gyro in column’s name replaced by Gyroscope
  * All BodyBody in column’s name replaced by Body
  * All Mag in column’s name replaced by Magnitude
  * All start with character f in column’s name replaced by Frequency
  * All start with character t in column’s name replaced by Time
7. **From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject**
  * FinalData (180 rows, 88 columns) is created by sumarizing TidyData taking the means of each variable for each activity       and each subject, after groupped by subject and activity. 
  * Export FinalData into FinalData.txt file.