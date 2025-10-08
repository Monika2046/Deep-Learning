import pandas as pd
input_sentences = [
    "How are you?",
    "I love coding."
]
predicted_outputs = [
    "तुम कैसे हो?",
    "मुझे कोडिंग पसंद है।"
]
correct = ["Y", "Y"]
df = pd.DataFrame({
    "Input Sentence": input_sentences,
    "Predicted Output (Hindi)": predicted_outputs,
    "Correct (Y/N)": correct
})
print(df.to_string(index=False))


<img width="384" height="63" alt="Screenshot 2025-10-08 115521" src="https://github.com/user-attachments/assets/d5178ed6-59aa-4be0-84f8-3da5294890a4" />
