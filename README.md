# ds301project
Bringing Dead Philosophers Back To Life: Text Generation with LLMs and Transfer Learning
```mermaid
graph TD;
    Data_Preprocessing-->GPT2_Fine_Tune;
    Data_Preprocessing-->BERT_Prompt_Engineer;
    BERT_Prompt_Engineer-->Prompt_Generation;
    Prompt_Generation-->GPT2_Fine_Tune;
```
# Project Background

Our project was to create a philosopher chatbot that can reply to philosophical questions in the style/teachings of a specific philosopher (David Hume). We created this model by primarily implementing the concept of transfer learning and fine tuning. We curated many writings of David Hume, and fine tuned a pretrained GPT-2 model with the data. We also used BERT for a kind of prompt engineering in order to get better outputs from our GPT-2 models. 

# Project Files

We first started with Data Preprocessing<sup>([Data Preprocessing](DataPreprocessing.ipynb))</sup>, to convert raw texts in pdf into tokenized segments. 

There are two options available now: max length(by calling mode='max') and sentence(by calling 'sen').

Preprocessed data is fed into two models: pretrained GPT2, which is our main model to fulfill the generative task, and BERT<sup>([BERT'prompt engineer'](BERT'prompt_engineer'.ipynb))</sup>, which we used for do Prompt Engineering.

Prompt Engineering is done by first using the topic word of user's input to search relevant texts, embed both the texts and the user's input to find top n similar segments in the texts, prompt into the prompt for the fine tuned GPT2, with Prompt Generation<sup>([Prompt Generation](PromptGeneration.ipynb))</sup>. 

# Results
We compared the output from philosophical questions between a base model that had been fed an engineered prompt and a non engineered prompt with our fine tuned GPT model that had been fed an engineered prompt and a non engineered prompt. The results for the question "Is there a continuous self?" can be seen below:

Base model with prompt engineering:

<img width="635" alt="Screen Shot 2023-12-19 at 1 16 34 AM" src="https://github.com/simran7813/ds301project/assets/105620884/2635038a-432f-4d7d-ac93-ac5b287a6d54">

Base model without prompt engineering:

<img width="629" alt="Screen Shot 2023-12-19 at 1 16 53 AM" src="https://github.com/simran7813/ds301project/assets/105620884/6b42fb08-e203-4e95-8eb0-4d2d19ee37b9">

Fine tuned model with prompt engineering:

<img width="633" alt="Screen Shot 2023-12-19 at 1 19 14 AM" src="https://github.com/simran7813/ds301project/assets/105620884/05195def-be50-44ab-a814-ab4f8f9a6589">

Fine tuned model without prompt engineering: 

<img width="637" alt="Screen Shot 2023-12-19 at 1 19 45 AM" src="https://github.com/simran7813/ds301project/assets/105620884/9e1e6086-48ae-4a35-9ba4-0c5b1a54497f">

However, we did get some faulty results, such as output from the model that was still encoded. 

<img width="626" alt="Screen Shot 2023-12-19 at 1 20 35 AM" src="https://github.com/simran7813/ds301project/assets/105620884/cf0da511-5603-469a-ad14-54b01b8ac360">
