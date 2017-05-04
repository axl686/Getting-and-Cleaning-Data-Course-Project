Basic information

This script was created during Getting and Cleaning Data course on Coursera. Basic purpose of this script is to take the data from adress below and transform it:

https://d396qusza40orc.cloudfront.net/getdata%2Fprojectfiles%2FUCI%20HAR%20Dataset.zip
Original dataset name: Human Activity Recognition Using Smartphones Dataset, Version 1.0
For a thorough description of the original data set and of the original study design please refer to the the documentation bundled with the above mentioned zip file.

Description of experiment provided with original data

The experiments have been carried out with a group of 30 volunteers within an age bracket of 19-48 years. Each person performed six activities (WALKING, WALKING _ UPSTAIRS, WALKING _ DOWNSTAIRS, SITTING, STANDING, LAYING) wearing a smartphone (Samsung Galaxy S II) on the waist. Using its embedded accelerometer and gyroscope, we captured 3-axial linear acceleration and 3-axial angular velocity at a constant rate of 50Hz. The experiments have been video-recorded to label the data manually. The obtained dataset has been randomly partitioned into two sets, where 70% of the volunteers was selected for generating the training data and 30% the test data.

The sensor signals (accelerometer and gyroscope) were pre-processed by applying noise filters and then sampled in fixed-width sliding windows of 2.56 sec and 50% overlap (128 readings/window). The sensor acceleration signal, which has gravitational and body motion components, was separated using a Butterworth low-pass filter into body acceleration and gravity. The gravitational force is assumed to have only low frequency components, therefore a filter with 0.3 Hz cutoff frequency was used. From each window, a vector of features was obtained by calculating variables from the time and frequency domain

Feature selection

According to the description provided in features_info in the original folder only a small subset of variables estimated from the signals are:

mean(): Mean value
std(): Standard deviation
These values were selected based on the assignment description. Mean frequencies were left out because they reflect more of how the observed features were evolving during the experiment than of their actual values.

The original number of 561 different variables is reduced to only 66 variables and 2 new variables are added:

subject: the id of the subject/volunteer performing the activity
activity: textual representation of the activity performed (one of the values WALKING, WALKING _ UPSTAIRS, WALKING _ DOWNSTAIRS, SITTING, STANDING, LAYING)
All names of the variables were described as specified in the ninth number of "Steps of transformation". Further description on the mean meaning of the variables can be found in CodeBook.md bundled hereby.

Steps of transformation

The transformation is made up of several steps:

Download the data from the URL specified above
Unpack the data from the zip file to temporary folder named "UCI HAR Dataset"
Get the names of the columns in original data set and pick only mean() and std() columns with descriptive statistics of means of standard deviations for each of the observed values in the original data set.
Read the data from the file "UCI HAR Dataset/test/X _ test.txt" and add columns identifying subject of the activity and activity perfomed from files "UCI HAR Dataset/test/subject _ test.txt" and "UCI HAR Dataset/test/y _ test.txt" respectively. Skip the columns that are not of interest according to step 3.
Do the same steps described in step four for the "UCI HAR Dataset/train" folder
Bind the two sets of collected in steps four and five.
Transform the names of the columns to the style described in lectures (lower case, no hyphens/undersores/dots/parenthesis included -> column names must match regex "[a-z0-9]+"). Also some of the original typos like "fBodyBodyAccJerkMag-mean()" were corrected to "fbodyaccjerkmagmean".
Replace the values in the activity column for its textual representations, which are derived from the "UCI HAR Dataset/activity_labels.txt"
Transform the data into data frame with 180 rows (30 volunteers performing 6 activities each) with 66 + 2 columns (66 descriptive statistics of mean and standard deviation + subject/volunteer id + activity performed). The description of the exact form of transformation is given in the "Result set" part of this file.
Result set

The transformation takes all of the original 2.56 sec windows from which the original values are stemming and computes means for each value, each activity and each subject. In other words all the observations were grouped by their subject/volunteer id and activity performed and column means were calculated to get one row o grand means (means of the original means) and means of standard deviations for each activity performed by each of the volunteers.

Result set therefore includes 180 rows, one per each volunteer and activity performed consisting of:

subject/voluntee id: who performed the activity
activity: which activity was measured
66 columns of grand means and means of standard deviations for each of the variables described in the CodeBook.md
