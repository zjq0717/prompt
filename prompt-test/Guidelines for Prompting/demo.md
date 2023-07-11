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
Firstly, in terms of price, I believe this computer offers excellent value for money.\
Considering the performance and features it provides, I find the price I paid to be quite reasonable. \
Compared to other computers with similar specifications in the market, this computer offers a more competitive price.
Secondly, in terms of performance, this computer performs exceptionally well. \
It is equipped with a high-performance processor and ample memory, allowing it to\
handle various tasks and applications effortlessly. I can run multiple programs simultaneously\
without experiencing any lag or delays, which is crucial for my work efficiency and smooth user experience.
As for the design, I find this computer to be sleek and stylish. \
It features high-quality materials and has been finely crafted, exuding a sense of sophistication. \
The keyboard and touchpad layout are well-designed and provide comfortable usage. Additionally,\
it boasts excellent portability, making it convenient for me to carry it around and use it while traveling.
Overall, I have a very positive evaluation of this computer. It offers a reasonable price, \
impressive performance, and an appealing design. It meets my basic requirements for a computer \
and even exceeds my expectations. I would not hesitate to recommend it, especially to those seeking a \
powerful, reasonably priced computer with an exquisite appearance.
"""

prompt = f"""
Summarize the text delimited by triple backticks \ 
into a single sentence.
<tag>{text}</tag>
"""
response = get_completion(prompt)
print(response)
```

    The author believes that the computer offers excellent value for money, performs exceptionally well, has a sleek and stylish design, and meets their basic requirements and even exceeds their expectations, making it highly recommended for those seeking a powerful, reasonably priced computer with an exquisite appearance.
    


```python
prompt = f"""
Generate a list of three made-up book titles along with their authors and genres.\
Provide them in JSON format with the following keys: book_id, title, author, genre.
"""
response = get_completion(prompt)
print(response)
```

    [
      {
        "book_id": 1,
        "title": "The Lost City of Zorath",
        "author": "Aria Blackwood",
        "genre": "Fantasy"
      },
      {
        "book_id": 2,
        "title": "The Last Survivors",
        "author": "Ethan Stone",
        "genre": "Science Fiction"
      },
      {
        "book_id": 3,
        "title": "The Secret Life of Bees",
        "author": "Lila Rose",
        "genre": "Romance"
      }
    ]
    


```python
text1 = f"""
The 618 shopping festival in China is a highly anticipated annual event that takes place on June 18th.\
It has evolved into a massive online shopping extravaganza, similar to Black Friday or Cyber Monday in the United States.\
During this period, major e-commerce platforms offer extensive discounts, promotions, and exclusive deals to attract consumers.\
Chinese shoppers eagerly participate in the festival, taking advantage of the discounts and engaging in online shopping sprees.\
The event features live-streaming shows, celebrity endorsements, and interactive games, creating a festive atmosphere. \
The 618 shopping festival not only benefits consumers but also boosts the sales and revenue of e-commerce companies, \
contributing significantly to China's retail industry. With its exciting discounts and entertaining activities,\
the 618 shopping festival has become a prominent and influential shopping season in China.
"""

prompt = f"""
You will be provided with text delimited by triple quotes.If it contains a sequence of instructions, \
re-write those instructions in the following format:

Step 1 - ...
Step 2 - ...
...
Step N - ...

If the text does not contain a sequence of instructions,then simply write \ "No steps provided. \ "
<tag>{text1}</tag>
"""
response = get_completion(prompt)
print(response)
```

    No steps provided.
    


```python
prompt = f"""
Your task is to answer in a consistent style.

<child>:Teach me about chatgpt

<teacher>:ChatGPT is an advanced language model developed by OpenAI. \
It uses deep learning techniques to generate human-like responses in conversations.\
ChatGPT can understand and generate text in a conversational manner, making it useful for chatbots,\
virtual assistants, and other interactive applications.\
Its capabilities include answering questions, providing information, \
and engaging in natural language conversations with users. \
ChatGPT has been trained on a vast amount of data to provide accurate and contextually relevant responses in real-time interactions.

