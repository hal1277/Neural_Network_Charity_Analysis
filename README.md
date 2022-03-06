# Neural_Network_Charity_Analysis

## Overview of the Analysis

The purpose of this analysis was to help Alphabet Soup determine if an organization that requests funding from them will be successful in their work if given the funds.  Alphabet Soup is looking for a machine learning solution to automate the review process and provide a sufficient level of accuracy.  They have provided a dataset of 34,000 organizations that have received funding from Alphabet Soup to use for training the machine learning models.  

## Results

The first step in any machine learning endeavor is examing the data and performing pre-processing and then the model can be built and trained.  The following work details this process.  

1. First step is determing what is the target for the model.  in this case it was the "IS_SUCCESSFUL" column since the goal is to train the model to predict if an organziation would be successful in their work if Alphabet Soup were to give them funding. 

2. Second step is determing what variables are considered the features for the model.  Until actually running a model or doing further analysis on the data we cannot be certain which data is truly a feature but we can include what we believe could be important features.  In this case i've included:
    -application type
    -affiliation
    -use case
    -organization
    -status
    -income amount
    -special considerations
    -ask amount

 3. Thirdly anything not considered a feature or a target needed to be removed from the data set. This included the Name and EIN data columns.  

 4. After preparing the data for modeling the categorical data was encoded, the data was split into training and testing sets, and the data was scaled.  The intial model prepared consisted of an input layer with 44 dimensions since it was set equal to the number of columns of data.  There were two hidden layers and the first hidden layer had 80 neurons since the number of neurons should be set somewhere in the range of 2-3 times the number of dimensions.  The second hidden layer contains 30 neurons since the second layer is typically set smaller than the first hidden layer.  Activation on the hidden layers was set to relu since it effective for non-linear data and for either classification or regression.  The problem in this case is a classification one.  

 5. After running the model in its initial set up the desired accuracy level of 75% was not met - the intital model only acheived an accuracy of 72.5%

 6. Having not acheived the desired level of accuracy on the initial model set up additional attempts were made to improve on the accuracy.  I examined the data set more closely to see if any noisy variables might be affecting the models performance.  i made the decision to remove the column indicating the amount of funding asked for.  Almost all organizations ask for $5,000 and other amounts were just outliers.  Since there is essentially no variation in this column, apart from extreme outliers than can confuse models, it serves no useful purpose in terms of modeling which is why it has been removed. With this new further cleansed data set i tried the following 3 re-designs to try and improve the models performance.  

    a. I increased the number of neurons in each hidden layer so layer 1 went from 80 neurons to 160 and layer 2 went from 30 neurons to 60.  This did not improve the models performance appreciably - reaching only 72.6%

    b. I added an additional hidden layer so that the first layer had 80 neurons, second layer had 30 neurons, and third layer had 15 neurons.  This reduced the performanc of the model slightly to 72.5%.

    c. I changed the activation in the hidden layers from rely to sigmoid since sigmoid is good for classification problems.  This also did not improve the models performance appreciably - reaching only 72.7%.

## Summary

In light of the work above I conclude that this problem of predicting success of organizations after funding them is not predictable by neural networks to the level of accuracy needed - at least not with the features currently avaialble in the data set and the volume of data available.  However, this may still be a problem that can be solved by machine learning in another form.  I would recommend trying to solve this using the simpler random forest model to see if better results can be achieved.  Since random forest uses weak learner algorithms and consensus they can outperform neural networks on some problems.  Random forest is very well suited to tabular data which is the data available to Alphabet Soup.  Random Forest may also run faster since each of the neural network models took some time to compute.  