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
text1 = f"""
When watching "The Flash," I couldn't help but feel a sense of nostalgia. \
Undoubtedly, this would be a "comeback" for DC, as countless netizens have mentioned the phrase "exceeded expectations." \
I still remember watching Jay Oliva's animated version of "Flashpoint Paradox" ten years ago, \
and my comment at that time was, "I hope they make a live-action movie of this story, I'm sure it would be satisfying."\
Now, after ten years of waiting, when it was finally made and released, the quality of "The Flash" itself is indeed quite impressive.\
The remarkable action sequences, visually stunning scenes, and well-executed use of bullet time, \
along with clear multiple storylines and touching emotional cues, make it highly enjoyable. However, \
the greater surprise that "The Flash" brought me, and the source of my nostalgia, lies in the Easter eggs\
it ignited—spanning DC's entire half-century history. Generations of emotions are displayed on this big screen.
"""
text2 = f"""
I thought "Spider-Man: Into the Spider-Verse" was already a masterpiece, but its sequel turned out to be\
even more surprising. It is the ceiling, the art itself. It elevates the artistic standard of the entire \
superhero film genre. The various Spider-Man designs are created by comic artists using different mediums,\
each with their own unique style. Some use markers, some use paintbrushes, pens and ink, pencils, and so on. \
The sequel brings them into three-dimensional space, immersing the audience in the experience. As the characters move on\
the big screen, they are outlined with ink lines – these lines are no longer just static color fills on the characters, \
but they blend and permeate like watercolor using wet-on-wet technique. When watching the movie, \
you truly feel like you've stepped into a comic book made of various materials. This is a film that people will \
watch repeatedly and want to rewind to appreciate all the details. Let me first list the Easter eggs and tributes I \
discovered in the movie.
"""
text3 = f"""
The story reminds me of Keigo Higashino's "The Masked Mansion." Compared to the cliché domestic suspense formula that has been \
flooding the market recently, "The Disappearance of Her" does bring a fresh touch to its plot design. However, unfortunately, \
a great script cannot save a crude director. From the film's visuals and the use of sound and light, it still fails to avoid the \
strange and nauseating characteristics of internet dramas. For example, when depicting dizziness, there are flashy zoom effects that \
lack any sense of sophistication, falling short of the suspense maestros in film history. Additionally, the misuse of background music\
and the criticized character framing that has been a problem since "Detective Chinatown 3." The extreme lack of sophistication is hard \
to conceal.
Returning to the plot, paying tribute to Keigo Higashino is commendable, and overall, the logic is acceptable. However, \
when it comes to the details, they are filled with artificiality. There are too many unnecessary elements added in order to lay \
the groundwork for twists, making it predictable for countless viewers from the beginning. Furthermore, it falls into the trap of \
forced sentimentality, which is something that domestic suspense films never seem to abandon. The director excessively embellishes parts \
that do not require emotional manipulation, making it over-the-top. If you want to see how a romantic storyline can be handled, you should \
watch Liu Xunzimo's "Acclaimed," which is far superior to Chen Sicheng's design. Adding commercialized decorations but claiming to be a \
great suspense work before the screening is not only laughable but also embarrassing. Looking back at David Fincher's films, it seems that \
any of them can demonstrate a high-level sense that transcends multiple dimensions with ease.
"""


texts = [text1, text2, text3]

for i in range(len(texts)):
    prompt = f"""
    Your task is to summarize the above film reviews
    Summarize the review below, delimited by triple backticks, in at most 30 words.
    Review: '''{text}'''
    """
    response = get_completion(prompt)
    print(i, response, "\n")