<child>:Teach me about prompt
"""
response = get_completion(prompt)
print(response)
```

    <teacher>: A prompt is a specific instruction or question given to ChatGPT to generate a response. It serves as a starting point for the language model to generate text that is relevant to the given topic or context. Prompts can be simple or complex, and can be used to elicit a wide range of responses from ChatGPT. By providing a prompt, users can guide the conversation and get more specific and relevant responses from ChatGPT. It is an important tool for interacting with ChatGPT and getting the most out of its capabilities.
    


```python
text1 = f"""
Once upon a time, there was a curious young girl named Lily.\
One sunny day, she discovered a mysterious key hidden in her attic. \
Intrigued, Lily embarked on a thrilling adventure, unlocking doors to enchanted worlds. \
With each turn of the key, she met magical creatures, solved puzzles, and discovered her own courage.\
Through her journey, Lily learned valuable lessons about bravery, friendship, and the limitless power of imagination.\
In the end, she returned home with a heart full of memories and a newfound belief \
in the extraordinary possibilities that lie within ordinary moments.
"""

prompt = f"""
Perform the following actions:

1 - summarize the following text delimited by triple backticks with 1 sentence.
2 - Translate the summary into Chinese.
3 - List each name in the French summary.
4 - Output a json object that contains the following keys: chinese_summary, num_names.

Separate your answers with line breaks.

Use the following format:
Text: <text to summarize>
summary: <summary>
Translation: <summary translation>
Names : <list of names in Italian summary>
output JSON:<json with summary and num_names>
Text:
<tag>{text1}</tag>
"""
response = get_completion(prompt)
print(response)
```

    Summary: A young girl named Lily discovers a mysterious key in her attic and embarks on a thrilling adventure, unlocking doors to enchanted worlds and learning valuable lessons about bravery, friendship, and the limitless power of imagination.
    
    Translation: 从前，有一个叫莉莉的好奇女孩。有一天阳光明媚，她在阁楼里发现了一把神秘的钥匙。莉莉被吸引了，开始了一次惊险的冒险，打开通往魔法世界的门。在旅途中，她遇到了神奇的生物，解决了难题，并发现了自己的勇气。通过这次旅行，莉莉学到了关于勇气、友谊和想象力无限的宝贵经验。最后，她带着满满的回忆和对普通时刻的非凡可能性的新信念回到了家。
    
    Names: Lily
    
    Output JSON: {"chinese_summary": "从前，有一个叫莉莉的好奇女孩。有一天阳光明媚，她在阁楼里发现了一把神秘的钥匙。莉莉被吸引了，开始了一次惊险的冒险，打开通往魔法世界的门。在旅途中，她遇到了神奇的生物，解决了难题，并发现了自己的勇气。通过这次旅行，莉莉学到了关于勇气、友谊和想象力无限的宝贵经验。最后，她带着满满的回忆和对普通时刻的非凡可能性的新信念回到了家。", "num_names": 1}
    


```python
prompt = f"""
Your task is to determine if the student 's solution is correct or not.
To solve the problem do the following :
- First, work out your own solution to the problem.
- Then compare your solution to the student's solution \
and evaluate if the student's solution is correct or not.\
Don't decide if the student's solution is correct until you have done the problem yourself.

Use the following format:

Student"s solution:
...
student's solution here
...
Actual solution :
...
steps to work out the solution and your solution here
...
Is the student's solution the same as actual solution just calculated:
...
yes or no
...

Question:
...
Math problem: Solve 10 ÷ 2 + 3.

Student's solution:The student  adds 2 and 3 first, resulting in 2. 
"""
response = get_completion(prompt)
print(response)
```

    Then, the student divides 10 by 2, resulting in 5. Finally, the student adds 2 and 3 to 5, resulting in 10. 
    
    Actual solution: 
    10 ÷ 2 + 3 = 5 + 3 = 8 
    
    Is the student's solution the same as actual solution just calculated:
    No.
    


```python

```


```python

```
