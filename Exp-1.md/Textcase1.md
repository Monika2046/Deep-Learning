import numpy as np
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

X = np.array([[0, 0], [0, 1], [1, 0], [1, 1]])
Y = np.array([[0], [1], [1], [0]])

model = Sequential()
model.add(Dense(4, input_dim=2, activation='relu'))
model.add(Dense(1, activation='sigmoid'))


model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])


model.fit(X, Y, epochs=1000, verbose=0)


predictions = model.predict(X)
print("Predictions:", np.round(predictions).astype(int))

<img width="1540" height="634" alt="DL1 T" src="https://github.com/user-attachments/assets/77e96312-fc56-4ad9-8b30-1a31d3d2f1ac" />



