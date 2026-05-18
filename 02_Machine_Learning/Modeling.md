# Modeling

Modeling is the art of finding the correct algorithm that describes how known input data can predict unknown output values. 

This is the most difficult part of the OSEMN workflow.

Some steps of this process are:
- Identify how you will evaluate the accuracy of a model (usually, a "cost" function)
- Select the data fields (known as **features**) that you will use in your model
- Split your data into different data sets (at least "**training**" and "**validation**" data)
- Use the training data to train different **algorithms** to predict the target unknown value based on the known input features
- Evaluate the performance of the model with the "unseen" validation data
- Select the model that **best** accomplishes the intended modeling goal. This often is the model which minimizes the cost function. However, you should consider other factors such as model training time, model complexity, future data availability and model explainability.