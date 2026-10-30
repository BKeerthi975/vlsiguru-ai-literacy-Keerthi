# Reflection

**1. Most important difference between traditional ML and deep learning?**
In traditional ML, engineers design the features and the model learns from them. In deep learning, the network
learns its own features from raw data such as pixels, which helps with complex inputs but needs much more data
and compute, and is harder to explain.

**2. How does data preparation affect what a network can learn?**
The network only sees the numbers I give it. Resizing, cleaning and normalisation decide what it can compare,
and wrong labels, duplicates or too few examples of a class directly limit what it can learn or can be trusted to do.

**3. What happens inside a network when it learns?**
It makes a prediction with its current weights, a loss measures the error, backpropagation works out how much each
weight contributed, and gradient descent adjusts the weights a little. Repeating this over many epochs reduces the loss.

**4. What did my experiment reveal about model complexity?**
Adding neurons helped a lot at first: a 4-neuron network solved the circle problem that a 1-neuron network could not
(test loss 0.422 down to 0.017). But a big network on noisy data with little training data showed a gap between
training loss (0.256) and test loss (0.453), so more complexity does not always help.

**5. One technical claim I verified:**
I cross-checked the share of normal wafers in the WM-811K labelled data. One paper said about 85% and another said 18.2%.
Adding the class counts in the second paper (25,519 defect examples out of 172,950) gave about 85% normal, so the
18.2% figure looks inconsistent. Sources can disagree, so I check numbers against each other.

**6. What remains unclear?**
How to choose the number of layers and neurons for a real problem without just trying many options, and how
to be sure that a model that works on one fab's data will work after the process changes.

**7. Question for the Saturday masterclass:**
How do engineers monitor a deployed defect-classification model for drift, and how do they decide when to
retrain it?
