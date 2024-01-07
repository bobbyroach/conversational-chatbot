## Turn-based Conversational Chatbot from Scratch with Tensorflow

### Data 
For this project, I used a combination of four different dialog datasets: 
1. Cornell movie dialog corpus: https://www.kaggle.com/datasets/Cornell-University/movie-dialog-corpus
2. Daily dialog corpus: https://www.kaggle.com/datasets/thedevastator/dailydialog-unlock-the-conversation-potential-in
3. Human conversation training corpus: https://www.kaggle.com/datasets/projjal1/human-conversation-training-data/data
4. NPR interview recordings: https://www.kaggle.com/datasets/shuyangli94/interview-npr-media-dialog-transcripts

From all of these datasets, I took every sentence that had a response in the conversation. In other words, if the conversation had one more line of text after a certain sentence, I added that sentence to a list. Making the list into a Pandas DataFrame, where each sentence from the dataset was a row, I gave each row a response value, which is the next line in the conversation. This way, the machine learning model trains on the response to every sentence spoken in the datasets. 

### Preprocessing

To preprocess the data, I converted it all to lower case, mapped contraction words to their multi-word format, got rid of numbers and punctuation, and used lemmatization. After this, I used a counter function to count the appearance of every word and then remove words that appeared less than 6 times in the corpus to decrease the vocabulary size significantly.


### Model and Training 



### Results
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 
 -
 ?
 ++
