##Getting and Cleaning Data Course Project
##CodeBook

Welcome! This is my attempt at the Course Project. I am a newbie to R and all.
So keep that in mind if you find something done in a very crude way. 
I am still learning and advice on coding is always appreciated.

Anyway!


##Files related
*The readme markdown document: Instructions on how to acquire the data, packages used and references and hints used.

*The R script named run_analysis.R: contains all the code with commentary.

*This codebook markdown document: describes all the variables and data transformation.

*The new dataset in txt file.


##Getting the data.Describing the original data.
The data was obtained from the UCI HAR dataset folder containing the text files 
x_test.txt: containing all the measured variables (features) values for the test

y_test.txt containing all the activity ids for the test dataset values

subject_test.txt containing all the ids for the subjects in the test dataset

x_train.txt  containing all the measured variables values for the train

y_train.txt containing all the activity ids for the train dataset values

subject_train.txt  containing all the ids for the subjects in the test dataset

The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals TimeAcceleration-XYZ and TimeGyroscope-XYZ. These time domain signals were captured at a constant rate of 50 Hz. Then they were filtered using a median filter and a 3rd order low pass Butterworth filter with a corner frequency of 20 Hz to remove noise. Similarly, the acceleration signal was then separated into body and gravity acceleration signals (TimeBodyAcceleration-XYZ and TimeGravityAcceleration-XYZ) using another low pass Butterworth filter with a corner frequency of 0.3 Hz. 

Subsequently, the body linear acceleration and angular velocity were derived in time to obtain Jerk signals (TimeBodyAccelerationJerkSignal-XYZ and TimeBodyGyroscopeJerkSignal-XYZ). Also the magnitude of these three-dimensional signals were calculated using the Euclidean norm (TimeBodyAccelerationMagnitude, TimeGravityAccelerationMagnitude, TimeBodyAccelerationJerkSignalMagnitude, TimeBodyGyroscopeMagnitude, TimeBodyGyroscopeJerkSignalMagnitude). 

Finally a Fast Fourier Transform (FFT) was applied to some of these signals producing FastFourierBodyAcceleration-XYZ, FastFourierBodyAccelerationJerkSignal-XYZ, FastFourierBodyGyroscope-XYZ, FastFourierBodyAccelerationJerkSignalMagnitude, FastFourierBodyGyroscopeMagnitude, FastFourierBodyGyroscopeJerkSignalMagnitude. (Note the 'f' to indicate frequency domain signals). 

These signals were used to estimate variables of the feature vector for each pattern:  
'-XYZ' is used to denote 3-axial signals in the X, Y and Z directions.

TimeBodyAcceleration-XYZ
TimeGravityAcceleration-XYZ
TimeBodyAccelerationJerkSignal-XYZ
TimeBodyGyroscope-XYZ
TimeBodyGyroscopeJerkSignal-XYZ
TimeBodyAccelerationMagnitude
TimeGravityAccelerationMagnitude
TimeBodyAccelerationJerkSignalMagnitude
TimeBodyGyroscopeMagnitude
TimeBodyGyroscopeJerkSignalMagnitude
FastFourierBodyAcceleration-XYZ
FastFourierBodyAccelerationJerkSignal-XYZ
FastFourierBodyGyroscope-XYZ
FastFourierBodyAccelerationMagnitude
FastFourierBodyAccelerationJerkSignalMagnitude
FastFourierBodyGyroscopeMagnitude
FastFourierBodyGyroscopeJerkSignalMagnitude

The set of variables that were estimated from these signals are: 

mean(): Mean value
std(): Standard deviation
mad(): Median absolute deviation 
max(): Largest value in array
min(): Smallest value in array
sma(): Signal magnitude area
energy(): Energy measure. Sum of the squares divided by the number of values. 
iqr(): Interquartile range 
entropy(): Signal entropy
arCoeff(): Autorregresion coefficients with Burg order equal to 4
correlation(): correlation coefficient between two signals
maxInds(): index of the frequency component with largest magnitude
meanFreq(): Weighted average of the frequency components to obtain a mean frequency
skewness(): skewness of the frequency domain signal 
kurtosis(): kurtosis of the frequency domain signal 
bandsEnergy(): Energy of a frequency interval within the 64 bins of the FFT of each window.
angle(): Angle between to vectors.

Additional vectors obtained by averaging the signals in a signal window sample. These are used on the angle() variable:

gravityMean
TimeBodyAccelerationMean
TimeBodyAccelerationJerkSignalMean
TimeBodyGyroscopeMean
TimeBodyGyroscopeJerkSignalMean

*Taken and updated from the original features_info.txt in the data folder.

  
##Data Transformation

The different text file tables were combined according to their dimensions. Then the column names were named using the features.txt and two extra labels "activity" and "subject". Then subsetted the columns containing the word "mean()" and "std()" in their names, dropped the columns containing the word "Freq" and all other column variables. Combined the "activity" and "subject" column to the new data frame.

The "activity" column values were replaced from code numbers to descriptive values using the "activity_labels.txt"

Then all columns names were reassigned to complete as possible variable names.

From this data set a new independent tidy data set was created with the average of each variable for each activity and each subject. The data frame then contains the following columns: "ActivityLabel" (describing the acitivity performed by the subject) "SubjectID" (identifying the subject performing the activity) and the various features columns that where means or standard deviation. 

