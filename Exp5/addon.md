from keras.models import Sequential 
from keras.layers import Embedding, GRU, Dense 
model = Sequential([ 
Embedding(10000, 32, input_length=100), 
GRU(100), 
Dense(1, activation='sigmoid') 
]) 
model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy']) 
model.fit(X_train, y_train, epochs=5, batch_size=64, validation_split=0.2) 


<img width="1130" height="379" alt="Screenshot 2025-09-10 121103" src="https://github.com/user-attachments/assets/12f8e430-ceba-4bc5-8aa9-5a09045b87c9" />
