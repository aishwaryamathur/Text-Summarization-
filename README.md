# Text-Summarization

## Datasets
### 1) Extractive Text Summarisation
- The  dataset  used  for  extractive  summarization  is BBC  News  Summarydataset  which contains news articles segregated into 5 categories namely, ‘Business’, ‘Entertainment’, ‘Politics’, ’Sport’ and ‘Tech’ and the summaries of each article. The dataset contains a 
total of 2,225 articles and summaries. It has 3 columns which are: title of article, article, and the summary. 

### 2) Abstractive Text Summarization
- The  dataset  used  for  abstractive  text  summarization  isCNN  DailyMail  News  Text Summarizationdataset. This dataset  is  from  Kaggle.  It  has  3  columns  which  are:  id, article, highlights. The id column is a character column, article column has text data which is  used  as  an  input  to  the  text  summarization  models  and  highlights  column  is  a  short summary of the articles which we will use to evaluate the performance of the model.

## Methods

### 1) Extractive Text Summarization 
The extractive text summarising approach entails extracting essential words from a source material and combining them to create a summary.The output of extractive summarization can be thought of as a subset of the input text that communicates the document's main idea and  emphasizes  its  key  points.  It  is  a  straightforward  model  because  it  employs  some method for rating the sentences in any text before ranking them and producing the results. This  method  works  by  identifying  important  text  passages,  removing  them,  and  then piecing them back together to produce a condensed version. They therefore only use phrase extraction from the source text. For extractive summarization, TextRank algorithm is used which is a graph-based ranking model for text processing, based on Google’s PageRankalgorithm, that finds the most relevant sentences in a text.For the project, the extractive summarization was performed on the BBC News Summary and the input news article category for the extractive summarization is taken from the user which  includes  Business,  Entertainment,  Politics,  Sports,  and  Tech.  After  choosing  the category, the article is split into sentences and the sentences were cleaned by performing methods like tokenization, conversion to lowercase, removing stop words and punctuation. The word vectors were obtained using GloVe global vectors and word embeddings were created. The first vectors (each of size 100 elements) for the constituent words in a sentence and  were  fetched  to  get  the  vector  for  the  sentence.The  sentence  vectors  were  formed using the word embeddings and the sentences were  compared with  each other to form a similarity matrix using cosine similarity. Similarity  scores between sentences were used to rank the sentences in the article and extract the most important points from the article 
to form a summary. The model was also implemented using Gensim library, which has an inbuild summarization method which takes the text and the ratio parameter which specifies the length of summary to be formed and gives the summary of the article. The extractive summarization model was evaluated by using ROGUE score metrics which works  by  comparing  the  automatically  produced  summary  using  the  model  against  the reference summaries present in the dataset. It is calculated using the number of overlapping words and the total words present in the reference summary. Rouge-1 score refers to the overlap of unigrams and Rouge-2 score refers to the bigrams between the summary  and reference  summary.  Rouge-L  score  measures  the  longest  matching  sequence  of  words using LCS (Longest Common Subsequence).

### 2) Abstractive Text Summarization

Transformers  provide  APIsand  tools  to  download  and  train  state  of  the  art  pretrained models. This reduces computational costs, carbon footprints and time to train a model from scratch.  These  models  support  various  tasks  such  as  text  classification,  named  entity recognition,  language  modelling,  summarization,  image  classification,  object  detection, audio speech recognition and video classification.For the project, we used Hugging Face’s pretrained transformer model. Transformersis a python library dedicated to supporting Transformer-based architecture and facilitating the distribution  of  pretrained  models.  At  its  core,  the  library  is  an  implementation  of  the Transformer which is designed for both research and production. The input text (the articles column from the dataset) was tokenized and then stop words and punctuations from the tokens were removed. On preliminary analysis, we noticed that words like ‘by’, ‘associated’, ‘press’, ‘published’ and ‘updated’appeared very frequently in  the  corpus,  so  we  decided  to  drop  these  words  too. The  words  in  the  corpus  were lemmatized and the input was converted to a string. The input was thus pre-processed and ready to be fed into the model.A function to generate summary was constructed. It counts the number of occurrencesof each word in the input text, gets the maximum number of occurrencessay dand divides this number dwith the value of occurrence of each word to get a score. These scores are then used to get a sentence scorefor each sentence in the text. Then a summarizer functionfrom the transformer library is called upon this text to generate a summary. The function also calculates the ROGUE score for the generated summary.
