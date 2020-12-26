# Language identification with character-lstm based embeddings

Link to github repo: https://github.com/atharva-naik/langid

## Task:

Language identification for a written document

## Dataset:

Europarl v7 dataset (size 1.5 GB) is used. It has 21 languages.

For the task following two subsets are used (separately)

Sentences in following eight languages are used: _Spanish_, _German_, _Italian_, _French_, _Portugese_, _English_, _Dutch_, _Danish_

### 1. **first 125,000 sentences of eight languages**

The first 125,000 sentences of each language are used, so in total 1,000,000 sentences

The train : validation : test distribution is 80% : 10% : 10%

test set class distribution {'Spanish': 12575, 'German': 12523, 'Italian': 12434, 'French': 12722, 'Portugese': 12500, 'English': 12280, 'Dutch': 12474, 'Danish': 12492}

### 2. **first 10,000 sentences of eight languages**

The first 10,000 sentences of each language are used, so in total 80,000 sentences

The train : validation : test distribution is 80% : 10% : 10%

test set class distribution {'Spanish': 1020, 'Italian': 981, 'French': 974, 'Portugese': 1022, 'Dutch': 963, 'English': 965, 'German': 1048, 'Danish': 1027}

## Model:

1. After the character set (a vocabulary of characters) is determined for the dataset.

2. 100 dimensional vectors are randomly initialized for each character.

3. The embedding for each word is then calculated by using an LSTM, and choosing the final hidden state.

4. The embeddings of each word are then max pooled along each of the 50 dimensions of the hidden layer.

5. Then a linear layer transforms it to 8 classes, coupled with a softmax layer to get probabilities.

6. The first subset requires nearly 5 hours to train for 5 epochs, the second subset resuqires almost 25-30 minutes for 5 epochs
   The model is implemented in pytorch

## Environment:

The model is trained in google vocab with a GPU hardware acclerator
Minimal requirements in: requirements.in
All packages installed in the colab notebook are given in: requirements.txt

## Results

The results of the charLSTM classifier approach for the 2 subsets are stated below

### first 125,000 sentences of eight languages

**accuracy** = 98.28%

**f1-micro** = 98.28%

**f1-macro** = 98.27959967758044%

**f1-weighted** = 98.2794312965243%

class wise accuracies are:

_Spanish_: 98.79644588045234%

_German_: 98.16681215776526%

_Italian_: 97.92299089311392%

_French_: 98.67685279987398%

_Portugese_: 96.94271531006224%

_English_: 97.97659678205754%

_Dutch_: 98.36237495966441%

_Danish_: 99.4198694706309%

### first 10,000 sentences of eight languages

**accuracy** = 95.875%

**f1-micro** = 95.875%

**f1-macro** = 95.90623350666452%

**f1-weighted** = 95.86089203953024%

class wise accuracies are:

_Spanish_: 96.07250755287009%

_Italian_: 93.78698224852072%

_French_: 97.00103412616339%

_Portugese_: 96.79037111334003%

_Dutch_: 98.69989165763813%

_English_: 97.97872340425532%

_German_: 90.04366812227073%

_Danish_: 97.84524975514202%
