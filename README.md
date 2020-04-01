# Getting-and-Cleaning-Data-Project

The run_analysis.R script uses the data included in the UCI HAR Dataset to complete the following 5 steps as found in the course
project's description.

1. Merges the training and the test sets to create one data set.
   - Combine x_train and x_test to create new dataframe, x, using rbind()
   - Combine y_train and y_test to create new dataframe, y, using rbind()
   - Combine subject_train and subject_test to create new variable, subject, using rbind()
   - Combine all data (x, y, subject) to create final dataframe, combinedData, using cbind()

2. Extracts only the measurements on the mean and standard deviation for each measurement.
   - Create new dataframe from combinedData that includes only measurements on mean and standard deviation using the select() function
     within dplyr package
   - Store in new dataframe titled cleanData

3. Uses descriptive activity names to name the activities in the data set
   - Replaced "code" column with "activity" variable from "activity_labels" column

4. Appropriately labels the data set with descriptive variable names.
   - Renamed "subject" column to "Subject"
   - Renamed "code" column to "Activities"
   - Replaced "Acc" with "Accelerometer" in all columns using gsub()
   - Replaced "BodyBody" with "Body" in all columns using gsub()
   - Replaced "Mag" with "Magnitude" in all columns using gsub()
   - Replaced "^t" with "Time" in all columns using gsub()
   - Replaced "^f" with "Frequency" in all columns using gsub()
   - Replaced "-mean()" with "Mean" in all columns using gsub()
   - Replaced "-std()" with "STD" in all columns using gsub()
   - Replaced "-freq()" with "Frequency" in all columns using gsub()
   - Replaced "gravity" with "Gravity" in all columns using gsub()

5. Creates a second, independent tidy data set with the average of each variable for each activity and each subject.
   - Created new dataframe, groupData, that groups "Activity" and "Subject" variables using the group_by() function within dplyr package
   - Created final dataframe, finalData, that takes the mean (average) of each variable for each activity and subject using the   
     summarise_all() function (and funs(mean) argument) within dplyr package
   - Stored finalData as a .txt file using write.table()
