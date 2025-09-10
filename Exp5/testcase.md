reviews = [
    "I loved the movie, fantastic!",
    "Worst film ever, boring.",
    "It was okay, not great."
]

actual_sentiments = [
    "Positive",
    "Negative",
    "Neutral"
]

predicted_sentiments = [
    "Positive",
    "Negative",
    "Positive"
]


print("Review Text\t\t\t\tActual Sentiment\tPredicted Sentiment\tCorrect (Y/N)")


for review, actual, predicted in zip(reviews, actual_sentiments, predicted_sentiments):
    correct = "Y" if actual == predicted else "N"
    print(f'"{review}"\t{actual}\t\t\t{predicted}\t\t\t{correct}')

    <img width="873" height="563" alt="Screenshot 2025-09-10 121741" src="https://github.com/user-attachments/assets/684fcfc4-fc1b-4517-881d-828d13f850c0" />
