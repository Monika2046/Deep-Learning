from keras.models import Sequential 
from keras.layers import Embedding, LSTM, Dense 
from keras.preprocessing.text import Tokenizer 
from keras.utils import pad_sequences, to_categorical 
# Assume 'corpus' contains cleaned Shakespeare text lines 
tokenizer = Tokenizer() 
tokenizer.fit_on_texts(corpus) 
total_words = len(tokenizer.word_index) + 1 
input_sequences = [] 
for line in corpus: 
token_list = tokenizer.texts_to_sequences([line])[0] 
for i in range(1, len(token_list)): 
n_gram_sequence = token_list[:i+1] 
input_sequences.append(n_gram_sequence) 
max_len = max([len(seq) for seq in input_sequences]) 
input_sequences = pad_sequences(input_sequences, maxlen=max_len, padding='pre') 
X, y = input_sequences[:,:-1], input_sequences[:,-1] 
y = to_categorical(y, num_classes=total_words) 
model = Sequential([ 
Embedding(total_words, 100, input_length=max_len-1), 
LSTM(150), 
Dense(total_words, activation='softmax') 
]) 
model.compile(loss='categorical_crossentropy', optimizer='adam', 
metrics=['accuracy']) 
model.fit(X, y, epochs=50, verbose=1)

![Screenshot_3-9-2025_9451_colab research google com](https://github.com/user-attachments/assets/0bfd7ce5-f903-4097-9768-5cdbadc292db)
