import nltk 
from keras.models import Model 
from keras.layers import Input, LSTM, Dense 
import numpy as np 
# Sample data 
input_texts = ['I love NLP', 'He plays football'] 
target_texts = [['PRON', 'VERB', 'NOUN'], ['PRON', 'VERB', 'NOUN']] 
# Tokenization (simplified for small dataset) 
word_vocab = sorted(set(word for sent in input_texts for word in sent.split())) 
tag_vocab = sorted(set(tag for tags in target_texts for tag in tags)) 
word2idx = {word: i+1 for i, word in enumerate(word_vocab)} 
tag2idx = {tag: i for i, tag in enumerate(tag_vocab)} 
encoder_input_data = np.array([[word2idx[word] for word in sent.split()] for sent 
in input_texts]) 
decoder_output_data = np.array([[tag2idx[tag] for tag in tags] for tags in 
target_texts]) 
# Model (simplified) 
encoder_inputs = Input(shape=(None,)) 
encoder = LSTM(64, return_state=True) 
encoder_outputs, state_h, state_c = encoder(encoder_inputs) 
decoder_inputs = Input(shape=(None,)) 
decoder_lstm = LSTM(64, return_sequences=True, return_state=True) 
decoder_outputs, _, _ = decoder_lstm(decoder_inputs, initial_state=[state_h, 
state_c]) 
decoder_dense = Dense(len(tag_vocab), activation='softmax') 
decoder_outputs = decoder_dense(decoder_outputs) 
model = Model([encoder_inputs, decoder_inputs], decoder_outputs) 
model.compile(optimizer='adam', loss='sparse_categorical_crossentropy', 
metrics=['accuracy']) 


<img width="570" height="245" alt="Screenshot 2025-10-08 105924" src="https://github.com/user-attachments/assets/926be181-00b0-43f9-b383-83741f9d5c5f" />
