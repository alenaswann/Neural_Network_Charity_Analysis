# Neural Network Charity Analysis

----------

## Overview

###  The purpose of this analysis is to build a binary classifier that is capable of predicting whether applicant organization will be successful if they are funded by the  Alphabet Soup foundation. This is accomplished with a CSV of metadata on 34,000 organizations previously funded by Alphabet Soup which is processed and analyzed with a neural network model to make successful outcome predictions.

## Results

### Data Preprocessing
- **Target Variable**: IS_SUCCESSFUL (whether or not the invested money was used effectively)
- **Feature variables**:
	- APPLICATION_TYPE (Alphabet Soup application type) - binned into 9 values
	- AFFILIATION (Affiliated sector of industry)
	- CLASSIFICATION (Government organization classification) - binned into 6 values
	- USE_CASE (Use case for funding)
	- ORGANIZATION (Organization type)
	- STATUS (Active status)
	- INCOME_AMT (Income classification)
	- SPECIAL_CONSIDERATIONS (Special consideration for application)
	- ASK_AMT (Funding amount requested)
- **Removed variables**:
	- EIN (Identification number)
	- NAME (Name of organization)

### Compiling, Training, and Evaluating the Model

**Keras Sequential Model Details**:

- 2 hidden layers
	- 1st layer: 80 neurons, relu activation function
	- 2nd layer: 30 neurons, relu activation function
- Output layer: 1 neuron, sigmoid activation function

This model could not achieve the target model performance (>75%), only reaching an accuracy of **72.8%**.

To attempt to increase model performance, I tried several optimization approaches:

- *Attempt 1*: Removed an additional feature from the input data (INCOME_AMT) which resulted in an accuracy of **72.7%**.

- *Attempt 2*: Attempt 1 steps AND added additional neurons and a third hidden layer:
	- 1st layer: 100 neurons, relu activation function
	- 2nd layer: 45 neurons, relu activation function
	- 3nd layer: 10 neurons, relu activation function
	- Output layer: 1 neuron, sigmoid activation function

	This resulted in a model accuracy of **72.8%**.
- *Attempt 3*: Attempt 1 & 2 steps AND  tried different activation functions:
	- 1st layer: 100 neurons, tanh activation function
	- 2nd layer: 45 neurons, tanh activation function
	- 3nd layer: 10 neurons, relu activation function
	- Output layer: 1 neuron, sigmoid activation function
	
	This still resulted in a model accuracy of **72.8%**.
	
## Summary

Overall, my attempts to optimize the model failed to improve the accuracy score, but maintained the accuracy from its initial build. 72% is not ideal but is an acceptable starting point in evaluating potential investments. Still, aiming to optimize the model to perform about 75% accuracy would make the the model more reliable and useful when it comes to financial decision-making. Additional attempts at optimization could include eliminating other features that may make the data noisy, or perhaps bucketing the ASK_AMT column and running several models for each of the different cost categories. 

Another potential model to look into is PyTorch as it can handle larger datasets more easily and runs faster than Keras while still maintaining flexibility and debugging capabilities.