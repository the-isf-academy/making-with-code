---
Title: Project
# draft: false
---

# Unit 01 Data Science Project

The final project for this unit will be a research project. Working with the data science tools we explored this unit, **you are expected to tell a narrative story about a time in your life using data as evidence.** 

To be successful in this project, you should **find a topic that is both interesting to you and answerable** (at least in part) with data from your chosen dataset. Your teachers will help you make sure your project hypothesis achieves that. 

{{< aside "Extra Examples" >}}

📖 **Extra Examples [HERE](https://colab.research.google.com/drive/1K12_0EC4NpNWzzhl6hGw3ImAmtxzMJuJ?usp=sharing)**

{{< /aside >}}



---

## [1] Timeline

1️⃣ **Plan your project and choose a research question.**

2️⃣ **Conduct the data analysis and create data visualizations.**

3️⃣ **Create a research poster to communicate your findings.**

4️⃣ **Present your findings to the class.**

5️⃣ **If interested, you may present your findings at Shuyuan Research Week in May.**  This is not required. 

---

📅 **You will have 6 in-class blocks to plan and complete the coding portion of this project.** 

| section | code due date |
|---------|----------|
| cs9.1  | 4 March   |
| cs9.2  | 3 March   |
| cs9.3  | 27 Feb   |

---

## [2] Starter Materials

{{< code-action >}} **You can find your project in your Google Drive:** `Project: Data Science.ipynb`

✏️ **For the poster, you may use Canva or any other service.** It will be A3 size. You will begin the poster after you finish the coding portion.

---

## [3] Assessment

✅ **The assessment is broken down into four criteria:**
- Project Planning  
- Data Analysis
- Data Visualization 
- Data Communication


**For each criteria you will be assigned a score from 0-3:**
- 0 - no to no evidence of the concept
- 1 - limited evidence of the concept
- 2 - adequate evidence of the concept
- 3 - substantial evidence of the concept


--- 

## [4] Success Claims

💯 **Successful computer scientists should be able to make the following claims:**
- Project Planning 
    - I can choose a relevant research question and determine appropriate forms of evidence
    - I can consistently track my progress with specific comments
- Data Analysis  
    - I can prepare my dataset by adding and removing necessary columns or rows
    - I can combine and reorganize pieces of data to explore new relationships and support my research question
    - I can generate summary statistics (mean, median, mode, frequency count) for describing the data
    - I can write readable code by using descriptive names for modules, functions, and variables
    - I can write descriptive comments to describe complex pieces of the code
- Data Visualization 
    - I can choose appropriate data visualizations to communicate my findings 
    - I can display data visualizations that are thoughtfully sorted and easy to read
    - I can include appropriate title, axis, and labels for my visualizations
- Data Communication: Poster 
    - I can explain the purpose and focus of the research 
    - I can explain my methodology, including action steps and reasoning for restructuring the data
    - I can reflect on the meaning of the data and provide context of the results
    - I can discuss the limitations and potential biases of my data and analysis 
    - I can consider potential future areas of investigation if I were to continue this project

**Keep the success claims in mind when coding your project.**

---

## [5] Tips & Tricks

**Detecting Chinese Characters**

Here is an example of how to detect if there are Chinese characters in a string.
- You will need to import `regex`
- Then use `regex.search()` - it will return either `True` or `False` if there are Chinese characters

```python
import regex

chinese_string = "上海 2025"

if regex.search(r'\p{Han}', chinese_string) == True:
  print("Has Chinese!")
else:
  print("No chinese")
```
