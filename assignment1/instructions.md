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