# Assignment 1

In this assignment, you will progressively build a sentiment classifier of increasing complexity.

Part 1 will be done in class. Part 2 is the actual assignment that will be graded. 


## Part 1

Here, you will build a rule-based sentiment classifier. 

Download Data from [here](./data/SST-2). The directory contains `train.tsv`,  `valid.tsv` and `test.tsv` files denoting the train, validation and test splits of the data.

Implement the following methods:

1. `load_data(filename) -> tuple[list[str], list[int]]`
Read the provided file and return a tuple of two elements. The first element is a list of reviews and the second is the list of corresponding sentiment label.
2. `extract_features(sentence) -> dict[str, int]`
Given a sentence, return a dict containing two keys and their corresponding values. `num_positive_words` and `num_negative_words`. 
3. `classify(sentence) -> int`
Given a sentence, use the `extract_features` method and based on the returned counts, assign a label to the sentence.
4. `evaluate(predictions, labels) -> float`
Compute accuracy given the predicted label (obtained by calling the `classify` method) and the original gold label (obtained from reading the original data files). 
5. `analysis(sentences, predictions, labels) -> list[str]`
Use the predictions and gold labels to find reviews for which your classifier makes incorrect predictions. Can you modify `extract_features` to reduce the number of errors and improve accuracy?
6. `main() -> tuple[float, list[str]]`
Implement the main method that takes in the train and validation splits of the data and returns the accuracy and list of reviews that have incorrect predictions. 

NOTE: Do not `evaluate` or look at the `test.tsv` unless you have finalized with your classifier. 

## Part 2
In the second part, you are going to use logistics regression(ML-based) sentiment classifier.
You still use `train.tsv`, `valid.tsv` and  `test.tsv` files to train, validate and test your classifier.

1. Preprocess all text and sentences in `train.tsv` following the common text processing pipeline of your choice(e.g: text normalization, puctuation and stop words removal, lowercase,  lemmatization and tokenization etc.) Build a dictionary of vocabularies using the words appear in training set. For words not appeared in the dictionary, use a special token '<unk>' to replace. Apply the same processing pipeline to validation and test set. 
2. Represent each sentence using bag-of-words representation. Write a dataset and dataloader(batched data) to iterate through the whole dataset.
3. Train a linear classifier using Deep Learning Frameworks of your choice. For example, in PyTorch, you need to  define the network(nn.Linear), loss function(nn.CrossEntropy). And train the network using back propagation(define optimizer=torch.optim.Adam.., opt.zero_grad(), net.backward(), opt.step()...)). Perform validation every epoches, and select the best model to save. For Pytorch, you can check tutorials(https://pytorch.org/tutorials/beginner/basics/intro.html).
4. Evaluation: Define the metrics, show your classification accuracy, precision and recall on validation set and test set.

  
## Part 3
In this part, instead of representing your sentence using bag of words representation. We are going to use pretrained word vectors(Word2Vec, GLoVe etc). Load these pretrained embedding vectors, for example, you can find GloVe here at https://nlp.stanford.edu/projects/glove/ and download them. Get vectors for all words in your dictionary(defined in Part 2). Represent each sentence with sum of the word vectors. And apply a linear layer on top of the sentence representation and perform logitstic regression. The other part should be the same as part 2.
  
  
