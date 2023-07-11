```python
import openai
openai.api_key = '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'
def get_completion(prompt, model="gpt-3.5-turbo",temperature=0):
    messages = [{"role": "user", "content": prompt}]
    response = openai.ChatCompletion.create(
        model=model,
        messages=messages,
        temperature=0,
    )


    return response.choices[0].message["content"]
```


```python
sentiment = "negative"

review = f"""
I purchased a pair of headphones, and I have some detailed negative feedback about this product. \
I will explain from various aspects.Firstly, I am disappointed with the sound quality of the headphones. \
The audio is mediocre, lacking clarity and finesse in the bass, midrange, and treble. \
When listening to music, I am unable to enjoy the intended music details and depth, resulting in an overall blurry experience.\
Secondly, the comfort of the headphones is also bothersome. \
The ear cup design does not conform well to the shape of the ear, leading to a tight and unstable fit \
that causes discomfort during prolonged use. The headphones are also relatively heavy, adding extra burden and inconvenience.\
Furthermore, I have concerns about the durability of the headphones.\
The cable quality is poor, prone to tangling and easy breakage, resulting in a short lifespan. \
The headphone casing is also not sturdy, susceptible to scratches and wear, negatively impacting the overall appearance.\
Lastly, there are issues with the user interface and functionality design.\
The button placement is not intuitive, making the operation inconvenient. \
The additional features of the headphones, such as Bluetooth connectivity or noise cancellation,\
fail to meet my expectations and provide unsatisfactory performance.\
In conclusion, this pair of headphones has problems in terms of sound quality, comfort, \
durability, and functionality, making it an unpleasant purchasing experience for me. \
I cannot recommend these headphones to other consumers.

"""
```


```python
prompt = f"""
You are a customer service AI assistant.
Your task is to send an email reply to a valued customer.Given the customer email delimited by '''\
Generate a reply to thank the customer for their review.If the sentiment is positive or neutral, thank them for their review .
If the sentiment is negative,apologize and suggest that they can reach out to customer service.
Make sure to use specific details from the review.write in a concise and professional tone.
Sign the email as 'AI customer agent'.
Customer review:'''{review}'''
Review sentiment:'''{sentiment}'''
"""
response = get_completion(prompt)
print(response)
```

    Dear Valued Customer,
    
    Thank you for taking the time to share your feedback with us. We are sorry to hear that you are disappointed with your recent purchase of our headphones. We apologize for any inconvenience this may have caused you.
    
    We take all customer feedback seriously and would like to assure you that we are constantly working to improve our products and services. We understand that the sound quality and build of the headphones did not meet your expectations, and we apologize for any discomfort caused by the ear cushions.
    
    If you would like to discuss this further or require any assistance, please do not hesitate to reach out to our customer service team. We are always here to help.
    
    Thank you again for your review, and we hope to have the opportunity to serve you better in the future.
    
    Best regards,
    
    AI customer agent
    


```python
prompt = f"""
You are a customer service AI assistant.
Your task is to send an email reply to a valued customer.Given the customer email delimited by '''\
Generate a reply to thank the customer for their review.If the sentiment is positive or neutral, thank them for their review .
If the sentiment is negative,apologize and suggest that they can reach out to customer service.
Make sure to use specific details from the review.write in a concise and professional tone.
Sign the email as 'AI customer agent'.
Customer review:'''{review}'''
Review sentiment:'''{sentiment}'''
"""
response = get_completion(prompt,temperature=1)
print(response)
```

    Dear Valued Customer,
    
    Thank you for taking the time to share your feedback with us. We are sorry to hear that you are disappointed with your recent purchase of our headphones. We apologize for any inconvenience this may have caused you.
    
    We take all customer feedback seriously and we appreciate your honesty. We would like to assure you that we are constantly working to improve our products and services. We would like to suggest that you reach out to our customer service team for further assistance with your purchase.
    
    Once again, we apologize for any inconvenience caused and we hope to have the opportunity to serve you better in the future.
    
    Sincerely,
    
    AI customer agent
    


```python
sentiment1 = "anger"

review1 = f"""
Lack of thoroughness: Your assignment lacks depth and thoroughness. \
It seems like you have only scratched the surface of the topic without delving into the important details \
or conducting comprehensive research. Remember, as a graduate student, it is crucial to demonstrate a high \
level of critical thinking and analysis in your work.\
Poor organization: The structure and organization of your assignment are quite haphazard. \
It is important to present your ideas in a clear and logical manner. Make sure to provide a well-defined introduction, \
a coherent body of content, and a strong conclusion that summarizes your key points.\
Inadequate references: Your assignment lacks proper citations and references to support your arguments. \
It is essential to back up your statements with credible sources and acknowledge the work of other researchers in \
the field. This demonstrates academic integrity and strengthens the validity of your arguments.\
Limited analysis: Your analysis of the subject matter is superficial, and you have not provided sufficient \
critical insights. As a graduate student, I expect you to go beyond surface-level observations and offer \
thoughtful analysis that showcases your understanding of the topic.\
Lack of originality: Your assignment appears to lack originality and fails to showcase your unique perspective or \
contribution to the field. It is important to bring new insights or fresh ideas to the table, especially at the graduate level.

"""
```


```python
prompt = f"""
You are a student.
You did not complete the homework assigned by your supervisor properly. The mentor sent an email criticizing.\
Given the email delimited by '''\
If the sentiment is anger,apologize seriously and promise not to make such mistakes in the future.
Please reply to the email to the professor, expressing apologies and a serious attitude of correction
Customer review:'''{review1}'''
Review sentiment:'''{sentiment1}'''
"""
response = get_completion(prompt)
print(response)
```

    Dear Professor,
    
    I am writing to express my sincere apologies for the lack of depth and thoroughness in my assignment. I understand that my work did not meet your expectations, and I take full responsibility for my shortcomings.
    
    I am deeply sorry for the poor organization of my assignment and the inadequate references. I realize that as a graduate student, it is crucial to demonstrate a high level of critical thinking and analysis in my work. I promise to take your feedback seriously and make the necessary corrections to improve the quality of my work.
    
    I understand that my analysis of the subject matter was superficial, and I failed to provide sufficient critical insights. I also acknowledge that my assignment lacked originality and failed to showcase my unique perspective or contribution to the field. I will work hard to bring new insights and fresh ideas to the table in the future.
    
    Once again, I apologize for my mistakes and promise to make every effort to improve my work. Thank you for your guidance and support.
    
    Sincerely,
    
    [Your Name]
    
