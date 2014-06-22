Codebook
========
Codebook was generated on 2014-06-22 18:10:32. See `run_analysis.R` for details on dataset creation.

Variable list and descriptions
------------------------------

Variable name    | Description
-----------------|------------
subject          | ID the subject who performed the activity for each window sample. Its range is from 1 to 30.
activity         | Activity name
featDomain       | Feature: Time domain signal or frequency domain signal (Time or Freq)
featInstrument   | Feature: Measuring instrument (Accelerometer or Gyroscope)
featAcceleration | Feature: Acceleration signal (Body or Gravity)
featVariable     | Feature: Variable (Mean or SD)
featJerk         | Feature: Jerk signal
featMagnitude    | Feature: Magnitude of the signals calculated using the Euclidean norm
featAxis         | Feature: 3-axial signals in the X, Y and Z directions (X, Y, or Z)
featCount        | Feature: Count of data points used to compute `average`
featAverage      | Feature: Average of each variable for each activity and each subject

Dataset structure
-----------------


```r
dtTidy <- read.table("TidyDataset.txt", header = TRUE)
str(dtTidy)
```

```
## 'data.frame':	11880 obs. of  11 variables:
##  $ subject         : int  1 1 1 1 1 1 1 1 1 1 ...
##  $ activity        : Factor w/ 6 levels "LAYING","SITTING",..: 1 1 1 1 1 1 1 1 1 1 ...
##  $ featDomain      : Factor w/ 2 levels "Freq","Time": 2 2 2 2 2 2 2 2 2 2 ...
##  $ featAcceleration: Factor w/ 2 levels "Body","Gravity": NA NA NA NA NA NA NA NA NA NA ...
##  $ featInstrument  : Factor w/ 2 levels "Accelerometer",..: 2 2 2 2 2 2 2 2 2 2 ...
##  $ featJerk        : Factor w/ 1 level "Jerk": NA NA NA NA NA NA NA NA 1 1 ...
##  $ featMagnitude   : Factor w/ 1 level "Magnitude": NA NA NA NA NA NA 1 1 NA NA ...
##  $ featVariable    : Factor w/ 2 levels "Mean","SD": 1 1 1 2 2 2 1 2 1 1 ...
##  $ featAxis        : Factor w/ 3 levels "X","Y","Z": 1 2 3 1 2 3 NA NA 1 2 ...
##  $ count           : int  50 50 50 50 50 50 50 50 50 50 ...
##  $ average         : num  -0.0166 -0.0645 0.1487 -0.8735 -0.9511 ...
```

Show a few rows of the dataset
------------------------------


```r
head(dtTidy, n = 20)
```

```
##    subject activity featDomain featAcceleration featInstrument featJerk
## 1        1   LAYING       Time             <NA>      Gyroscope     <NA>
## 2        1   LAYING       Time             <NA>      Gyroscope     <NA>
## 3        1   LAYING       Time             <NA>      Gyroscope     <NA>
## 4        1   LAYING       Time             <NA>      Gyroscope     <NA>
## 5        1   LAYING       Time             <NA>      Gyroscope     <NA>
## 6        1   LAYING       Time             <NA>      Gyroscope     <NA>
## 7        1   LAYING       Time             <NA>      Gyroscope     <NA>
## 8        1   LAYING       Time             <NA>      Gyroscope     <NA>
## 9        1   LAYING       Time             <NA>      Gyroscope     Jerk
## 10       1   LAYING       Time             <NA>      Gyroscope     Jerk
## 11       1   LAYING       Time             <NA>      Gyroscope     Jerk
## 12       1   LAYING       Time             <NA>      Gyroscope     Jerk
## 13       1   LAYING       Time             <NA>      Gyroscope     Jerk
## 14       1   LAYING       Time             <NA>      Gyroscope     Jerk
## 15       1   LAYING       Time             <NA>      Gyroscope     Jerk
## 16       1   LAYING       Time             <NA>      Gyroscope     Jerk
## 17       1   LAYING       Time             Body  Accelerometer     <NA>
## 18       1   LAYING       Time             Body  Accelerometer     <NA>
## 19       1   LAYING       Time             Body  Accelerometer     <NA>
## 20       1   LAYING       Time             Body  Accelerometer     <NA>
##    featMagnitude featVariable featAxis count  average
## 1           <NA>         Mean        X    50 -0.01655
## 2           <NA>         Mean        Y    50 -0.06449
## 3           <NA>         Mean        Z    50  0.14869
## 4           <NA>           SD        X    50 -0.87354
## 5           <NA>           SD        Y    50 -0.95109
## 6           <NA>           SD        Z    50 -0.90828
## 7      Magnitude         Mean     <NA>    50 -0.87476
## 8      Magnitude           SD     <NA>    50 -0.81901
## 9           <NA>         Mean        X    50 -0.10727
## 10          <NA>         Mean        Y    50 -0.04152
## 11          <NA>         Mean        Z    50 -0.07405
## 12          <NA>           SD        X    50 -0.91861
## 13          <NA>           SD        Y    50 -0.96791
## 14          <NA>           SD        Z    50 -0.95779
## 15     Magnitude         Mean     <NA>    50 -0.96346
## 16     Magnitude           SD     <NA>    50 -0.93584
## 17          <NA>         Mean        X    50  0.22160
## 18          <NA>         Mean        Y    50 -0.04051
## 19          <NA>         Mean        Z    50 -0.11320
## 20          <NA>           SD        X    50 -0.92806
```

Summary of variables
--------------------


```r
summary(dtTidy)
```

```
##     subject                   activity    featDomain  featAcceleration
##  Min.   : 1.0   LAYING            :1980   Freq:4680   Body   :5760    
##  1st Qu.: 8.0   SITTING           :1980   Time:7200   Gravity:1440    
##  Median :15.5   STANDING          :1980               NA's   :4680    
##  Mean   :15.5   WALKING           :1980                               
##  3rd Qu.:23.0   WALKING_DOWNSTAIRS:1980                               
##  Max.   :30.0   WALKING_UPSTAIRS  :1980                               
##        featInstrument featJerk      featMagnitude  featVariable
##  Accelerometer:7200   Jerk:4680   Magnitude:3240   Mean:5940   
##  Gyroscope    :4680   NA's:7200   NA's     :8640   SD  :5940   
##                                                                
##                                                                
##                                                                
##                                                                
##  featAxis        count         average       
##  X   :2880   Min.   :36.0   Min.   :-0.9977  
##  Y   :2880   1st Qu.:49.0   1st Qu.:-0.9621  
##  Z   :2880   Median :54.5   Median :-0.4699  
##  NA's:3240   Mean   :57.2   Mean   :-0.4844  
##              3rd Qu.:63.2   3rd Qu.:-0.0784  
##              Max.   :95.0   Max.   : 0.9745
```
