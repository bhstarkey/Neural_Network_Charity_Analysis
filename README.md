## Purpose

As a company that helps fund and route donations to different charities, we were tasked with the job of deciphering which ones would use the money given to them effectively. In order to help predict which charities we should give money to, we built a neural network to help predict which charities and applications would effectively use the money that is given to them. 

## Results

### Data Processing

Looking at our initial dataset, the target variable is the column 'Is Successful', with that showing whether or not the money was used successfully. The features were all the other colmns in the dataset. EIN and Name could be excluded (especially EIN) because they are used just as identifiers, and could skew data, but they could be considered features. I dropped the EIN and Name column from every neural network I ran, except the last one, so that that wouldn't skew the data. 

### The Model

Initially, I only selected 2 layers to get a baseline of the data. It had 80 neurons in the first layer, and 30 in the second, with an activation function of relu. I chose 80 because the number of features we had was around 40, and 80 is 2 times that, which is suggested for optimization. I chose relu, because I have been impressed with it's ability to classify data playing with the tensorflow model; it seems to outpreform the other functions on some datasets. After creating my optimization Jupyter Notebook file, I ran it through the Keras tuner and gave it the option of the activation functions relu, sigmoid, and tanh, and a number of layers between 2 and 6, with nerons being inbetween 80 and 120 for the first layer, and 30 and 120 for the subsequent layers. After running that model, I built my nest neural network based on my 3 highest preformers. After still not seeing mark improvement in the loss metric and accuracy of the model, I added the name column back into the network, and built my final neural network. That one had 5 hidden layers, with 1200, 300, 100, 100, and 100 neurons respectively. It used the activation function relu, and went through 100 epochs. 

It wasn't until the name column was added back into the mix that I was able to get above 75% accuracy, and I have mixed feelings about that. While I see the value of having it in there, and having the model be able to see the history of each charity, it is still an identifier column, and we don't fully know whether or not it is being skewed by it.

## Summary

After optimizing the model, we would be able to predict about 805 of the time whether or not a charity would use the money given to them effectively. I would want to try the keras tuner again with the data, and see if I could get those metrics even higher, but then I would also be concerned about the model being overfit for the data. I would like to compare it to a random forest model, and compare how well it would classify the data compared to the neural network.

While we were able to get a reasonably high accuracy score, I feel the model is missing important data that would be able to indicate use of the allocated money, without using an identifier column. I would go back and try to get more data, and try the model again.
