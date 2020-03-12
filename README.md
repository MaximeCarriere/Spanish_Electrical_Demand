# Demand
## Dataset
 
The dataset is the hourly demand of electricity for Spain from the 01/01/2018 to the 31/12/2019. The dataset is split into a training dataset and a test dataset at 66% of the entire dataset.
 
![image](https://media.github.tools.digital.engie.com/user/2475/files/b51ecd80-5ccc-11ea-951b-02b1cf53d936)
 
 
 
## Benchmarking for different types of neural networks
 
All these neural networks use the current/previous week to predict the hourly demand.
 
Inputs:
- 168 (24 hours * 7 days)
 
Outputs:
- 168 (24 hours * 7 days)
 
### Simple Neural Network: the so-called Multilayer Perceptron
 
Parameters:
- 1 Inputs layer of 168 nodes
- 1 Hidden layer of 168 nodes
- 1 Output layer of 168 node
- Batch Size: 150
- Loss function: MSE
- Optimizer: Adam
 
 
![MLP](https://media.github.tools.digital.engie.com/user/2475/files/ad9bb900-6470-11ea-94ca-20b0275eef88)
 
 
### Recurrent Neural Network
 
The RNN is different from the previous feedforward neural network by the connections between nodes that form a directed graph along a temporal sequence. This allows it to exhibit temporal dynamic behavior.
 
Parameters:
- 1 Inputs layer of 168 nodes
- 1 Hidden layer of 168 nodes
- 1 Output layer of 168 node
- Batch Size: 150
- Loss function: MSE
- Optimizer: Adam
 
![RNN_drawing](https://media.github.tools.digital.engie.com/user/2475/files/7b3e8b80-6471-11ea-8910-ee4042fb1102)
 
 
### Long Short-Term-Memory Neural Network
 
The LSTM is different from the previous RNN by the cell that keeps in information from the sequence in memory. A common LSTM unit is composed of a cell, an input gate, an output gate and a forget gate. The cell remembers values over arbitrary time intervals and the three gates regulate the flow of information into and out of the cell.
 
Parameters:
- 1 Inputs layer of 168 nodes
- 1 Hidden layer of 168 nodes
- 1 Output layer of 168 node
- Batch Size: 150
- Loss function: MSE
- Optimizer: Adam
 
![LSTM_drawing](https://media.github.tools.digital.engie.com/user/2475/files/b55c5d00-6472-11ea-8e3a-6c17266262f7)
 
## Training comparison
 
Now it is time to do some benchmarking to choose the best Neural Network and then to improve it by doing a parameter study.
 
### Loss Function
 
![Loss_Drawing](https://media.github.tools.digital.engie.com/user/2475/files/e473ce00-6474-11ea-96e9-37f33a8681fb)
 
All types of Neural Network converge extremely quickly to a low error. So fast, that is it almost impossible to compare which one is the best without doing a zoom. In the second graph (zoom of the last 50 epochs), it can be seen that the error for all neural networks are still decreasing. The LSTM seems to have a greater slope than the two other. Moreover, the LSTM has the lowest error, followed by the MLP and then the RNN. Thus, for a loss perspective the LSTM is the best.
 
### Accuracy
 
![Accuracy_drawing](https://media.github.tools.digital.engie.com/user/2475/files/56e5ad80-6477-11ea-8700-8f6942b6088c)
 
For the accuracy it is clear that the LSTM performs better than the two others.
 
 
### RMSE/MSE during training / test
 
![RMSE_MAE_comparison](https://media.github.tools.digital.engie.com/user/2475/files/8994a380-6481-11ea-853f-bbbce296a9d4)
 
RMSE = Root Mean Square Error (sensible to high error)
 
MSE = Mean Absolute Error (less sensible to high error)
 
Here again the LSTM model is the best for the training and test dataset. The scores of RMSE during the test for all models are relatively similar. This shows the importance of a second measure for the Error.
 
### Out of sample
 
 
![Out_of_sample_Drawing](https://media.github.tools.digital.engie.com/user/2475/files/8ef4ec80-6487-11ea-80e4-e190661320cb)
 
The models are now tested out of sample (input week of february 2020). All models perform quite well.
 
 
![Data_vs_Prediction](https://media.github.tools.digital.engie.com/user/2475/files/36265380-6489-11ea-9a38-1e47a8bd036a)
 
However when the error (Data vs Prediction) is plotted, the MLP is the best. More research is needed to find the best model.
 
