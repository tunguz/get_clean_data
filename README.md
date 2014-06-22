# Getting And Cleaning Data Course Project

## 1. Importing All Files

### Following are the steps taken for the purpose of importing all the necessary data files:

Read the y_test.txt into a table y_test_table.

Read the subject_test.txt into a table subject_test_table.

Read the X_test.txt into a table X_test_table.

Read the y_train.txt into a table y_train_table.

Read the subject_train.txt into a table subject_train_table.

Read the X_train.txt into a table X_train_table.

### Following are the steps taken for the purpose of importing all the necessary lables and variables:

Read activity_labels.txt into a table activity_labels_table

Read features.txt into a features table features_table.

## 2. Renaming of variables

### We rename all variables with the more descriptive names.

Convert numerical values of different activities in the y_test_table into the descriptive ones.

Convert numerical values of different activities in the y_train_table into the descriptive ones.

## 3. Combine all six different tables inot a single one

Combine all different test tables into one single table.

Combine all different train tables into one single table.

Combine the test table and the train table into a single final table with all the elements.

## 4. Renaming of activities

### We rename all activities with the more descriptive names and rename all coulmns in the final table.

Turn features table into a vector of different features.

Change the first two columns of the final table into the more descriptive names.

Change the rest of the column names in the final table based on the features vector.

## 5. Subsetting the measn and standard deviation variables in the final table.

### We subset only the means and the standard deviation variables in the final table

Subset the features vector with the values that only include "-mean()" substring.

Subset the features vector with the values that only include "-std()" substring.

The final set of features that includes only subject, activity, means, and standard deviations.

Create the final table that only contains the final features.

## 6. Extracting the tidy data table

### We finally loop over the final table and extract information and mean values for each subject and activity type, and then add them incrementally to a new dataframe named df.

## 7. Saving the tidy data set as a text file.

### Finally, we save the final data frame df that contains only the means and the tidy data into  a text file tidy_data.txt

