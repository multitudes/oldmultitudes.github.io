---
layout: post
title:  "AI for Everyone - a Takeaway"
date:   2017-03-20 10:41:47 +0100
categories: AI, games
comments: true
published: true
---
<div class="message">
The old model of education where you go to college for four years and then work for
the remaining 40, that just does not work anymore into these rapidly changing world. 
Through governments, companies and individuals realizing that all of us need to keep on learning, 
this increases the odds that everyone will be in a better position, even as jobs may go away.
<br>
<cite>Andrew NG (2019) </cite>
</div>

![image](/assets/img/AI4Everyonepics/PastedGraphic-2.png)

This post wants to give a very high-level bird view of AI. I put together a series of annotation inspired by watching AI for everyone, a non-technical series of videos about AI on Coursera by Andrew Ng. After attending this course I am amazed how he could manage to do really an accessible course about AI without going in deep in technical details. He managed quite a feat indeed and the course is very easy to follow.
For me, the most interesting part has been the week where he talks about ethics and AI. Realistically, there will be a long fight ahead of us, comparable to what we had in the past (and still today) with fraud and spam emails. Security in AI is becoming an important topic.

## What is AI? 

AI is a system of tools to make computers act intelligently.

The main AI tools are Machine Learning and Data Science. 
Deep Learning and Neural Networks are subset of machine learning. 

### The rise of AI 

The rise of AI has been largely driven by machine learning, ML for short. The most common type is called supervised learning. The idea of supervised learning where a model trains itself to learn input to output mappings on a training set of data has been around for many decades, but it’s really taken off in the last few years. Thanks to the rise of the Internet and the rise of computers, the amount of data you have access to has really grown. To increase the performance you need to have a lot of data, not only this. Only data is not enough. With more data, you need to be able to train a larger neural network. So, the rise of fast computers with graphics processing units or GPUs has recently facilitated the spread of AI.

Examples of models trained with supervised learning are:
- Spam filters.
- Speech recognition.
- Machine translation.
- Online advertising, (‘will you click on this ad or not?’)
- A self-driving car,(avoid the other cars and obstacles).
- In manufacturing (computer vision can use AI to find a defect in the finished product)

## What is Data?

There are structured and unstructured data. An example of unstructured data is pictures, text, audio.
When I collect pictures I need to label them to create a dataset and be able to train a model to predict the label of still unseen pictures. 
Structured data is organised like a spreadsheet with data divided into columns. One of the columns in the training dataset will be the value my model is being trained to predict.

## How do I acquire data?

- Manual Labeling (ex pictures)
- Observing and recording behaviours, of a machine, website users etc
- Download from web or partners

The importance of data can be misunderstood. More data is not always an advantage. 
It is important that the relevant data is collected, so it is recommended to experiment with data before to spend too much time collecting it, to find out that it is not helping to train our model.
Data can be messy as well, with missing values or a mix of different types, and we will have to decide how to deal with this.

### What is ML

<!-- 
<div class="message">
 -->
> Machine learning is the field of study that gives computers the ability to learn without being
explicitly programmed. <br>
    <cite>Arthur Samuel (1959) </cite>
<!-- </div>
 -->
 
![image](/assets/img/AI4Everyonepics/PastedGraphic0.jpg)

Arthur Samuel was one of the pioneers of machine learning, who was famous for building a checkers-playing program. 
They could play checkers, even better than he himself, the inventor could play the game. So, a machine learning project will often result in a piece of software that runs, that outputs B given A. 
In contrast, data science is the size of extracting knowledge and insights from data. So, the output of a data science project is often a slide deck, the PowerPoint presentation that summarizes conclusions for executives to take business actions.

The Regression problem and Classification are the most common solved problems in Machine Learning today. Regression we want our model to look at an example of our data and predict a number or more specifically a floating point number. 
For a classification problem, we want our model to look at an example of our data and tell us which class this example is. Incidentally, logistic regression is a classification algorithm!

