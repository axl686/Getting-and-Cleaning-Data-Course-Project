The run_analysis.R script is composed of five (5) major phases with the following functionality:

Phase 1 is designed to merge the training and the test sets to create one data set. It has three (3) sub-phases with the following functionality:

Phase 1.1 reads the training and its corresponding subject and activity label files and merge it into one tidy data set named mergedTrainingSet.
Phase 1.2 reads the testing and its corresponding subject and activity label files and merge it into one tidy data set named mergedTestingSet.
Phase 1.3 merges the training and testing tidy data sets into one and name it as mergedDataSet.
Phase 2 is designed to extract only the measurements on the mean and standard deviation for each measurement in mergedDataSet. . It has three (3) sub-phases with the following functionality:

Phase 2.1 reads the file feature.txt and calls the getMeanStdCol() function to extract the index of the mean and standard deviation columns. The indices were then assigned to meanStdIndex.
Phase 2.2 combines the indices in meanStdIndex as well as the subject and activity indices, respectively.
Phase 2.3 extracts the necessary columns and assign it to filteredDataSet.
Phase 3 is designed to appropriately label the data set (filteredDataSet) with descriptive variable names taken from the features.txt file.
Phase 4 is designed to assign a descriptive activity name for every activity in the filteredDataSet through the following phases:

Phase 4.1 reads the activity_labels.txt file to create a lookup table (activityLabels).
Phase 4.2 assign the appropriate activity label based on the values in the lookup table.
Phase 5 is designed to create a second, independent tidy data set with the average of each variable for each activity and each subject using the dataset that was produced in Phase 4.
