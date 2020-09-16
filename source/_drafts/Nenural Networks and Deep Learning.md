

# Active Recall



## Programming Assignments



### Python Basics with numpy

**What you need to remember:**

- np.exp(x) works for any np.array x and applies the exponential function to every coordinate
- the sigmoid function and its gradient
- image2vector is commonly used in deep learning
- np.reshape is widely used. In the future, you'll see that keeping your matrix/vector dimensions straight will go toward eliminating a lot of bugs. 
- numpy has efficient built-in functions
- broadcasting is extremely useful

**What to remember:**
- Vectorization is very important in deep learning. It provides computational efficiency and clarity.
- You have reviewed the L1 and L2 loss.
- You are familiar with many numpy functions such as np.sum, np.dot, np.multiply, np.maximum, etc...



### Logistic Regression with a Neural Network mindset

**What you need to remember:**

Common steps for pre-processing a new dataset are:
- Figure out the dimensions and shapes of the problem (m_train, m_test, num_px, ...)
- Reshape the datasets such that each example is now a vector of size (num_px \* num_px \* 3, 1)
- "Standardize" the data

**Logistic Loss**

**What to remember:** You've implemented several functions that:

Initialize (w,b)Optimize the loss iteratively to learn parameters (w,b):computing the cost and its gradientupdating the parameters using gradient descentUse the learned (w,b) to predict the labels for a given set of examples

**What to remember from this assignment:**

Preprocessing the dataset is important.You implemented each function separately: initialize(), propagate(), optimize(). Then you built a model().Tuning the learning rate (which is an example of a "hyperparameter") can make a big difference to the algorithm. You will see more examples of this later in this course!