## Deep Learning and Neural Networks 
### What is deep learning? 
Deep Learning uses a neural network, sometimes called an artificial neural network. the terms neural network and deep learning are used interchangeably and they mean essentially the same thing. The Deep in deep Neural Networks refers to how deep are the layers of our model. What a neural network does is takes the inputs and then output B, which is our predicted value example: 
price of a house given the number of bedrooms, size, etc. Ex demand and price. Price goes up and demand goes down. This a very simple neuro-network. ￼ 

![image](/assets/img/AI4Everyonepics/PastedGraphic1.jpg)

Imagine the neuron as a Lego brick and stack more of them together mapping an (input) to b (output)

￼![image](/assets/img/AI4Everyonepics/PastedGraphic2.jpg)￼

Neural networks are much bigger in the thousands of nodes and figure for themselves the function inside, affordability and awareness and quality, given they are large enough.

## How can a company become good at AI? 

Create pilot projects to gain momentum. AI training in house. Strategic data acquisition. Give a product for free or heavily discounted in order to collect data. Be good at data acquisition. Automation, understand what can be automated well. Have teams for ML.

## The limits of AI and ML 
The rise of AI can create inflated expectations. It is important to help people form an intuition about what's possible and what is not. AI can understand if an email is spam, or a complaint, or a refund request but cannot empathise on customer problems. Or produce market research papers. Learning a ‘simple’ concept is more likely to be feasible. Also if we have enough data available a self-driving car can learn to recognise position and distances of objects. But recognise the intention of gesture is still very difficult. Also, the level of accuracy required makes it harder to train for gestures. An AI model can learn to diagnose pneumonia from 10000 images, but cannot learn from 10 images and a paragraph in a medical textbook like a young doctor would do. AI cannot learn complex concepts from a small amount of data and cannot perform well on a new unseen type of data..

## How face recognition works. 
When we see an image of a face we recognise eyes and other traits of the person. What does a computer see? The computer sees just a grid of pixel brightness values. In a colour picture that pixel would correspond to three values of intensity of Red Green and Blue The job of the neural network is to take in input these values and output the name of the person in the picture
So if the picture is 1000 x 1000 pixels, the inputs of my neural network would be of 1000000 nodes. If it is a colour picture of 3000000. For picture recognition convolutional NN is used where the first block of neutrons learn to recognise edges and lines, then the second learn how to put them together in details form the picture and the last layers learn to map this to a person.

## Workflows
Key steps are:
- collect data
- train model
- iterate
- deploy (might not work as well)

## Data Science versus Machine Learning

Example of a data science project could be to analyse the traffic on a commerce website. How many times people go to the checkout without buying. If the number is high, it is maybe the shipping costs are not included in the price of the item. It is important to get an insight into data and then apply those insights to the model - website. And reanalyse the data periodically to see if the accuracy of prediction gets better. 
Data Science optimises the sale funnel on websites. ML can automate the sorting of emails, or a manufacturing line. Data science is used to maximise yield. Collect analyse and suggest actions. DS optimise product line 
As common use for ML is the visual inspection on the final product

Data Science wants to optimise the recruiting process. ML can screen resumes Data science: Marketing A/B testing is common in Websites .two version of the same version and sees which one is performing more ML: website Recommendation product recommendation Agriculture. Data science: Data on soil weather condition. Crop analytics. ML: Precision weed killing?

## What AI can do? 
<!-- 
Think more about automating tasks instead of automating jobs. 
You can make progress even without more data. Big data is great when you can get it, but it is sometimes overhyped.
Technical diligence (doable with AI systems? How much data need? Engineering timeline) vs business diligence (valuable for business . Lower cost, increase revenue, launch new product)
Also ethical diligence. Make sure humanity is better off with your project
ML projects can be "in house" or outsourced. DS more commonly in house
Keywords Acceptance criteria. A measure of the min accuracy for a project
Training set (validation set ) and test set
Ex smart speaker Trigger word recognition Speech recognition Intent recognition Execute -->

