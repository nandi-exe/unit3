# Quiz 45

## UML Diagram

![Screenshot 2025-02-24 at 10 40 02 PM](https://github.com/user-attachments/assets/36aecefb-834f-4248-ab8d-ec8952c188a8)

## Code

```

class WordCounter:
    def __init__(self, text):
        self.text = text
        self.word_counts = {}

    def process_text(self):
        words = self.text.lower().split()
        for word in words:
            word = word.strip(".,!?;:")  # Remove punctuation
            if word in self.word_counts:
                self.word_counts[word] += 1
            else:
                self.word_counts[word] = 1
        
        for word, count in sorted(self.word_counts.items(), key=lambda x: x[1], reverse=True):
            print(f"{word}: {count}")

# Example usage
text = "This is a sample text. It contains some words that will be counted."
counter = WordCounter(text)
counter.process_text()

```
## Proof of Work

![image](https://github.com/user-attachments/assets/f92aed35-e8a5-47a7-8e86-512e7937dc7c)
