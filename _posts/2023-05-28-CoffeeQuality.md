---
layout: post
title:  "BeanQuest: Unveiling the Essence of Specialty Coffees for Your Perfect Cup"
author: Sep
categories: [ Python ]
image: assets/images/coffeebean.jpg
beforetoc: "Why the specialty coffee getting more attention nowadays? What is so special about the coffee specialty and why we should use it?"
toc: true
featured: true
hidden: true
---
Discover the world of specialty coffees through our captivating analysis. Dive into the characteristics that define exceptional beans, and uncover the passionate producers behind these extraordinary brews. 

* Warning: This article is very very long, but you can read it in many way. If you want to see the insights only, please click on the Conclusion part. If you want to see the coding part, please check the python code [here](https://github.com/PouringInsights/CoffeeQuality/blob/main/coffeequality.ipynb) or go through the article in order to get the explaination. For whatever purposes that you read this article, I would like to thank you in advance for reading it. 

### Introduction
Coffee plays an important part in many people's life. Indeed, some people would take a cup of coffee to start a day by focusing and awakening, helping them have a productive day. It is the reason for using coffee, but why specialty coffee? Here is the simple answer: it contains better taste. It is the beverage recipe, we all want to have it taste good, it’s the most enjoyable part from taking a coffee cup. Moreover, it is traceable and transparent, people are allowed to trace back to the origin, knowing why its made, and how its made and prepared. Using specialty coffee also helps small scale farmers with ethical sources because the farmers are usually paid fair prices for their crops, ensuring a better livelihood and economic stability for their communities. Choosing specialty coffee supports a more equitable and transparent coffee supply chain. It also support environmental sustainability because specialty coffee producers often prioritize environmentally friendly farming practices. 
### Problem Statement
Your questions would be like: How do I know what kind of coffee would taste best? Everything taste like… coffee. I barely know the difference between each cup, do I really need to pay attention on the high quality coffee? I’m already satisfied with my current coffee daily and they taste decent, it doesn’t have much difference between my local coffee shop and Starbucks at all. 

I understand the confusion, I don’t want to set the boundary for coffee expert and the normal people, I want to make this simple as much as possible because in the end, everyone has different reference for their taste so it is such a bias if I insist on the fancy coffee instead of normal coffee. However, you are the one who actually judge the coffee shop. For example: you can basically know some coffee taste bad because it made you feel wrongly, or it doesn’t serve its purpose to help you awake for a working day,… You only feel hard to notice the slightly better coffee, but if the gap is significantly better, you probably know it. It is how it worked. The specialty coffee could allow you get what you prefer. For example: you prefer strong coffee, or you prefer some juicy coffee, everything you need would be found from specialty coffee shop. The various technique from bean to cup would allow a specialty coffee shop give you exactly what you want for your preference. 

In this article, I would describe some sort of coffee qualification that allow the customers to know coffee characteristics and even for a coffee owners would know about the coffee itself, as well as where to get it. For the reference, I will use the book: “The World Atlas of Coffee” of James Hoffman, the famous barista champion and influence in the coffee industry, his book has described all the coffee varieties and the origin, I could either read the whole book and memorise it, or using my analytical skills to extract information that I need then look at the book for more context information. 

### Dataset 
The dataset is updated in May 2023, which is new when I started writing this article. It was scrapped from Coffee Quality Institute- a non profit organization that works to improve the quality and value of coffee worldwide. All the code for the scrapper can be found in: [github](https://github.com/fatih-boyar/coffee-quality-data-CQI/tree/main) 
He has an amazing work with this scrapper in python and cleaned it as well. In my article, I will use his work instead of leading you to the technique of scrapping. I would update my analysis for that part in the future to see the change in the industry, but for now, I will use the arabica data that is cleaned in order to focus on exploration data analysis. 

```python
### Exploration Data Analysis
At first, we need to import the data into the workspace and see how the data look like: 
import pandas as pd
# Specify the file path of the dataset
file_path = r"C:\Giang\Studying\Coding fun\coffee dataset- 2023\Coffee Quality Data\df_arabica_clean.csv"

# Read the dataset into a pandas DataFrame
df = pd.read_csv(file_path)

# Display the first few rows of the DataFrame to verify the data has been loaded correctly
print(df.head())
```

There are 41 columns with different information include everything we need about coffee, each row represents the information of 1 rated coffee batch. It has the country of origin, the farm name, the lot number, mill, some ID, company that submit the coffee, the attitude of coffee where it plants, the region of coffee, the color when harvest, the defects that would affect quality, the expiration of coffee or we can understand that the used date in order to get high quality coffee,… 
Most important information of this dataset is about the flavor, about the scores. The dataset introduced the cupping scores. This cupping score would be described as the professional tasting traits, which included: 
* Aroma: Refers to the scent or fragrance of the coffee.
* Flavor: The flavor of coffee is evaluated based on the taste, including any sweetness, bitterness, acidity, and other flavor notes.
* Aftertaste: Refers to the lingering taste that remains in the mouth after swallowing the coffee.
* Acidity: Acidity in coffee refers to the brightness or liveliness of the taste.
* Body: The body of coffee refers to the thickness or viscosity of the coffee in the mouth.
* Balance: Balance refers to how well the different flavor components of the coffee work together.
* Uniformity: Uniformity refers to the consistency of the coffee from cup to cup.
* Clean Cup: A clean cup refers to a coffee that is free of any off-flavors or defects, such as sourness, mustiness, or staleness.
* Sweetness: It can be described as caramel-like, fruity, or floral, and is a desirable quality in coffee. According to James Hoffman in “the world Atlas of coffee”, the more the better. 

The professional taster would taste the coffee multiple times and record it in the scores sheet, the data we get is the results from so many tasting times. Those aspects are important. The roasters will taste the coffee using the cupping form look like this: 
![image](https://github.com/PouringInsights/pouringinsights.github.io/assets/100246099/0447019a-10e7-433b-99b1-9c6733403d51)


They taste it as a part of purchasing process, or by a jury ranking coffees of an auction of the best lots from a particular place. It will be taste again by the roaster as a part of quality control to make sure the roasting process was done correctly. The coffee owners also taste it, in order to select the coffee they wish, and finally, the customer, the one we hopefully enjoy it. 
That’s how those scores are important. Now we will take a look with the mean scores of all the attributes: 
```python
average_scores = df[['Aroma', 'Flavor', 'Aftertaste', 'Acidity', 'Body', 'Balance', 'Uniformity', 'Clean Cup', 'Sweetness','Overall'
]].mean()

# Create a bar plot
plt.bar(average_scores.index, average_scores.values)
plt.xlabel('Sensory Evaluations')
plt.ylabel('Average Score')
plt.title('Average Scores for main cupping aspect')

# Set the y-axis limits to make the differences more visible
plt.xticks(rotation=45)

plt.show()
```
![image](https://github.com/PouringInsights/pouringinsights.github.io/assets/100246099/553e26f5-4fbd-425c-b416-15d81dfb0659)

The bar chart shows the average scores for main cupping aspects. We can see that all the scores are quite high in the range of 10. The Uniformity, Clean cup and Sweetness is equal to 10 which is showing the current qualification of coffee expected the high sweetness in the taste. The Uniformity is expected for the consistency of the cup as well as the taste is not different from the described notes of it. It has somewhat shows the trends in the industry that the desirable coffee should have high sweetness as well as having no off-flavor and high consistency. Because those score is always 10 so we decided to not look at these 3 variables from now on. Rerun the code again but exclude Uniformity, Clean cup and Sweetness; limit the range from 7 to 8 to see the difference better because all the attributes have score higher than 7 and lower than 8.
```python
#immune some variables since their average is 10 
average_scores = df[['Aroma', 'Flavor', 'Aftertaste', 'Acidity', 'Body', 'Balance','Overall'
]].mean()

# Create a bar plot
plt.bar(average_scores.index, average_scores.values)
plt.xlabel('Sensory Evaluations')
plt.ylabel('Average Score')
plt.title('Average Scores for main cupping aspect')

# Set the y-axis limits to make the differences more visible
plt.xticks(rotation=45)
plt.ylim(7,8)
plt.show()
```
![image](https://github.com/PouringInsights/pouringinsights.github.io/assets/100246099/e7604db7-d31c-43a4-a9c7-acbeed1e5013)

In the chart above, we can see that flavor hold the highest score while aftertaste has lowest score. 
Flavor is a difficult attribute, James Hoffman said: “This is not just about describing the different flavors and aromas of particular coffee, but also about how pleasant the taster finds them. Many new tasters find this the most frustrating aspect of coffee tasting. Each of the coffees they taste are clearly different but the language to describe them remains elusive”. Yes, it sounds hard to understand, no worries, I will break it down in the easy and basic way, so that we can understand how this attribute describe then we can evaluate it better. 
In illustration, I would use the flavor wheel, it looks like this, and don’t go to the detail, we only need to see how it looks.
![image](https://github.com/PouringInsights/pouringinsights.github.io/assets/100246099/d7845f49-a232-45ac-8b54-cd0cf578de47)

OK I admit that this is quite hard to understand, the roasters usually use some word such as “apple”, “caramel”, “Strawberry” to describe their tastes, but it tastes like.. coffee, while they put some “irrelevant” word on it? Those words are coming from this wheel. The example of Apple or Strawberry are the way to communicate that the expected taste would have some level of sweetness and acidity. You don’t need to identify the taste with individual note such as “apple” or “caramel”, you only need to know that is sweet or fruity in example. 

The Flavor is the preference, it represents some good notes in general instead of bad notes. For example: you don’t want your coffee taste bitter but wanted to it has more sweet, or it should taste like fruity, those categories are totally different from each other, the flavor score is not bias like sweet is better than acidity because its user preference, the score is the total combination that has no bad notes, that’s all. However, this score has so much potential to rely on in tasting coffee. Therefore, Flavor is the important trait that will be used in further test. 

Another trait that is hard to understand is about balance. It is tricky attribute. Unlike Flavors, the score of balance represents the combination of flavour and mouthfeel. Many other attribute is relevant to this, we can see it in the heat map of correlation later. This attribute is like a well- mixed piece of music. The low score of balance is like one element too loud compare to the others. So that, the better mixture of coffee notes would bring higher balance. 

Body: This attribute shows the similar score compare to Balance. It is about the thickness of coffee when you drink it. If you see the coffee is quite strong, have alot of "coffee" in it, instead of some water with coffee flavor, then it is full body, and in contrast, it is light body. Sometimes this might make a confusion with underextraction but if you feel everything else is quite good, but not thick as you need, then it is about the body.  

Aftertaste score is the lowest score, meaning that the feel of the taste stay not too long in the tongue. However, this is the high quality coffee, the aftertaste score is 7.6 in average which is that’s how we expected from the Aftertaste in coffee. Some decent coffee would have less aftertaste score, as it wont stay longer in the mouth. In general, customer could feel the sweet taste after drinking for a while, it’s how the aftertaste work. 

### Correlation analysis
```python
import seaborn as sns

# Calculate the correlation matrix
correlation_matrix = df[['Aroma', 'Flavor', 'Aftertaste', 'Acidity', 'Body', 'Total Cup Points']].corr()

# Create a heatmap
sns.heatmap(correlation_matrix, annot=True, cmap='coolwarm')
plt.title('Correlation Heatmap')
plt.show()
```
![image](https://github.com/PouringInsights/pouringinsights.github.io/assets/100246099/566a8c21-917d-4e8a-bfcb-45f21f74a74b)

The heatmap shows the correlation between each traits of coffee, with the red color as the high correlation and blue color as low correlation. However, the range in this heatmap are from 0.65 to 1, meaning that all the attributes are correlated to each other. Normally, the score of 0.6 represents the moderate correlation and score higher than 0.8 is high. Lets take a look at Total cup points, we can see that all the attributes have high correlate to total points, and the order from high to low is: Flavor, Balance, Aftertaste, Acidity, Aroma, Body. Interestingly, the Aroma and Body has lowest correlation, so the smell of coffee and the thickness of coffee are not really relevant, however, it has high correlation with flavor, meaning that if the smell of coffee is extremely good, we would expect the excellent flavor as well. 

I personally love the coffee smell, the enticing aroma of coffee captivates my senses, immersing me in a world of delightful sensations and enhancing every moment. 
Beside the relationship with Total cup points, some high correlation are from Flavor with Balance and Aftertaste. It seems like those scores have highly related to each other. 

Next, I will take a look at the country of origin. Because the roasters are from around the world, it is reasonable to checking the origin of coffee and its average score with our recent dataset. 
### Country of Origin
```python
import matplotlib.pyplot as plt

# Group the data by "Country of Origin" and calculate the average cupping score
average_scores_by_country = df.groupby('Country of Origin')['Total Cup Points'].mean()

# Sort the countries by average cupping score in descending order
average_scores_by_country = average_scores_by_country.sort_values(ascending=False)

# Filter out countries with average cupping scores outside the range of 80 to 87
filtered_scores_by_country = average_scores_by_country[(average_scores_by_country >= 80) & (average_scores_by_country <= 87)]

# Calculate the country with the highest cupping score
country_highest_score = filtered_scores_by_country.idxmax()
highest_score = filtered_scores_by_country.max()

# Create a bar plot of average cupping scores by country
plt.figure(figsize=(12, 6))
plt.bar(filtered_scores_by_country.index, filtered_scores_by_country.values)
plt.xlabel('Country of Origin')
plt.ylabel('Average Cupping Score')
plt.title('Average Cupping Score by Country of Origin (80-87)')
plt.xticks(rotation=90)  # Rotate x-axis labels for better visibility
plt.ylim(80, 87)
plt.show()

print(f"The country of origin with the highest cupping score is {country_highest_score} with an average score of {highest_score}.")
print(filtered_scores_by_country)
```
![image](https://github.com/PouringInsights/pouringinsights.github.io/assets/100246099/d7613933-f809-4e63-878a-731c5dba7314)

Within the presented table, Ethiopia secures the top position with the highest average cupping score. While this outcome is expected, it is the second and third rankings that astound with their unexpected performance. The result shows that the high quality coffee recently are from Tanzania and Taiwan. OK, this result sounds weird for me, because in my general knowledge, I always see some common coffee in the specialty coffee shop is Ethiopia, Colombia, Brazil. The high score of Taiwan and Tanzania shows that these countries are seriously improve their coffee quality recently. 
Lets compare the result with the exporting data from the Statista: 
![image](https://github.com/PouringInsights/pouringinsights.github.io/assets/100246099/a512c42e-3e63-44ef-ab42-7e43a115557b)

The above chart is from Statista, and the source of it might from OEC(The Observatory of Economic Complexity): 
![image](https://github.com/PouringInsights/pouringinsights.github.io/assets/100246099/c37912c0-091a-4177-9bcf-545edce87d15)

The chart showed that Brazil, Switzerland, Colombia, Vietnam and Germany are the top exporters of coffee in the world while the top cupping score shows Ethiopia, Tanzania, Taiwan, Guatemala, and Madagascar are top 5 quality coffee in the data of May 2023. 
This proves that the high volume of coffee export doesn’t relate to the high quality of coffee. The specialty coffee map is different than this map. However, it is noted that the number of observations are only 208 from recent harvest coffee, most common harvest year is: 

```python
# Count the number of samples for each harvest year
harvest_year_counts = df['Harvest Year'].value_counts().sort_index()

# Create a bar chart
plt.figure(figsize=(12, 6))
plt.bar(harvest_year_counts.index, harvest_year_counts.values, color='#2E57B6')
plt.xlabel('Harvest Year')
plt.ylabel('Number of Samples')
plt.title('Distribution of Coffee Samples by Harvest Year')
plt.xticks(rotation=90)
plt.show()
```
![image](https://github.com/PouringInsights/pouringinsights.github.io/assets/100246099/f429570e-a029-4794-bc3b-df255a87d6d6)


Most of the coffee in the dataset harvest from 2021-2022, around 100 observations which is recent data. It means that the above countries have interested in the specialty coffee and send the sample to the CQI to evaluate it. It doesn’t mean other countries have bad coffee overtime, it only proves that recently, CQI recorded that coffee from Ethiopia, Taiwan and Tanzania have the highest cupping score. 
Let check the book to know more about those 3 origin: 
* Tanzania: According to James Hoffman, the taste profile of Tanzania coffee is complex, with bright and lively acidity and often with berry and fruity flavours. It can be juicy, interesting and delicious. 
* Ethiopia: The birthplace of coffee, its taste is diversity. It could be citrus, often bergamot, florals through to candied fruit or even tropical fruit flavors. The best washed coffee can be incredibly elegant, complex and delicious and the best naturally processed ones can be wildly fruity, and enchantingly unusual. 
* Taiwan: I cant find Taiwan in the book but China, it might because Taiwan is not considered as coffee region, so lets see what it said from China first. In China, the quality based auctions are increasingly popular and prices being paid for locally grown coffee are very high. This makes China an unusual market. China now exporting some excellent coffee, which is well worth seeking out. The taste profile from China have pleasant sweetness and fruitiness, though many still carry a little woodiness or earthiness too. Relatively low in acidity and often relatively full bodies. I would do the research for Taiwan coffee too to compare if it has different taste profile. Founder of San Formosan, Ding He Doong concluded that Taiwanese coffee has a sweet aftertaste and many people said it has tea like aroma. Ofcourse many production would have different characteristics but in general, the sweet aftertaste is the main tasting profile for Taiwanese coffee. 

Next, I will explore the coffee varieties: 
### Varieties
```python
import pandas as pd

# Group the data by "Country of Origin" and "Variety", and count the unique values in "Variety" column
variety_counts_by_country = df.groupby(['Country of Origin', 'Variety']).size().reset_index(name='Count')

# Find the countries with the highest number of unique varieties
top_countries = variety_counts_by_country.groupby('Country of Origin')['Count'].count().nlargest(5).index

# Filter the data for the top countries
top_varieties = variety_counts_by_country[variety_counts_by_country['Country of Origin'].isin(top_countries)]

# Group the top varieties by country and aggregate the variety names
top_varieties_agg = top_varieties.groupby('Country of Origin')['Variety'].agg(lambda x: ', '.join(x))

# Create a DataFrame for the top countries and varieties
result_df = pd.DataFrame({'Country of Origin': top_countries, 'Varieties': top_varieties_agg}).reset_index(drop=True)

# Display the result as a table
print(result_df)


 Country of Origin 	                                         Varieties	Number of Varieties
 Colombia  	Bourbon Sidra, Castillo, Castillo Paraguaycito, Castillo and Colombia blend, Castillo,Caturra,Bourbon, Caturra, Caturra,Colombia,Castillo, Red Bourbon, Red Bourbon,Caturra, Santander, Typica Gesha	11
 Taiwan 	BOURBON, CATURRA Y CATIMOR, Bourbon, Catuai, Caturra, Gesha, MARSELLESA, CATUAI, CATURRA & MARSELLESA, ANACAFE 14, CATUAI, Typica	7
 Thailand  	Catrenic, Caturra, Caturra-Catuai, Parainema, SHG, Sarchimor	6
 Guatemala  	Caturra, Gesha, SL34, Sl34+Gesha, Typica, Typica + SL34, Yellow Bourbon, unknow, unknown	9
 Nicaragua  	Bourbon, Bourbon, Catimor, Caturra, Typica, Catimor, Caturra, Gayo, Java, Typica, Typica Bourbon Caturra Catimor 	8

In the table above, in the dataset, the Colombia has the highest number of coffee varieties, then Taiwan, Thailand, Guatemala and Nicaragua have the several of varieties that are high quality, it allows coffee shop owners choose the variety easier since each variety has different taste profile. Now let see which variety has the high score. 
```
```python
# Group the data by "Variety" and find the maximum cupping score for each variety
top_cupping_scores = df.groupby('Variety')['Total Cup Points'].max().reset_index()
top_cupping_scores = top_cupping_scores.sort_values('Total Cup Points', ascending=False).reset_index(drop=True)

# Group the data by "Variety" and find the maximum flavor score for each variety
top_flavor_scores = df.groupby('Variety')['Flavor'].max().reset_index()
top_flavor_scores = top_flavor_scores.sort_values('Flavor', ascending=False).reset_index(drop=True)

# Group the data by "Variety" and find the maximum balance score for each variety
top_balance_scores = df.groupby('Variety')['Balance'].max().reset_index()
top_balance_scores = top_balance_scores.sort_values('Balance', ascending=False).reset_index(drop=True)

# Group the data by "Variety" and find the maximum body score for each variety
top_body_scores = df.groupby('Variety')['Body'].max().reset_index()
top_body_scores = top_body_scores.sort_values('Body', ascending=False).reset_index(drop=True)

# Print the top scores for each category
print("Top Cupping Scores by Variety:")
print(top_cupping_scores.head(5))
print()

print("Top Flavor Scores by Variety:")
print(top_flavor_scores.head(5))
print()

print("Top Balance Scores by Variety:")
print(top_balance_scores.head(5))
print()

print("Top Body Scores by Variety:")
print(top_body_scores.head(5))
```

Top Cupping Scores by Variety:
  
     Variety	  Total Cup Points
     Castillo  	 89.33
        Gesha    	 87.58
         Java    	 87.42
  Red Bourbon    	87.08
4  Sl34+Gesha       	86.75

Top Flavor Scores by Variety:
               
Variety 	 Flavor
                Gesha 	   8.50
             Castillo   	 8.50
                 Java   	 8.42
          Red Bourbon  	  8.33
  Ethiopian Heirlooms  	  8.25

Top Balance Scores by Variety:
    
  Variety  	Balance
    Castillo    	 8.42
       Gesha    	 8.25
         SHG    	 8.17
        Java     	8.17
  Sl34+Gesha   	  8.08

Top Body Scores by Variety:
  Variety 	 Body
  Castillo  	8.25
     Gesha  	8.25
   Bourbon 	 8.17
   Caturra 	 8.08
   Catimor  	8.08
  






In all the table above, the fancy coffee such as Castillo, Gesha, Java, Red Bourbon and SL34 are having high total cup scores, which make them become the most quality variety. However, some of them are expensive, and the number of production are usually small. This would be good for quality, but not for profit. Lets check the other table with the top score of some important attribute. 
* Flavor: It has similar names in this table, except for Ethiopian Heirlooms. It seems like the Ethiopia farmers are producing Heirlooms. As expected from the world famous coffee origin, the Heirlooms have the excellent flavor. This would be an option for coffee owner, everyone love Ethiopian coffee, see it as the top qualified coffee, and most of all, it is usually cheaper than other variety such as Gesha. 
* Balance: Beside Castillo and Gesha, there are SHG variety in the list. SHG (Strictly High Grown) specifies that the coffee was grown at an altitude around 1350 meters. Higher altitude generally means higher quality but at the expense of greater cost. As always, you get what you pay for. OK its another expensive one, might consider SL34 instead if the coffee owner prefer balancing in the taste
* Body: Some people love thickness, they feel like they need strong coffee and the full body coffee would give them the satisfaction, in this list, we have Castillo, Gesha, Bourbon, Caturra and Catimor. Most of varieties here have the achievable price except for Gesha in general. 
import matplotlib.pyplot as plt

```python
# Group the data by "Variety" and find the maximum scores for each category
top_cupping_scores = df.groupby('Variety')['Total Cup Points'].max().sort_values(ascending=False).head(5)
top_flavor_scores = df.groupby('Variety')['Flavor'].max().sort_values(ascending=False).head(5)
top_balance_scores = df.groupby('Variety')['Balance'].max().sort_values(ascending=False).head(5)
top_body_scores = df.groupby('Variety')['Body'].max().sort_values(ascending=False).head(5)

# Create subplots for each category
fig, axes = plt.subplots(nrows=2, ncols=2, figsize=(12, 10))

# Top Cupping Scores
axes[0, 0].bar(top_cupping_scores.index, top_cupping_scores.values)
axes[0, 0].set_title('Top Cupping Scores by Variety')
axes[0, 0].set_xlabel('Variety')
axes[0, 0].set_ylabel('Cupping Score')
axes[0, 0].set_ylim(85, 90)

# Top Flavor Scores
axes[0, 1].bar(top_flavor_scores.index, top_flavor_scores.values)
axes[0, 1].set_title('Top Flavor Scores by Variety')
axes[0, 1].set_xlabel('Variety')
axes[0, 1].set_ylabel('Flavor Score')
axes[0, 1].set_ylim(8, 9)

# Top Balance Scores
axes[1, 0].bar(top_balance_scores.index, top_balance_scores.values)
axes[1, 0].set_title('Top Balance Scores by Variety')
axes[1, 0].set_xlabel('Variety')
axes[1, 0].set_ylabel('Balance Score')
axes[1, 0].set_ylim(8, 9)

# Top Body Scores
axes[1, 1].bar(top_body_scores.index, top_body_scores.values)
axes[1, 1].set_title('Top Body Scores by Variety')
axes[1, 1].set_xlabel('Variety')
axes[1, 1].set_ylabel('Body Score')
axes[1, 1].set_ylim(8, 9)

# Adjust layout and display the plot
plt.tight_layout()
plt.show()
```
![image](https://github.com/PouringInsights/pouringinsights.github.io/assets/100246099/4b3ce68f-2cfa-45d1-953a-6888f6a48859)

After checking some useful information about varieties, we have some names that always found in the table, now lets check where it plant: 
```python
varieties = ['Castillo', 'Gesha', 'SL34', 'Java', 'Red Bourbon', 'Sl34+Gesha']

# Filter the dataset for the specified varieties
filtered_data = df[df['Variety'].isin(varieties)]

# Get the unique countries for each variety
countries = filtered_data.groupby('Variety')['Country of Origin'].unique()

# Display the countries for each variety
for variety in varieties:
    print(f"Variety: {variety}")
    print(f"Countries: {', '.join(countries[variety])}\n")
```
Variety: Castillo
Countries: Colombia
Variety: Gesha
Countries: Taiwan, Costa Rica, Guatemala, Ethiopia, Peru
Variety: SL34
Countries: Taiwan
Variety: Java
Countries: Laos, Thailand
Variety: Red Bourbon
Countries: Colombia
Variety: Sl34+Gesha
Countries: Taiwan

It shows that the Castillo and Red Bourbon can be found in Colombia where having a lot of different varieties. Taiwan has a lot of good varieties such as Gesha, SL34. Laos and Thailand have Java varieties. 

This result shows that it is good to contact with the producers from those countries to buy their coffee and start business because some of them are quite cheap compare to the other. The real analysis about pricing would be tested in another article because of the limited resource. 
Now I would find the producer information for those varieties:

```python
varieties = ['Castillo', 'Gesha', 'SL34', 'Java', 'Red Bourbon', 'Sl34+Gesha']

# Filter the dataset for the specified varieties
filtered_data = df[df['Variety'].isin(varieties)]

# Get the unique companies and producers for each variety
companies = filtered_data.groupby('Variety')['Company'].unique()
producers = filtered_data.groupby('Variety')['Producer'].unique()

# Display the companies and producers for each variety
for variety in varieties:
    print(f"Variety: {variety}")
    print("Companies:")
    for company in companies[variety]:
        print(company)
    print("Producers:")
    for producer in producers[variety]:
        print(producer)
        
    print()

```

### Processing method 
```python
import plotly.express as px
import plotly.graph_objects as go

average_scores = df.groupby('Processing Method')['Total Cup Points'].mean().reset_index()
average_scores = average_scores.sort_values('Total Cup Points', ascending=False)

# Set the colour for the top 3 bars
colors = ['pink' if i < 3 else 'blue' for i in range(len(average_scores))]

fig = go.Figure(data=[go.Bar(x=average_scores['Processing Method'],
                             y=average_scores['Total Cup Points'],
                             marker_color=colors)])

fig.update_layout(title='Average Cupping Score by Processing Method',
                  xaxis_title='Processing Method',
                  yaxis_title='Total Cup Points')
fig.update_yaxes(range=[75, 90])
fig.show()
```
The result shows that Double Anaerobic Washed (89.33), Semi washed (87.42), Honey, Mosto(87.08) are usually having high cupping scores. It’s an interesting result because the value is high, proving excellent of the processing method. 
```python
# Group the data by processing method and calculate the average body score and flavour score
processing_scores = df.groupby('Processing Method').agg({'Body': 'mean', 'Flavor': 'mean', 'Aftertaste': 'mean'}).reset_index()

# Create a bar chart
ar_fig = px.bar(processing_scores, x='Processing Method', y=['Body', 'Flavor', 'Aftertaste'],
                 title='Comparison of Processing Method with Body Score and Flavor Score')
# Customize the plot layout
bar_fig.update_layout(
    xaxis=dict(title='Processing Method'),
    yaxis=dict(title='Score'),
    legend_title='Score Type'
)

# Show the bar chart
bar_fig.show()
```
![image](https://github.com/PouringInsights/pouringinsights.github.io/assets/100246099/42c8b337-9741-442f-a691-728e07b51de5)

The table above shows the comparison of the processing method with body score, aftertaste score and flavour score. Let's use the natural process as the benchmark because this is the most traditional method, it has a value of around 7.6 in all the attributes. Some processing methods have the difference between the 3 scores while some of them have similar scores. For example, the semi-washed method would have a higher flavour than other value while the double anaerobic washed hold a high score in the aftertaste. The Honey process is also showing a higher score of aftertaste than other methods. 

### Conclusion 
If you are reading everything here, thank you so much for reading my explanation, if not, no worries because I will save your time by summary of what I found. 
After analysing carefully the coffee quality dataset in May 2023, scrapping from Quality Coffee Institute- a non-profit organization that works to improve the quality and value of coffee worldwide, some interesting information is found. 

First of all, as expected of high-end coffee around the world, all the tasting traits have a score higher than 7/10, some values are 10 such as Sweetness, Clean Cup and Uniformity. Some important attributes such as Flavor, Balance, Body, Aftertaste, Acidity and Aroma range from 7.6 to 7.8, with flavour being the highest score and aftertaste being the lowest score, showing that high-quality coffee usually has excellent notes. However, the aftertaste is lower, meaning that it remains in the mouth not too long after drinking. The combination of notes from high-quality coffee is also good, as the score is quite high compared to the others, and the same with the body score. 

Secondly, the correlation analysis shows how these attributes relate to each other as well as the total cup point. It found that all the traits have high related to total cup points, especially the flavour. Moreover, the result shows an interesting relationship between Aroma and Body Flavor. The good smell might not give rich in body but flavour, meaning that by the smell of coffee, you can find the coffee has excellent flavour. In addition, it seems that if the coffee has a high score in flavour, it also has a high score in balance and aftertaste, allowing drinkers to get a delightful cup of coffee. 

In the exploratory of coffee origin, it found that Ethiopia secures the top position with the highest average cupping score. While this outcome is expected, it is the second and third rankings that astound with their unexpected performance. The result shows that the high-quality coffee recently is from Tanzania and Taiwan. It would be the simple result showing farmers from that country have given incredible coffee. Some key points from these taste profiles: 
* Ethiopia: citrus, often bergamot, floral through to candied fruit or even tropical fruit flavours. 
* Tanzania: complex, with bright and lively acidity, often with berry and fruity flavour. 
* Taiwan: sweet aftertaste, tea-like aroma. 

The research has found that some excellent coffee is usually Castillo, Gesha, Java, SL34, SHG, Caturra, Catimor and Ethiopian Heirlooms. Those coffee varieties have different attributes. For example: in overall: Castillo, Gesha, Java, Red Bourbon and SL34. For top flavour: Gesha, Castillo, Java, Red Bourbon and Ethiopian Heirlooms. Top Balance: Castillo, Gesha, SHG, Java, SL34. Top Body: Castillo, Gesha, Bourbon, Caturra, Catimor. The top quality coffee is usually expensive, especially Gesha or SHG. However, by finding where it has been planted, and finding a country that has many coffee varieties from the list, it could cut down the cost for coffee owners, or if you are a customer, you can easier choose coffee because the country of origin is always the first thing in the package of coffee. After running some analysis, I found that it is affordable to check coffee from Colombia, Ethiopia, Taiwan, Thailand or Laos. The processing that could be interesting besides the popular method of Natural, Washed and Honey is: Double Anaerobic washed and semi-washed. 

### Future idea 
The dataset is focused on the quality of coffee so this research is also about quality. It helps the readers understand why speciality coffee is good and breakdown all the scores of it. It's valuable for coffee shop owners to check how coffee farmers are doing and choose their producers for wholesale. It helps customers know which coffee has high quality if they are interested, and of course, not to mention the data analyst who is interested in the data insights. 

Because the dataset has no business-related score I would like to find some other information about price, the menu or some information related to a coffee shop doing as well as competitors
