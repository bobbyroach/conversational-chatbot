## Turn-based Conversational Chatbot from Scratch with Tensorflow

### Data 
For this project, I used a combination of four different dialog datasets: 
1. Cornell movie dialog corpus: https://www.kaggle.com/datasets/Cornell-University/movie-dialog-corpus
2. Daily dialog corpus: https://www.kaggle.com/datasets/thedevastator/dailydialog-unlock-the-conversation-potential-in
3. Human conversation training corpus: https://www.kaggle.com/datasets/projjal1/human-conversation-training-data/data
4. NPR interview recordings: https://www.kaggle.com/datasets/shuyangli94/interview-npr-media-dialog-transcripts

From all of these datasets, I took every sentence that had a response in the conversation. In other words, if the conversation had one more line of text after a certain sentence, I added that sentence to a list. Making the list into a Pandas DataFrame, where each sentence from the dataset was a row, I gave each row a response value, which is the next line in the conversation. This way, the machine learning model trains on the response to every sentence spoken in the datasets. 

### Preprocessing

To preprocess the data, I converted it all to lower case, mapped contraction words to their multi-word format, got rid of numbers and punctuation, and used lemmatization. After this, I used a counter function to count the appearance of every word and then remove words that appeared less than 6 times in the corpus to decrease the vocabulary size significantly. After that, I dropped rows with null values and removed lines over 40 tokens long. 

### Model and Training 

To prepare the data for the model, I added start and end tokens at the end of the response values, fit tokenizers on the input and output data, and then tokenized and padded it. After that, I split it into training and validation data. To help the model learn the relationships between words, I used pre-trained GloVe embeddings. 

For the model, I used a keras encoder and decorder sequential model. Both the encoder and decorder models have encoding layers, for which I used pre-trained word embeddings, and lstm layers. Additionally, the decoder has a dense layer which produces the output sequence. Then, I compiled it using RMSprop for an optimizer and sparse categorical crossentropy for a loss function. I then trained the model in batches of 50 for 50 epochs, using an early stop callback to return the best model possible. 

### Results

Here's a conversation with the bot: 

User: hi
Bot: hi 
 
User: hello
Bot: hello 
 
User: what is up
Bot: nothing much what is going on 
 
User: what up dude
Bot: well i am going to be back
 
User: i love you
Bot: i love you too 
 
User: aww thanks
Bot: i am not sure i am not sure
 
User: thank you
Bot: i am so happy for you
 
User: happy for me?
Bot: i am not sure i am not sure 
 
User: not sure about what
Bot: i am not sure
 
User: well bye now
Bot: i am not not sure i am not sure

-----------------------------------
 
This model definitely shows some promise, as it can correctly respond to some basic phrases, like "I love you" and "what is up." Even when it responds incorrectly, the sentences are still comprehensive, which is good. Also, when it doesn't know how to respond to a statement, it does a good job of saying that it is not sure

This model's performance can only be increased in a few ways. Increasing the training data size and making the model's architecture more complex are the best methods of doing so. Unfortunately, adding to the model's architecture with only one more LSTM layer in the encoder and decoder causes the training time to increase almost tenfold. Also, increasing the training data size has diminishing returns on the increase of the model's performance, requiring me to significantly increase the amount of data to see any significant improvement. 
 
 
 
 
