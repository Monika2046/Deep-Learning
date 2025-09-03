# Sample data
webcam_data = [
    {"Image": "Live Face 1", "Expected": "John", "Recognized": "John"},
    {"Image": "Live Face 2", "Expected": "Alice", "Recognized": "John"},
    {"Image": "Unknown", "Expected": "", "Recognized": "Unknown"}
]

# Evaluate correctness
for entry in webcam_data:
    expected = entry["Expected"]
    recognized = entry["Recognized"]
    correct = "Y" if expected == recognized else "N"
    entry["Correct"] = correct

# Display results
print(f"{'Webcam Image':<15} {'Expected Name':<15} {'Recognized Name':<17} {'Correct (Y/N)':<13}")
for entry in webcam_data:
    print(f"{entry['Image']:<15} {entry['Expected']:<15} {entry['Recognized']:<17} {entry['Correct']:<13}")

![Screenshot_3-9-2025_1181_colab research google com](https://github.com/user-attachments/assets/474e25a5-d945-4c20-8d16-a5b0bee9249f)
