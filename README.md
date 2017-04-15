# Deep-Lyrics
*Lyrics Generator aka Character-level Language Modeling with Multi-layer LSTM Recurrent Neural Network*

The goal of this project is to generate completely new original lyrics inspired by the work of any number of artists.

## Description
This repository contains 4 main components:
* A web parser to gather lyrics online
* A preprocessing program to transform the lyrics into a computation-friendly format
* A program to train a LSTM model to fit the data
* A sampling program to generate new lyrics based on the learned data

The Deep Learning algorithm is implemented and tested with [TensorFlow](https://www.tensorflow.org/) version *0.10.0rc0*.  
The parser is gathering lyrics from [songmeanings.com](http://songmeanings.com/) which does not provide any API to request data. Therefore, it is needed to manually find the IDs of the artists you want to get inspired from and pass them to the script. The intersting thing is that it does not matter if the artists you pick are related in style or not, the algorithm will learn from all of them; which can obviously lead to some weird results at times!

## Usage

```
# parse web pages to retrieve lyrics, concatenate them and save them locally in a single file
./gather.py --output_file data.txt --artists "artist_ID_1, artist_ID_2, artist_ID_3, artist_ID_4, artist_ID_5"

# create a vocabulary file containing a binary representation for each character
./preprocess.py --input_file data.txt

# train the LSTM model to fit the lyrics data
./train.py --training_file data.txt --vocabulary_file data.vocab --model_name lstm_regression_model

# generate new lyrics and save them in a file
./sample.py --model_name lstm_regression_model --vocabulary_file data.vocab --output_file sample.txt --seed "You are"
```

## Example
Example of lyrics generated with this code (slightly edited to fix typos).
The resulting text is understandable but does not make any sense at all, which is quite funny!

```
You are gonna take it
And you wanna feel right

The baby gone far, kiss in the rain, but you, back home
They'll never get back when you've go

So you have been work

They come back home
But hidden I can't be there
The baby give is all the give

There is no on the way mind
We clink to go do the back and long, come
```

^^^()()^^^