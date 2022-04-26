# Nissan Project

## Overview

### Backgroud

Currently Nissan uses a survey to measure opinion/brand preference, brand awareness, and attribute association for automotive brands and models.

**Attributes currently being tracked in survey**

- **Functional Attributes:** Dependable, Lasts long, Value for money, Quality fit and finish, Attractive styling, Safe, Retains resale value, Driver comfort, Fun to drive, Advanced features, Responsive handling, Prestigious, Dealerships, Fuel efficient, Quick acceleration, Environmentally friendly, Affordable
- **Personal Attributes:** Trusted, Leader, Responsible, Confident, Innovative, Exciting, Practical, Adventurous, Passionate, Distinctive, Youthful, Aggressive

We use Transformer Model combing actual customer and expert commentary online to determine natural conversations about how automotive brands and models are being talked about instead of using the traditional attributes survey takers are pushed through to. 

### Problem

Understand organically the conversations around the Nissan Rogue and competitors as a first use case. What attributes are naturally associated with which models, both outside of and including the existing attributes we track? And what is preference/opinion of each model in comparison to one another.


### Solution
To gain the data, we scraped from the Web Scrape car reviews online and merge them, including Edmunds.com, KBB.com, cars.com, Youtube Review under Nissan Rogue, Chevy Equinox, Ford Escape, Ford Bronco Sport, Honda CR-V, Hyundai Tucson, Kia Sportage, Mazda CX-5, Subaru Forester, Toyota RAV4.

Then, we directly apply zero-shot classification on all attributes as our baseline model.

Since there are some potential issues, we design a two-stage modeling:

1. Judge if this attribute is mentioned in each car review by applying transformers question-answering to it.

2. If Yes (this attribute is included in this car review), proceed to apply zero-shot classification for each attribute (eg. dependable, not dependable); If No, ignore.

### Result
**Improved results:**

<img width="800" alt="image" src="https://user-images.githubusercontent.com/69759816/165228352-28746444-837c-4dce-89db-f71eac41b0a3.png">

**Correlation of each attributes:**

<img width="800" alt="image" src="https://user-images.githubusercontent.com/69759816/165228518-02ffd910-7089-419c-b1c7-1b0707505d6c.png">


**Comparing each model:**

<img width="800" alt="image" src="https://user-images.githubusercontent.com/69759816/165228527-7d39cad1-ee23-4673-ada7-3b76f9790e50.png">

## Critical Analysis

1. The Rogue's overall rating is slightly below average, especially when it comes to car acceleration and fun to drive. We checked the car configs and Rogue has 180 hp and the others are around 200 hp. We think this is the main reason.

2. We think Rogue can bring more at this price compared with other models, which means better value for money. We think the potential customers of these models are price-sensitive, and Rogue should improve on the premise of maintaining value for money.

3. Some attributes are overlapped or unclearly defined, we may optimize them later, such as Value for money and Retains resale value are similar, and it's hard to interpret what is last long.

4. Since zero-shot model has limitations, we will choose another model, such as GPT-3, to try fine-tuning. This is also our future work.

## Huggingface Space
Huggingface space is [here](https://huggingface.co/clevo570/Nissan_Project).

## Huggingface Model Card
Huggingface model card is [here](https://huggingface.co/clevo570/Nissan_Project).

## Resource Links

[Huggingface tutorial](https://huggingface.co/course/chapter7/3?fw=pt#using-our-finetuned-model)

[facebook/bart-large-mnli](https://huggingface.co/facebook/bart-large-mnli)

[deepset/roberta-base-squad2](https://huggingface.co/deepset/roberta-base-squad2)

## Code Demo

Code is inside this repo

## Video Recording

Coming Soon
