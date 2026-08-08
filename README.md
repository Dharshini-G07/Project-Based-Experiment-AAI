<H3>Name : Priyadharshini G</H3>
<H3>REGISTER NO: 212224230209</H3>
<H3>DATE: 08.08.2026</H3>

<H1 Align="center">Facebook Sentiment Analysis Using Python</H1>

<H3>Objective:</H3>
To analyze Facebook posts and classify them as Positive, Negative, or Neutral using VADER Sentiment Analysis in Python.

<H3>Program:</H3>

```
import pandas as pd
import nltk
from nltk.sentiment.vader import SentimentIntensityAnalyzer

file = "FacebookPosts.xlsx"
xl = pd.ExcelFile(file)
df = xl.parse(xl.sheet_names[0])

dfs = list(df['Post'])

sid = SentimentIntensityAnalyzer()

for data in dfs:
    score = sid.polarity_scores(data)

    if score['compound'] >= 0.05:
        sentiment = "Positive"
    elif score['compound'] <= -0.05:
        sentiment = "Negative"
    else:
        sentiment = "Neutral"

    print(data, "->", sentiment)

positive = 0
negative = 0
neutral = 0

for data in dfs:
    score = sid.polarity_scores(data)

    if score['compound'] >= 0.05:
        positive += 1
    elif score['compound'] <= -0.05:
        negative += 1
    else:
        neutral += 1

print("Positive:", positive)
print("Negative:", negative)
print("Neutral:", neutral)

import matplotlib.pyplot as plt

labels = ['Positive', 'Negative', 'Neutral']
values = [positive, negative, neutral]

plt.bar(labels, values)
plt.xlabel('Sentiment')
plt.ylabel('Number of Posts')
plt.title('Facebook Sentiment Analysis')
plt.show()

```



<H3>Output:</H3>
<img width="406" height="173" alt="image" src="https://github.com/user-attachments/assets/16a3880c-fbc2-4da5-9b67-b1d8284ea402" />

<img width="151" height="78" alt="image" src="https://github.com/user-attachments/assets/5c6506d8-6aac-4409-beb0-728816655df3" />

<img width="568" height="475" alt="image" src="https://github.com/user-attachments/assets/0723f5f2-5f95-41f6-b6a5-32f930f5204b" />


<H3>Inference:</H3>
Through this project, I learned how to read data from an Excel file using Pandas and perform sentiment analysis using the VADER library in Python. I also learned how to classify Facebook posts into Positive, Negative, and Neutral sentiments using compound scores and visualize the results using a bar chart.
