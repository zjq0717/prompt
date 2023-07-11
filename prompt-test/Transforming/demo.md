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
prompt = f"""
Translate the following English text to Spanish: 
'''Hi, I would like to order a blender'''
"""
response = get_completion(prompt)
print(response)
```

    Hola, me gustaría ordenar una licuadora.
    


```python
prompt = f"""
Tell me what language this is : '''Hola, me gustaría ordenar una licuadora.'''

"""
response = get_completion(prompt)
print(response)
```

    This is Spanish.
    


```python
prompt = f"""
Translate the following English text to Spanish and French and Chinese: 
'''Hi, I would like to order a blender'''
"""
response = get_completion(prompt)
print(response)
```

    Spanish: Hola, me gustaría ordenar una licuadora.
    French: Bonjour, je voudrais commander un mixeur.
    Chinese: 你好，我想订购一个搅拌机。
    


```python
prompt = f"""
Translate the following text to Chinese in both the formal and informal forms :
''' would you like to order a pillow? '''
"""
response = get_completion(prompt)
print(response)
```

    Formal: 您需要订购枕头吗？
    Informal: 你想订购枕头吗？
    


```python
user_message = [
    
    "Life is short, cherish the present."
    
]
for issue in user_message:
    prompt = f"Tell me what language this is：'''{issue}'''"
    lang = get_completion(prompt)
    print(f"Original message ({lang}): {issue}")
    
    prompt = f"""
    Translate the following text to Chinese:'''{issue}'''
    """
    response = get_completion(prompt)
    print(response,"\n")
```

    Original message (This is English.): Life is short, cherish the present.
    生命短暂，珍惜当下。 
    
    


```python
prompt = f"""
Translate the following from slang to a business letter:
'Dude，This is Joe,check out this spec on this standing lamp'
"""
response = get_completion(prompt)
print(response)
```

    Dear Sir/Madam,
    
    I am writing to bring to your attention a standing lamp that I believe may be of interest to you. Please find attached the specifications for your review.
    
    Thank you for your time and consideration.
    
    Sincerely,
    
    Joe
    


```python
data_json = {
    "students":[
        {"name":"Andy","email":"1234565@qq.com"},
        {"name":"Tom","email":"1efsdfs@qq.com"},
        {"name":"Bob","email":"1efdefasfd65@qq.com"}
    ]
}
prompt = f"""
Translate the follow python dictionary from JSON to an HTML\
table with column headers and title:{data_json}
"""
response = get_completion(prompt)
print(response)
```

    <table>
      <caption>Students</caption>
      <thead>
        <tr>
          <th>Name</th>
          <th>Email</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <td>Andy</td>
          <td>1234565@qq.com</td>
        </tr>
        <tr>
          <td>Tom</td>
          <td>1efsdfs@qq.com</td>
        </tr>
        <tr>
          <td>Bob</td>
          <td>1efdefasfd65@qq.com</td>
        </tr>
      </tbody>
    </table>
    


```python
text = {
    "I can't go to the mall because I don't have no money.",
    "I goed to the park yesterday and had a lot of fun."
}
for t in text :
    prompt = f"""Proofread and correct the follow text.If you don not find errors,just say "no error": '''{t}'''"""
    response = get_completion(prompt)
    print(response)
```

    "I can't go to the mall because I don't have any money."
    I went to the park yesterday and had a lot of fun.
    


```python
text = {
    "I can't go to the mall because I don't have no money.",
    "The sun is shining brightly today."
}
for t in text :
    prompt = f"""Proofread and correct the follow text.If you don not find errors,just say "no error": '''{t}'''"""
    response = get_completion(prompt)
    print(response)
```

    "I can't go to the mall because I don't have any money."
    No error.
    
