# Financial fraud detection project

## To do:
- C1: Model development
- C2: Hard-decision threshold selection
- C3: Calibration
- Presentation: explain choices and results
- Individual reflection

## C1: Model development
Which one and why?: 
- My proposal is to first do binary classification using logistic regression. This is a simple, but effective model. It usually performs bad on complicated non-linear patterns, which might motivate more complex models such as gradient boosting . I think building from an "easy" model makes a more compelling story.

What information do we already have on the dataset that we might use to decide our starting point?
- How complex do we believe the dataset is?


### The training pipeline:
- Training set (80%), used to find the final hypothesis
- Validation set (20%), calculate validation error (squared error). Remember that: ![alt text](image.png)![alt text](image-1.png)
- Test set (Lampe does this, right?)

## How we sample our data
- stratified sampling

## Model 1: Logistic regression
- Motivation 
    - Outputs a probability (more suitable than binary classification) that a certain sample is fraudulent/legit.
    Still low overhead, robust and good generalization properties. 

- How to implement:
![alt text](images/image.png) (Learning from data, p. 95)
    - Optimize with  SGD or Adam?
        - I see that you chose LBFGS, I think that works well but we should motivate that choice. (supports L2 regularization)
    - Initialize weights independlty from a Normal distribution with zero mean and small variance is often good practice
        - I don't see what the weights are initialized with in your code
    - Termination
        - Now it is upper bounded by the number of iterations, however that means there is no guarantee of the quality of the final weights. Therefore we should also add a small lower bound for the size of the gradient (is this already implemented and I'm just blind?).
        ![alt text](images/image-1.png)

- Train/test on balanced dataset for exploratory work.

- Train/test on imbalanced dataset to tune hyperparameters
    - What are our hyperparameters

- Combat overfitting (when minimizing In-sample-error results in higher out-of-sample-error)
    - Regularization (weight decay, ![alt text](images/image-2.png)) is nescessarry due to the noisy structure of our dataset

## Model 2: Gradient boosting
- The most advaneced model, should 


Short discussion about why NN and random forest weren't chosen.


## Meeting on Wednedsday
- "The focus of the work is to develop and test one or two methods", you propose three, I think that's a a bit over the top

- I also think the code (the way it is now) hides many of the model choices that have been made.

- Change variable name from test_set to validation_set 

