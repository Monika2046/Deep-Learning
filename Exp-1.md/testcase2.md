import numpy as np

class Perceptron:
    def __init__(self, input_size, learning_rate=0.1):
        self.weights = np.zeros(input_size + 1)  # +1 for bias
        self.learning_rate = learning_rate
    
    def activation(self, x):
        return 1 if x >= 0 else 0
    
    def predict(self, x):
        # Add bias input 1
        x = np.insert(x, 0, 1)
        weighted_sum = np.dot(self.weights, x)
        return self.activation(weighted_sum)
    
    def train(self, X, Y, epochs=10):
        for _ in range(epochs):
            for x, y in zip(X, Y):
                prediction = self.predict(x)
                error = y - prediction
                x = np.insert(x, 0, 1)
                self.weights += self.learning_rate * error * x

X = np.array([
    [0, 0],
    [0, 1],
    [1, 0],
    [1, 1]
])

Y = np.array([0, 1, 1, 0])


perceptron = Perceptron(input_size=2)


perceptron.train(X, Y, epochs=10)

print("Perceptron predictions on XOR inputs:")
for x, y in zip(X, Y):
    pred = perceptron.predict(x)
    correctness = "Correct" if pred == y else "May fail"
    print(f"Input: {x} | Actual: {y} | Predicted: {pred} | {correctness}")
<img width="465" height="600" alt="DL2(1)" src="https://github.com/user-attachments/assets/0df3166c-0c48-480f-b32f-91edae841bd5" />
