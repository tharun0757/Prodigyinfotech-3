text = """
Machine learning is the science of getting computers to act without being explicitly programmed.
In the past decade, machine learning has given us self-driving cars, speech recognition, effective web search,
and a vastly improved understanding of the human genome.
""
words = text.split()
import random
markov_chain = {}
for i in range(len(words) - 1):
    current_word = words[i]
    next_word = words[i + 1]
    if current_word not in markov_chain:
        markov_chain[current_word] = [] markov_chain[current_word].append(next_word)

def generate_text(chain, start_word, length=20):
    word = start_word
    result = [word]
    for _ in range(length):
        next_words = chain.get(word, None)
        if not next_words:
            break
        word = random.choice(next_words)
        result.append(word)
    return ' '.join(result)
print(generate_text(markov_chain, "machine"))
