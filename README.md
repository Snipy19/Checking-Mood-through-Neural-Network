# Checking-Mood-through-Neural-Network

from textblob import TextBlob
import numpy as np
import pandas

# Define sentiment analysis function
def analyze_sentiment(text):
    analysis = TextBlob(text)
    sentiment = analysis.sentiment.polarity
    if sentiment > 0:
        return "positive"
    elif sentiment < 0:
        return "negative"
    else:
        return "neutral"

# Define responses based on sentiment
positive_responses = ["I'm glad to hear that!", " happy for you!"]
negative_responses = ["I'm sorry.",  "I'm here to help if you need it."]
neutral_responses = [ "Interesting.", "Thanks for sharing."]

# Chatbot interaction
print("Welcome to the sentiment analysis chatbot!")
while True:
    user_input = input("\nEnter your thoughts or type 'exit' to quit: ")
    if user_input.lower() == "exit":
        break
    
    sentiment = analyze_sentiment(user_input)
    
    if sentiment == "positive":
        print(np.random.choice(positive_responses))
    elif sentiment == "negative":
        print(np.random.choice(negative_responses))
    else:
        print(np.random.choice(neutral_responses))