```

    0 "The Flash" is a highly enjoyable movie with impressive action sequences, visually stunning scenes, and well-executed use of bullet time. It also ignites nostalgia with Easter eggs spanning DC's entire half-century history. 
    
    1 The sequel to "Spider-Man: Into the Spider-Verse" elevates the artistic standard of the superhero genre with unique Spider-Man designs created by comic artists using different mediums, immersing the audience in a three-dimensional comic book experience. Viewers will want to watch repeatedly to appreciate all the details. 
    
    2 "The Disappearance of Her" brings a fresh touch to its plot design but fails to avoid the strange and nauseating characteristics of internet dramas. The plot is predictable with too many unnecessary elements added in order to lay the groundwork for twists. The director excessively embellishes parts that do not require emotional manipulation, making it over-the-top. 
    
    


```python
text1 = f"""
The Huawei P60 exhibits several innovative advantages. Firstly, its camera system introduces innovative features. \
The Huawei P60 Pro boasts a 50-megapixel primary camera (Sony IMX888 sensor, approximately 1/1.4-inch sensor size),\
a 64-megapixel periscope telephoto lens (OV64B model with OIS optical stabilization), and a 50-megapixel ultra-wide-angle \
lens (IMX858 model, 1/2.51-inch sensor size). Additionally, the Huawei P60 Pro incorporates the classic RYYB pixel array into \
its imaging system. By replacing green pixels with yellow pixels, the brightness is enhanced by combining the light from red \
and green channels. The increased light input theoretically improves the light intake by around 30-40%, and the broader spectral\
response of the yellow pixels captures more photons. This significantly enhances the signal-to-noise ratio in low-light conditions, \
resulting in superior night photography capabilities.\
Secondly, the Huawei P60 series features innovative battery technology. The devices are equipped with a new battery technology \
that breaks through in terms of battery capacity and efficiency. They are rumored to include a 5000mAh carbon-silicon negative \
electrode battery (single cell) and support 88W wired fast charging.\
Furthermore, Huawei P60 series smartphones will incorporate Huawei's second-generation satellite communication technology, \
also known as "Lingxi Communication." This technology offers three key functions, including two-way SMS, voice messaging, \
and short-duration voice calls, enhancing the capabilities and practicality of satellite communication.\
Other innovations include the adoption of graphene cooling, similar to the Huawei Mate X3, for efficient heat \
dissipation. The devices will debut with HarmonyOS 3.1, a system that optimizes system architecture, improves core \
capabilities such as memory, file systems, and task scheduling, providing a more durable and smooth experience. \
Additionally, the P60 series will feature an upgraded version of Kunpeng glass, offering greater hardness and durability.
As for the disadvantages or regrets of the Huawei P60, it lacks 5G network support, which may deter some users.\
Additionally, due to restrictions on the use of Kirin processors, Huawei had to rely on Qualcomm Snapdragon processors, \
but it did not incorporate the Snapdragon 8 Gen2 processor, which can be seen as a missed opportunity.
"""
prompt = f"""
Your task is to generate a short summary of a product review from an ecommerce site.
Summarize the review below, delimited by triple backticks, in at most 30 words.
Review: '''{text}'''
"""
response = get_completion(prompt)
print(response)
```

    The Huawei P60 series boasts innovative camera features, battery technology, satellite communication, and graphene cooling. However, it lacks 5G support and missed the opportunity to incorporate the Snapdragon 8 Gen2 processor.
    


```python
text1 = f"""
The Huawei P60 exhibits several innovative advantages. Firstly, its camera system introduces innovative features. \
The Huawei P60 Pro boasts a 50-megapixel primary camera (Sony IMX888 sensor, approximately 1/1.4-inch sensor size),\
a 64-megapixel periscope telephoto lens (OV64B model with OIS optical stabilization), and a 50-megapixel ultra-wide-angle \
lens (IMX858 model, 1/2.51-inch sensor size). Additionally, the Huawei P60 Pro incorporates the classic RYYB pixel array into \
its imaging system. By replacing green pixels with yellow pixels, the brightness is enhanced by combining the light from red \
and green channels. The increased light input theoretically improves the light intake by around 30-40%, and the broader spectral\
response of the yellow pixels captures more photons. This significantly enhances the signal-to-noise ratio in low-light conditions, \
resulting in superior night photography capabilities.\
Secondly, the Huawei P60 series features innovative battery technology. The devices are equipped with a new battery technology \
that breaks through in terms of battery capacity and efficiency. They are rumored to include a 5000mAh carbon-silicon negative \
electrode battery (single cell) and support 88W wired fast charging.\
Furthermore, Huawei P60 series smartphones will incorporate Huawei's second-generation satellite communication technology, \
also known as "Lingxi Communication." This technology offers three key functions, including two-way SMS, voice messaging, \
and short-duration voice calls, enhancing the capabilities and practicality of satellite communication.\
Other innovations include the adoption of graphene cooling, similar to the Huawei Mate X3, for efficient heat \
dissipation. The devices will debut with HarmonyOS 3.1, a system that optimizes system architecture, improves core \
capabilities such as memory, file systems, and task scheduling, providing a more durable and smooth experience. \
Additionally, the P60 series will feature an upgraded version of Kunpeng glass, offering greater hardness and durability.
As for the disadvantages or regrets of the Huawei P60, it lacks 5G network support, which may deter some users.\
Additionally, due to restrictions on the use of Kirin processors, Huawei had to rely on Qualcomm Snapdragon processors, \
but it did not incorporate the Snapdragon 8 Gen2 processor, which can be seen as a missed opportunity.
"""
prompt = f"""
Your task is to generate a short summary of a product review from an ecommerce site to feedback to the development department.
Summarize the review below, delimited by triple backticks, in at most 30 words.Focusing on imaging and battery life.
Review: '''{text}'''
"""
response = get_completion(prompt)
print(response)
```

    Huawei P60 boasts innovative camera features with enhanced low-light photography and battery technology with a 5000mAh carbon-silicon negative electrode battery and 88W wired fast charging. However, it lacks 5G network support and missed the opportunity to incorporate Snapdragon 8 Gen2 processor.
    
