```python
import openai
openai.api_key = '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'
def get_completion(prompt, model="gpt-3.5-turbo"):
    messages = [{"role": "user", "content": prompt}]
    response = openai.ChatCompletion.create(
        model=model,
        messages=messages,
        temperature=0,
    )


    return response.choices[0].message["content"]
```


```python
text = f"""
Needed a nice lamp for my bedroom,and this one had \
additional storage and not too high of a price point. Got it fast. The string to our lamp broke during the \
transit and the company happily sent over a new one. Came within a few days as well. It was easy to put \
together. I had a missing part, so I contacted their support and they very quickly got me the missing piece! \
Lumina seems to me to be a great company that cares about their customers and products!
"""

prompt = f"""
what is the sentiment of the following product review, which is delimited with triple backticks?
Review text:'''{text}'''
"""
response = get_completion(prompt)
print(response)
```

    The sentiment of the product review is positive.
    


```python
prompt = f"""
what is the sentiment of the following product review, which is delimited with triple backticks?
Give your answer as a single word, either "positive" or "negative" .
Review text:'''{text}'''
"""
response = get_completion(prompt)
print(response)
```

    positive
    


```python
prompt = f"""
Identify a list of emotions that the writer of the following review is expressing. \
Include no more than five items in the list. Format your answer as a list of lower-case words separated by commas.
Review text:'''{text}'''
"""
response = get_completion(prompt)
print(response)
```

    happy, satisfied, impressed, grateful, content
    


```python
prompt = f"""
Is the writer of the following review expressing anger? The review is delimited with triple backticks. 
Give your answer as either yes or no.
Review text:'''{text}'''
"""
response = get_completion(prompt)
print(response)
```

    No
    


```python
prompt = f"""
Is the writer of the following review expressing happy? The review is delimited with triple backticks. 
Give your answer as either yes or no.
Review text:'''{text}'''
"""
response = get_completion(prompt)
print(response)
```

    Yes.
    


```python
prompt = f"""
Identify the following items from the review text:-Item purchased by reviewer
- company that made the item
The review is delimited with triple backticks. Format your response as a JSON object with .
"Item" and "Brand" as the keys.
If the information isn't present, use "unknown" las the value.
Review text:'''{text}'''
"""
response = get_completion(prompt)
print(response)
```

    {
      "Item": "lamp",
      "Brand": "Lumina"
    }
    


```python
prompt = f"""
Identify the following items from the review text:
-sentiment ( positive or negative)
-Is the reviewer expressing anger? (true or false)
-Item purchased by reviewer
-Company that made the item
The review is delimited with triple backticks. Format your response as a JSON object with .
"sentiment" , "Anger" , "Item" and "Brand" as the keys.If the information isn't present, use "unknown"as the value.
Make your response as short as possible.Format the Anger value as a boolean.
Review text:'''{text}'''
"""
response = get_completion(prompt)
print(response)
```

    {
      "sentiment": "positive",
      "Anger": false,
      "Item": "lamp with additional storage",
      "Brand": "Lumina"
    }
    


```python
story = f"""
Private enterprises play a vital role in China's economic development, and within this dynamic and opportunistic business environment,\
there is a remarkable employee named Li Ming who showcases his deep love and sense of belonging for his company.\
Li Ming, a seasoned sales manager, has been working for a private enterprise for the past five years. \
He considers it his second home. During our conversation, he openly expressed his feelings towards the company.\
First and foremost, Li Ming strongly identifies with the company's corporate culture and values.\
He mentioned that the company emphasizes teamwork, innovation, and employee growth, \
which creates a positive and motivating work atmosphere. He expressed his pride and motivation, \
stating that he is willing to contribute more to the company's development.\
Furthermore, Li Ming highly appreciates the trust and respect he receives from the company's leadership team. \
He commended the senior management for their attitude of listening to employee opinions during decision-making processes \
and maintaining transparent and fair communication. He believes that this open communication and leadership \
style have fostered trust, making employees feel valued and important.\
Li Ming also acknowledged the company's provision of excellent benefits and development \
opportunities for its employees. He expressed gratitude for the training and promotion opportunities provided, \
which allowed him to continuously enhance his skills and knowledge. Additionally, \
the company prioritizes work-life balance and offers flexible work arrangements and welfare benefits,\
enabling employees to better manage their personal and professional lives.\
Lastly, Li Ming emphasized the strong cohesion within the company's "big family." \
He likened the company's team to a warm and supportive family, where colleagues assist, understand, \
and encourage one another. They share the joys and achievements together, overcoming both successes and challenges. \
Li Ming nostalgically shared that this team spirit generates a sense of unity and belonging, \
eliminating any feelings of loneliness in the workplace.\
As a Chinese private enterprise employee, Li Ming's story exemplifies his deep love and attachment to his company. \
His strong alignment with the company's culture, trust in leadership, appreciation for benefits and opportunities, \
and sense of camaraderie all contribute to his positive and fulfilling work experience.
"""

prompt = f"""
Determine five topics that are being discussed in the following text, which is delimited by triple backticks.
Make each item one or two words long.
Format your response as a list of items separated by commas.
Text:'''{story}'''
"""
response = get_completion(prompt)
print(response)
```

    Private enterprises, Employee loyalty, Corporate culture, Leadership style, Work-life balance
    


```python
topic_list = ["Private enterprises", "Employee loyalty", "Corporate culture", "Leadership style", "Work-life balance",
             "work overtime"]
prompt = f"""
Determine whether each item in the following list of topics is a topic in the text below, which\
is delimited with triple backticks.
Give your answer as list with 0 or 1 for each topic.
List of topics:{",".join(topic_list)}
Text:'''{story}'''
"""
response = get_completion(prompt)
print(response)
```

    Private enterprises: 1
    Employee loyalty: 1
    Corporate culture: 1
    Leadership style: 1
    Work-life balance: 1
    Work overtime: 0
    


```python

```