Each row conforms a single observation. 

##Variables (Features) in the new tidy data set variable column
(Columns From new tidy data)

 [1] "ActivityLabel"                                        
 [2] "subjectID"                                            
 [3] "TimeBodyAcceleration-mean()-X"                        
 [4] "TimeBodyAcceleration-mean()-Y"                        
 [5] "TimeBodyAcceleration-mean()-Z"                        
 [6] "TimeBodyAcceleration-std()-X"                         
 [7] "TimeBodyAcceleration-std()-Y"                         
 [8] "TimeBodyAcceleration-std()-Z"                         
 [9] "TimeGravityAcceleration-mean()-X"                     
[10] "TimeGravityAcceleration-mean()-Y"                     
[11] "TimeGravityAcceleration-mean()-Z"                     
[12] "TimeGravityAcceleration-std()-X"                      
[13] "TimeGravityAcceleration-std()-Y"                      
[14] "TimeGravityAcceleration-std()-Z"                      
[15] "TimeBodyAccelerationJerkSignal-mean()-X"              
[16] "TimeBodyAccelerationJerkSignal-mean()-Y"              
[17] "TimeBodyAccelerationJerkSignal-mean()-Z"              
[18] "TimeBodyAccelerationJerkSignal-std()-X"               
[19] "TimeBodyAccelerationJerkSignal-std()-Y"               
[20] "TimeBodyAccelerationJerkSignal-std()-Z"               
[21] "TimeBodyGyroscope-mean()-X"                           
[22] "TimeBodyGyroscope-mean()-Y"                           
[23] "TimeBodyGyroscope-mean()-Z"                           
[24] "TimeBodyGyroscope-std()-X"                            
[25] "TimeBodyGyroscope-std()-Y"                            
[26] "TimeBodyGyroscope-std()-Z"                            
[27] "TimeBodyGyroscopeJerkSignal-mean()-X"                 
[28] "TimeBodyGyroscopeJerkSignal-mean()-Y"                 
[29] "TimeBodyGyroscopeJerkSignal-mean()-Z"                 
[30] "TimeBodyGyroscopeJerkSignal-std()-X"                  
[31] "TimeBodyGyroscopeJerkSignal-std()-Y"                  
[32] "TimeBodyGyroscopeJerkSignal-std()-Z"                  
[33] "TimeBodyAccelerationMagnitude-mean()"                 
[34] "TimeBodyAccelerationMagnitude-std()"                  
[35] "TimeGravityAccelerationMagnitude-mean()"              
[36] "TimeGravityAccelerationMagnitude-std()"               
[37] "TimeBodyAccelerationJerkSignalMagnitude-mean()"       
[38] "TimeBodyAccelerationJerkSignalMagnitude-std()"        
[39] "TimeBodyGyroscopeMagnitude-mean()"                    
[40] "TimeBodyGyroscopeMagnitude-std()"                     
[41] "TimeBodyGyroscopeJerkSignalMagnitude-mean()"          
[42] "TimeBodyGyroscopeJerkSignalMagnitude-std()"           
[43] "FastFourierBodyAcceleration-mean()-X"                 
[44] "FastFourierBodyAcceleration-mean()-Y"                 
[45] "FastFourierBodyAcceleration-mean()-Z"                 
[46] "FastFourierBodyAcceleration-std()-X"                  
[47] "FastFourierBodyAcceleration-std()-Y"                  
[48] "FastFourierBodyAcceleration-std()-Z"                  
[49] "FastFourierBodyAccelerationJerkSignal-mean()-X"       
[50] "FastFourierBodyAccelerationJerkSignal-mean()-Y"       
[51] "FastFourierBodyAccelerationJerkSignal-mean()-Z"       
[52] "FastFourierBodyAccelerationJerkSignal-std()-X"        
[53] "FastFourierBodyAccelerationJerkSignal-std()-Y"        
[54] "FastFourierBodyAccelerationJerkSignal-std()-Z"        
[55] "FastFourierBodyGyroscope-mean()-X"                    
[56] "FastFourierBodyGyroscope-mean()-Y"                    
[57] "FastFourierBodyGyroscope-mean()-Z"                    
[58] "FastFourierBodyGyroscope-std()-X"                     
[59] "FastFourierBodyGyroscope-std()-Y"                     
[60] "FastFourierBodyGyroscope-std()-Z"                     
[61] "FastFourierBodyAccelerationMagnitude-mean()"          
[62] "FastFourierBodyAccelerationMagnitude-std()"           
[63] "FastFourierBodyAccelerationJerkSignalMagnitude-mean()"
[64] "FastFourierBodyAccelerationJerkSignalMagnitude-std()" 
[65] "FastFourierBodyGyroscopeMagnitude-mean()"             
[66] "FastFourierBodyGyroscopeMagnitude-std()"              
[67] "FastFourierBodyGyroscopeJerkSignalMagnitude-mean()"   
[68] "FastFourierBodyGyroscopeJerkSignalMagnitude-std()"   


##Units
The data has been normalized. This means the units have checked each other and the values don't have units.

##New file
And finally the script writes the new dataset as a text file with the name "newUCIHARdataset.txt" on the following location "./data/newUCIHARdataset.txt"


And that is it. Many thanks to everyone at Coursera forums and StackOverflow.

I hope this makes sense to you reading this! 


-SevenWatch