## Example of job roles in AI

Software Engineer -> ensure the reliability of the ML application As applied ML Scientist:
Machine Learning Engineer ->
Machine Learning Researcher -> extend the state of the art in ML

## The AI Transformation playbook for a company :
Execute pilot projects to gain momentum
Build an in-house AI Team
Provide broad AI training
Develop an AI strategy
Develop internal and external communication
Develop an AI strategy

Leverage AI to create an advantage specific to your industry sector.
Design strategy aligned with the “Virtuous Cycle of AI”: a better product > brings more users > brings more data > brings a better product etc

### Computer Vision can be divided in:

#### Image Classification/Object recognition and Face recognition
- Object detection
- Image segmentation
- Tracking
- Natural Language Processing

#### Text Classification
- Information retrieval (E.g. web search)
- Name Entity recognition
- Machine Translation
- Speech

#### Speech recognition (speech to text)
- Trigger word/wake word detection
- Speaker ID
- Speech synthesis ( text-to-speech, TTS)
- Robotics

#### Perception: whats in the world around your device
- Motion planning: finding a path for the robot to follow
- Control: sending commands for the robot to follow the path
- General Machine Learning

#### Unstructured data
- Structured Data
- Unsupervised learning

#### Clustering 
Transfer Learning Ex from a model trained to recognise cars, retrain to detect golf carts

#### Reinforcement Learning 
Uses a “Reward Signal” to tell AI when it is doing well or poorly. It automatically learns to maximise its rewards

#### GANs : (Generative Adversarial Networks) 
Synthesize new images from scratch. The image below is of an individual who does not exist.

![image](/assets/img/AI4Everyonepics/PastedGraphic3.jpg)

￼#### Knowledge Graphs For example what we get in search results:

￼![image](/assets/img/AI4Everyonepics/PastedGraphic4.jpg) ￼

## AI and Society - AI and Ethics

### AI and hype 
The optimistic hype: Sentient / super intelligent Ai killer Robots coming soon! 
The pessimistic version is: AI cannot do everything so after recognising this, many industries will stop researching and a new AI winter is coming. 
The correct view is between the two. AI cannot do everything but will transform industries.

### Limitations of AI 
AI has performance limitations. If we give biased data to our model we get biased data back! Sometimes is difficult to explain what is happening behind the scenes
### Bias 
Bias matters. Examples of it are: 
- Hiring tools that discriminated against women. 
- Facial recognition working better for light-skinned than dark-skinned individuals 
- Bank Loans approvals 
- Toxic effect of reinforcing unhealthy stereotypes 

Combating bias: technical solutions, eg zero out the bias in words- use less biased data or more inclusive data transparency and or auditing processes diverse AI workforce
### Adversarial attacks 
As in the picture below The so-called adversarial attack on AI are a real problem for security. 
Minor transformation in pixel value cause the AI to misinterpret a picture even it looks the same for a human￼

![image](/assets/img/AI4Everyonepics/PastedGraphic5.jpg) 
![image](/assets/img/AI4Everyonepics/PastedGraphic6.jpg) 


## Adversarial defences

- Defences do exist but incur monetary cost.
- Similar to spam vs anti-spam we might be in an arms race for some applications

## Adverse uses of AI

- Deep fakes (synthetic video of people doing things they never did
- the undermining of democracy and privacy ( oppressive surveillance)
- Generating fake comments
- spam vs antispam and fraud vs antifraud
￼

## AI, developing economies and jobs

Some economies never had the evolution from PC, desktop computer to mobile, but they did “leapfrog” from nothing in term of infrastructures to mobile payments and online education for instance. AI will impact jobs worldwide. On an optimistic prediction by 2030, we will have 400-800 mil jobs lost, and 555-890 mil jobs created. So there is apparently no reason to panic just yet!



That's it for now. If I missed something let me know in the comments! 

All pictures courtesy of coursera, licenced for non commercial use.

￼
￼

