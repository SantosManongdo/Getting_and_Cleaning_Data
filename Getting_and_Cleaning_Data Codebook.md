#Getting and Cleaning the Data Course Project Codebook


##Data Source

The data used in this project came from the Human Activity Recognition Using Smartphones experiments conducted by Davide Anguita, Alessandro Ghio, Luca Oneto, Xavier Parra and Jorge L. Reyes-Ortiz.  

As mentioned in the Features_info document, the experiments have been carried out with a group of 30 volunteers wearing a smartphone on their waist while performing six activities (WALKING, WALKING_UPSTAIRS, WALKING_DOWNSTAIRS, SITTING, STANDING, LAYING). Using the embedded accelerometer and gyroscope in the smartphone, the 3-axial linear acceleration and 3-axial angular velocity were captured  at a constant rate of 50Hz. The data collected were randomly partitioned into two sets where measurements from 70% of the volunteers were marked as training data and the remaining 30% as test data. A full description of the  features is available at this site http://archive.ics.uci.edu/ml/datasets/Human+Activity+Recognition+Using+Smartphonesm)

The data itself can be downloaded from this URL and a detailed description of the data can be read in the **README.txt** https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip

The following files are contained in the .zip file:
* features_info.txt: Shows information about the variables used on the feature vector.
* features.txt: List of measurement feature names
* activity_labels.txt: Links the class labels with their activity name.
* train/X_train.txt: Training set - 70 % of the randomly partitioned measurement data obtained from volunteers.
* train/y_train.txt: Training labels - numeric value of the activity for which the training measurement data were obtained.
* train/subject_train.txt Train subject identifier refers the volunteer who performed the activity.
* test/X_test.txt: Test set - 30 % of the randomly partitioned measurement data obtained from volunteers.
* test/y_test.txt: Test labels -  numeric value of the activity for which the test measurements data were obtained.
* test/subject_test.txt Test subject identifier refers the volunteer who performed the activity.


##Feature Selection
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. These signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.
*tBodyAcc-XYZ
*tGravityAcc-XYZ
*tBodyAccJerk-XYZ
*tBodyGyro-XYZ
*tBodyGyroJerk-XYZ
*tBodyAccMag
*tGravityAccMag
*tBodyAccJerkMag
*tBodyGyroMag
*tBodyGyroJerkMag
*fBodyAcc-XYZ
*fBodyAccJerk-XYZ
*fBodyGyro-XYZ
*fBodyAccMag
*fBodyAccJerkMag
*fBodyGyroMag
*fBodyGyroJerkMag

For each of the signals and direction above, the following set of variables were generated as features:
*mean(): Mean value
*std(	): Standard deviation
*mad(): Median absolute deviation 
*max(): Largest value in array
*min(): Smallest value in array
*sma(): Signal magnitude area
*energy(): Energy measure. Sum of the squares divided by the number of values. 
*iqr(): Interquartile range 
*entropy(): Signal entropy
*arCoeff(): Autorregresion coefficients with Burg order equal to 4
*correlation(): correlation coefficient between two signals
*maxInds(): index of the frequency component with largest magnitude
*meanFreq(): Weighted average of the frequency components to obtain a mean frequency
*skewness(): skewness of the frequency domain signal 
*kurtosis(): kurtosis of the frequency domain signal 
*bandsEnergy(): Energy of a frequency interval within the 64 bins of the FFT of each window.
*angle(): Angle between to vectors.

Additional features were obtained by averaging the signals in a signal window sample. These are used on the angle() variable:
*gravityMean
*tBodyAccMean
*tBodyAccJerkMean
*tBodyGyroMean
*tBodyGyroJerkMean

The complete list of 561 features generated from this experiment is available in **features.txt**


## Cleaning feature names 

For each of this 3 signals, 
_fBodyAcc_
_BodyAccJerk_
_fBodyGyro_
the following measurements were recorded for each direction (X,Y,Z) but the variable name did not identify the direction, hence column names are duplicated
bandsEnergy()-1,8
bandsEnergy()-9,16
bandsEnergy()-17,24
bandsEnergy()-25,32
bandsEnergy()-33,40
bandsEnergy()-41,48
bandsEnergy()-49,56
bandsEnergy()-57,64
bandsEnergy()-1,16
bandsEnergy()-17,32
bandsEnergy()-33,48
bandsEnergy()-49,64
bandsEnergy()-1,24
bandsEnergy()-25,48

To remove duplicate column names, make.unique() function is used. The function appends '.1' on the second set of repeated variables and '.3' on the third set of repeated variables

```{r eval=FALSE}
# check for any duplicate values
duplicated(features$V2)

# make values unique to have unique column names
features$V2 <- make.unique(features$V2) 
```




