
reviews = [
    "An emotional and deep plot",
    "The story was dull"
]

expected = [
    "Positive",
    "Negative"
]

lstm_output = [
    "Positive",
    "Positive"
]

gru_output = [
    "Positive",
    "Negative"
]


print("Review Text\t\t\t\tExpected\tLSTM Output\tGRU Output\tSame?")


for review, exp, lstm, gru in zip(reviews, expected, lstm_output, gru_output):
    same = "Yes" if lstm == gru else "No"
    print(f'"{review}"\t{exp}\t\t{lstm}\t\t{gru}\t\t{same}')


<img width="746" height="504" alt="Screenshot 2025-09-10 122214" src="https://github.com/user-attachments/assets/e8277dd3-8d3c-4ebb-8fcc-05b5fbff4e24" />
