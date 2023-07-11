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
《Rita Hayworth and Shawshank Redemption》 is a drama film.

Plot summary: The film tells the story of Andy Dufresne (played by Tim Robbins), \
who is wrongly convicted of his wife's murder and sent to Shawshank State Penitentiary.\
In prison, he forms a deep friendship with Red (played by Morgan Freeman) and \
uses his intelligence and perseverance to help other inmates transform their lives.

Director and cast: The film is directed by Frank Darabont, with Tim Robbins and Morgan \
Freeman in the lead roles. Director Darabont is renowned for his excellent directing skills \
and storytelling abilities, while Robbins and Freeman deliver outstanding performances, \
infusing the characters with depth and complexity.

Visual effects and cinematography: "The Shawshank Redemption" offers a visually immersive experience. \
The cinematography, with its precise use of camera angles and set design, \
captures the oppressive atmosphere of prison life and the emotional journey of the characters.

Music and score: The film's score, composed by Thomas Newman, \
is emotionally resonant and warm. The music plays a significant role in the film, \
enhancing the tension of the plot and expressing the characters' emotions.

Themes and significance: "The Shawshank Redemption" explores themes of hope, \
freedom, and the power of the human spirit. It conveys a profound understanding of \
the importance of perseverance, seeking truth, and pursuing personal freedom.

Critical reception and awards: The film received widespread acclaim and is often \
hailed as one of the greatest films of all time. It garnered seven Academy Award \
nominations, including Best Picture and Best Director, and has since become a cinematic classic.

Emotions and mood: Watching "The Shawshank Redemption" evokes a range of emotions, \
from hope to despair, from setbacks to triumphs, offering a deeply moving and engaging viewing experience.

Historical and social impact: Set in 20th-century America, \
the film touches upon sensitive social issues such as the prison system, \
social injustice, and the complexity of human nature, reflecting the context of its time.

Similar film recommendations: If you enjoyed "The Shawshank Redemption," \
I also recommend watching "Witness for the Prosecution" and "Argo,"\
as these films share compelling stories and captivating performances.
"""
prompt = f"""
Your task is to write a promotional draft for the movie from the perspective of the promotional side,\
in order to attract the audience's attention.

This promotional manuscript is prepared for audiences who value actors, \
introducing the actors and their performances.


Up to 200 words.
<tag>{text}</tag>
"""
response = get_completion(prompt)
print(response)
```

    Experience the power of friendship, perseverance, and hope in the critically acclaimed drama film, "Rita Hayworth and Shawshank Redemption." Directed by Frank Darabont and starring Tim Robbins and Morgan Freeman, this film tells the story of Andy Dufresne, a man wrongly convicted of murder and sent to Shawshank State Penitentiary. Through his friendship with Red, played by Freeman, Andy uses his intelligence and determination to transform the lives of his fellow inmates.
    
    The film's outstanding performances by Robbins and Freeman bring depth and complexity to their characters, while the precise cinematography captures the oppressive atmosphere of prison life. The emotionally resonant score by Thomas Newman enhances the tension of the plot and expresses the characters' emotions.
    
    "The Shawshank Redemption" explores themes of hope, freedom, and the power of the human spirit, making it a cinematic classic that has received widespread acclaim and seven Academy Award nominations. This film offers a deeply moving and engaging viewing experience that evokes a range of emotions, from hope to despair, from setbacks to triumphs.
    
    Reflecting the context of its time, "The Shawshank Redemption" touches upon sensitive social issues such as the prison system and social injustice. If you enjoyed this film, we recommend watching "Witness for the Prosecution" and "Argo," as they share compelling stories and captivating performances. Don't miss out on this unforgettable cinematic experience.
    


```python
prompt = f"""
Your task is to write a promotional draft for the movie from the perspective of the promotional side,\
in order to attract the audience's attention.
<tag>{text}</tag>
"""
response = get_completion(prompt)
print(response)
```

    Experience the power of hope and the human spirit in "Rita Hayworth and Shawshank Redemption." Directed by Frank Darabont and starring Tim Robbins and Morgan Freeman, this drama film tells the story of Andy Dufresne, who is wrongly convicted of his wife's murder and sent to Shawshank State Penitentiary. Through his friendship with Red and his own intelligence and perseverance, Andy transforms the lives of those around him.
    
    With stunning cinematography and a moving score by Thomas Newman, "The Shawshank Redemption" offers a visually immersive and emotionally resonant experience. The film explores themes of hope, freedom, and the power of the human spirit, and has received widespread acclaim, including seven Academy Award nominations.
    
    Watching "The Shawshank Redemption" is a deeply moving and engaging experience, evoking a range of emotions from hope to despair. The film also touches upon sensitive social issues, reflecting the context of its time.
    
    If you enjoyed "The Shawshank Redemption," we also recommend watching "Witness for the Prosecution" and "Argo," as these films share compelling stories and captivating performances. Don't miss out on this cinematic classic and its profound message of perseverance and personal freedom.
    


```python
prompt = f"""
Your task is to write a promotional draft for the movie from the perspective of the promotional side,\
in order to attract the audience's attention.

