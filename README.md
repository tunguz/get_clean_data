# Getting And Cleaning Data Course Project

## 1. Importing All Files

### Following are the steps taken for the purpose of importing all the necessary data files:

Read the y_test.txt into a table y_test_table.

Read the subject_test.txt into a table subject_test_table.

Read the X_test.txt into a table X_test_table.

Read the y_train.txt into a table y_train_table.

Read the subject_train.txt into a table subject_train_table.

Read the X_train.txt into a table X_train_table.

# Read activity_labels.xtx into a table

activity_labels_table <- read.table("./data/activity_labels.txt")

# Read features.txt into a features table.

features_table <- read.table("./data/features.txt")

# Convert numerical values of different activities in the y_test_table into the descriptive ones:

for(i in 1:length(y_test_table[,1])){
        y_test_table[,1][i] <- as.character(activity_labels_table[[y_test_table[,1][i],2]])
}

# Convert numerical values of different activities in the y_train_table into the descriptive ones:

for(i in 1:length(y_train_table[,1])){
        y_train_table[,1][i] <- as.character(activity_labels_table[[y_train_table[,1][i],2]])
}

# Combine all different test tables into one single table:

test_table <- cbind(subject_test_table, y_test_table, X_test_table)

# Combine all different train tables into one single table:

train_table <- cbind(subject_train_table, y_train_table, X_train_table)

# Combine the test table and the train table into a single final table with all the elements:

total_table <- rbind(test_table, train_table)

# Turn features table inot a vector of different features:

features <- as.character(features_table[[2]])

# Change the first two columns of the final table into the more descriptive names:

colnames(total_table)[1:2] <- c("Subject", "Activity_Label")

# Change the rest of the column names in the final table based on the features vector

colnames(total_table)[3:563] <- features

# Subset the features vector with the values that only include "-mean()" substring

mean_features <- grep("-mean()", features, fixed=TRUE)

# Subset the features vector with the values that only include "-std()" substring

std_features <- grep("-std()", features, fixed=TRUE)

# The final set of features that includes only subject, activity, means, and standard deviations

final_features <- c("Subject", "Activity_Label", features[mean_features], features[std_features])

# Create the final table that only contains the final features:

final_table <- total_table[final_features]

# The following block of code loops over the final table and extracts information adn mean values 
# for each subject and activity type, and then adds them incrementally to a new dataframe named df.


df = data.frame(c())
for (k in lables){
        temp_df = data.frame(c())
        for (j in 1:30){
                second_partial <- subset(final_table, Subject == j & Activity_Label == k)
                temp_means_vector <- c()
                for (i in sub_final_features){
                        temp_means_vector <- c(temp_means_vector,mean(second_partial[,i]))
                }
                temp_df <- rbind(temp_df, temp_means_vector)
        }
        temp_df <- cbind(1:30, k, temp_df)
        colnames(temp_df)[1:2] <- c("Subject", "Activity_Label")
        colnames(temp_df)[3:68] <- sub_final_features
        df <- rbind(df, temp_df)
}

# Finally, we save the final data frame df that contains only the means and the tidy data into 
# a text file tidy_data.txt

write.table(df, "./data/tidy_data.txt", sep="\t")
