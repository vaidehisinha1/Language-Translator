# Language-Translator

The objective of the project is to implement language translation model aka machine translation for converting German to English (and vice versa).

For this, the data is a text file (.txt) of English-German sentence pairs of which I have used the first 50,000 sentence pairs to reduce the training time of the model.

Data : http://www.manythings.org/anki/

I went through the following steps for this project : 

1. Import the Required Libraries

2. Read the Data into the IDE

    a. Split the text into English-German pairs separated by ‘\n’.
    
    b. Text Cleaning - Get rid of punctuation marks and convert all sentences to lower case. 
    
    c. Text to Sequence Conversion - 'A Seq2Seq model requires that we convert both the input and the output sentences into integer sequences of fixed length.'  -  capture the lengths of all the sentences in two separate lists for English and German, respectively - the maximum length of the German sentences is 11 and that of the English phrases is 8. 
    
    d. Vectorize text data by using Keras’s Tokenizer () class. It will turn sentences into sequences of integers. After which, it can then pad those sequences with zeros to make all the sequences of the same length.
    
    
MODEL BUILDING

1. Split the data into train and test set for model training and evaluation, respectively.

2. Start off by defining  Seq2Seq model architecture:

    a. For the encoder, use an embedding layer and an LSTM layer.
    
    b. For the decoder, use another LSTM layer followed by a dense layer.
    
    
3. Use the RMSprop optimizer in this model as it’s usually a good choice when working with recurrent neural networks.

4. Use ‘sparse_categorical_crossentropy ‘as the loss function. This is because the function allows us to use the target sequence as is, instead of the one-hot encoded format. One-hot encoding the target sequences using such a huge vocabulary might consume our system’s entire memory.

5. Train model for 4 epochs and with a batch size of 512 with a validation split of 20%.

    a. 80% of the data will be used for training the model and the rest for evaluating it.
    

6. Also use the Model Checkpoint () function to save the model with the lowest validation loss.

7. Predictions that will be obtained will be sequences of integers. Convert these integers to their corresponding words.

8. Convert predictions into text (English).

9. Finally put the original English sentences in the test dataset and the predicted sentences in a data frame.

10. Randomly print some actual vs predicted instances to see how our model performs.