Up to 200 words.

<tag>{text}</tag>
"""
response = get_completion(prompt)
print(response)
```

    Experience the power of hope and the human spirit in "Rita Hayworth and Shawshank Redemption." Directed by Frank Darabont and starring Tim Robbins and Morgan Freeman, this drama film tells the story of Andy Dufresne, who is wrongly convicted of his wife's murder and sent to Shawshank State Penitentiary. In prison, he forms a deep friendship with Red and uses his intelligence and perseverance to help other inmates transform their lives.
    
    With visually immersive cinematography and emotionally resonant music by Thomas Newman, "The Shawshank Redemption" offers a deeply moving and engaging viewing experience. The film explores themes of hope, freedom, and the power of the human spirit, conveying a profound understanding of the importance of perseverance, seeking truth, and pursuing personal freedom.
    
    Widely acclaimed and often hailed as one of the greatest films of all time, "The Shawshank Redemption" received seven Academy Award nominations, including Best Picture and Best Director. It has since become a cinematic classic, touching upon sensitive social issues and reflecting the context of its time.
    
    If you enjoyed "The Shawshank Redemption," we also recommend watching "Witness for the Prosecution" and "Argo," as these films share compelling stories and captivating performances. Don't miss out on this unforgettable cinematic experience.
    


```python
prompt = f"""
Your task is to write a promotional draft for the movie from the perspective of the promotional side,\
in order to attract the audience's attention.

This promotional manuscript is prepared for audiences who value actors, \
introducing the actors and their performances

Up to 200 words.

<tag>{text}</tag>
"""
response = get_completion(prompt)
print(response)
```

    Step into the world of "Rita Hayworth and Shawshank Redemption," a gripping drama film that will leave you on the edge of your seat. Directed by Frank Darabont, this film features an all-star cast, including Tim Robbins and Morgan Freeman, who deliver outstanding performances that will leave you in awe.
    
    The film tells the story of Andy Dufresne, a man wrongly convicted of his wife's murder and sent to Shawshank State Penitentiary. In prison, he forms a deep friendship with Red and uses his intelligence and perseverance to help other inmates transform their lives. The cinematography captures the oppressive atmosphere of prison life and the emotional journey of the characters, while the score by Thomas Newman enhances the tension of the plot and expresses the characters' emotions.
    
    "The Shawshank Redemption" explores themes of hope, freedom, and the power of the human spirit, conveying a profound understanding of the importance of perseverance, seeking truth, and pursuing personal freedom. The film received widespread acclaim and is often hailed as one of the greatest films of all time, garnering seven Academy Award nominations, including Best Picture and Best Director.
    
    If you enjoyed "The Shawshank Redemption," we also recommend watching "Witness for the Prosecution" and "Argo," as these films share compelling stories and captivating performances. Don't miss out on this cinematic classic that will leave you with a range of emotions, from hope to despair, from setbacks to triumphs.
    
