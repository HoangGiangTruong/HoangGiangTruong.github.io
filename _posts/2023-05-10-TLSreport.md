---
layout: post
title:  "Performance Dashboard for in-game guild Strategy"
author: Sep
categories: [ Excel, Spreadsheet ]
image: assets/images/maple1.jpeg
beforetoc: "Why am I passionate about creating dashboards for this guild? What sets TheLostSocks apart from the rest? Is there something truly unique and impactful about it? Well, all the answers lie right here, where everything will be unveiled and presented in one place."
toc: true
featured: true
hidden: true
---

Introducing the ultimate guild management companion: a dynamic weekly update dashboard for Maple Story M. Stay on top of activities, set goals, and access invaluable insights to foster motivation and create a welcoming guild atmosphere.

The dashboard showcase is available [here](https://docs.google.com/spreadsheets/d/e/2PACX-1vRfE01WV3VvT1nJbXA9RHHUCI62DCtKBRM0lCH7YLpGpVr6eERto3_x7OKrPgOvhhwZCxsxDXWYfR4B/pubhtml?gid=1968448146&single=true).

## Key skills

Data Manipulation, Data Cleaning, Data Validation, Business logic, Data story telling 

The function that I used most in this dashboard is INDEX- MATCH and conditional formating, it makes immediately impact to the readers  

## Introduction

Maple Story M has been established in 2017, but it was first published in 2003 as an online MMORPG (massively multiplayer online role-playing game) by Nexon company. It is an attractive game that is free to play, 2D, with "cute animation characters". It doesn't really have a PvP function but only defeats or hunts monsters to develop characters' skills. With an amazing story for each character and the game's main plot, players can enjoy the game in multiple ways, including chatting and trading. 

In this matter. I could call the selling point for the game about ability to socialise. The game successfully creates a social environment where players can enjoy fighting concepts, communicate with other players, and buy fashion that makes them look good. The game has satisfied players' needs. If I could use the business term to analyze it, I would demonstrate it in Maslow's model: 

- Belongingness: Connect with others, join communities, and form friendships.
- Esteem: Gain recognition, achieve goals, and boost self-confidence.
- Socialization: Chat, cooperate, and celebrate with fellow players.
- Safety: Enjoy a secure and controlled virtual environment.
- Self-Actualization: Express creativity, pursue personal growth, and fulfil achievements.
- Cognitive and Aesthetic: Engage in intellectually stimulating quests and appreciate visually appealing graphics.

TheLostSocks- however, being #4 in the server demonstrates the competitive strength. However, they have a balanced playstyle which is unique for the server, allowing members can have a more relaxed, chill atmosphere while still can archive higher competitive content in the game. 

## TheLostSocks SWOT analysis 

I was mentioning Maslow's model, so here is the SWOT analysis of this guild. I drafted it so I could find something useful for the dashboard

![image](https://github.com/HoangGiangTruong/hoanggiangtruong.github.io/assets/100246099/c78b75d0-acdf-42b5-8891-985615b4c82c)

![image](https://github.com/HoangGiangTruong/hoanggiangtruong.github.io/assets/100246099/7579aeb3-816a-4fa4-8536-688108caa235)

![image](https://github.com/HoangGiangTruong/hoanggiangtruong.github.io/assets/100246099/6c90a6cc-2c78-4b11-937e-ccf7f344a713)

![image](https://github.com/HoangGiangTruong/hoanggiangtruong.github.io/assets/100246099/f267de1a-0d20-4983-911a-f9020bcf9806)

Now I know our guild's strengths and weaknesses. I figure out that it is quite hard to keep strong players for better content without making them burn out so collaborating with another guild should be considered for higher content. This solution affects them to be competitive while not feeling an obligation to be strong if they have to move to a stronger guild for content. 

However, the new players would feel lost if there are no mentors or motivation for them to play so the social activity and guidance as well as the checkup for progression would motivate them for sustainable growth. 

## Data Exploration

To evaluate the guild strength, there are several ranking systems within the game, so that any players could know how they work as a guild. Ok, if that is the case, I don't need to think about this. Understanding that every guild has different purposes and they're set up for the activities. I would list out some key points from our competitors: 

* Endeavor: Targeting for the top 1 in the server, high requirement, whaling, and DPS is the priority. Managing high content, people usually solo for their lower content. 
* Exploits: Also aiming for top 1 in the server, direct competitive with Endeavor. The difference between them is while Endeavor is born to be top 1, Exploits organized to take the title and they did it. The endeavour would find some other solutions to attract whale or high-end equipment players to take the top 1 back. 
* MapleSatori: This guild is special, as the direct competition with TheLostSocks since the beginning, with the background story which makes them become our competitor. At the moment, after the merger with Union, they formed a big community where MapleSatori is the ranking guild and Union is the chilling guild. This concept is unique to them. However, in my opinion, I just don't like the concept 

There are multiple guilds out there, but if we perform well, we wouldn't be a threat to them. So, what kind of data should I use to make an in-depth analysis for the guild? and who is my audience. 

The game has 2 main focusing content in the competitive field: guild content and boss content. 

For guild content, multiple concepts would rank the guild base on group performance and individual performance. 
For boss content, there are a lot of bosses but depending on gears, players can access different bosses with different difficulty 

That is the case, so the data I need have to be easy to access for guildies without restriction, showing their progression over time as well as reflecting guild strength. The culvert score is the perfect match for my idea because it is the personal score, weekly ranking, and high reward so it would attract players to play it. 

I asked my guildmate- Ven to record the data entry for them. He posted it in the spreadsheet file and there are where I showcase my data analytical skills. 

The first purpose of this part is to show who is performing well in the guild for Management. Guild leaders could see people's progress so they could decide it. I want to make it faster so that I create an interactive table that filters out who doing low damage. 

But there is a high range of scores between members, after observing performance for few months, we decided the benchmark would be 3000 because it is an easy score for higher than level 200 players to achieve. For the player that has level lower than 200, don't worry about it, because it takes them just about a few months to reach level 200 without putting too much effort into it. 

The table showed the top 5 lowest scores each week, and in the main data table, I choose to use conditional formatting for colour to filter out the low scores as dark red colour and the qualified score as dark blue colour. 

In addition, Ven updated the boss score- Chaos Crimson Queen as the benchmark for dps. I found it useful because the boss has average difficulty and could be a good benchmark for a variety of references. Eventhough it's just an approximate value so it is not always correct because the variable of team members within the run could be considered. Still, it is the good one to check dps for higher content while the culvert score is better to evaluate all guild members' performance. 
While trying to analyze boss dps for players, I found an issue with Ven's input, his input is in string form instead of an integer. Here we go, I need to clean this. His input looks like this: 700M or 1.4B referring to 700,000,000 dps and 1,400,000,000 DPS. The issue is it is not only in string format, but it is also included both numbers and characters at the same time, and the calculating for each case is different, and I need them in the same types as well as the same format. 
In this case, I would have 2 options, 1 is to rework the input, and 2 is to transform the data into the same format. As a lazy person, of course, I go with a harder choice :). Oh, the actual reason is 1, I want to do data cleaning and 2, I am not the one who does the input, it's Ven, how could I help him do it as he likes but I still have the perfect input to generate insights? So I write a function that would delete the ending and multiply with 1m if the ending is "M" and multiply with 1b if the ending is "B" in the next column, I hide it from Ven so he won't be confused. 

Therefore, I have top players in the guild. I also add some charts to manage guilds such as total main players or dps categories for organizing boss-run content. 

The sheet would run automatically whenever Ven adds new content weekly, leading to low effort for him (and for me). Again, I have to mention that I am lazy so I want to optimise my time and performance as much as possible. 

## Dashboard  

I showed the spreadsheet to the leader's team, and they found it useful, and the leader wants to show it to guildies so they could know their progress of themselves. Now I have another audience: Guild members
By targeting guild members as my audience, I decided to make a dashboard, which briefly shows weekly records and some descriptive analysis for them to see. Some details I didn't post in the dashboard because it is more for management, not for members. The purpose of the dashboard is to help guildies track their record, and summary what happened in the guild for the last week/month. This dashboard must not look like a company record because this is a game, and we play games for fun, not for work. 

Moreover, the guild has many players with different origins, ethnic, and religions, let's respect everyone and show a good vibe when they see the dashboard. Some questions that I need to solve to understand my audiences:
- What makes them enjoy the insights from me? 
- If they got a bad score, would it offend them? 
- How could I notice some people progressing so they could feel they are doing well? 
- Is it ok if I only show a good table and ignore bad performance? 

Ok so after reviewing all the questions I finally found the way to do this, with the help of brainstorming from guild leaders: 
- First of all, I summarised guild performance- our ranking, the targeting for the guild by calculating the approximate score that we need to achieve in the future, the guild's overall level and dps. 
- Secondly, I distribute the "Hall of Fame", this is where our strongest players of all time show up, can call them the top 10, the elite or what so ever. 
- Thirdly, the champion of the week/month would show who has higher performance for the week/ month. This result was shown for management by calculating the difference between each member's score. 
- Next, I distribute a table called "Slackers": This table compares member scores with their previous best, and the table name is not serious, making people not offended when seeing their name here. 
- Then, the luckiest of the week/month would generate a random function for players that meet some criteria, I found this function quite challenging because it has so many criteria for the if function, but it finally worked so Im proud of myself. 
- Last but not least, the small line chart is showing their progress during the month. It is so powerful that members can track their scores without seeing numbers. The number would make me offended and it is in the game function, why do I need to input here for 1 min reading dashboard? 
- At last, I spend some space for the weekly recap. With the help of the discord server, we have a Flex channel where people posted their updates from the game (and some luxury activities as well), I could filter the date and time and copy the content to the dashboard. 

Finally, I published it to the website base and let people enjoy it. After running for 1 month, I found it helps the guild increase the performance by around 30%, leading to the targeting being closer than ever!!! The outside game activities and the guild discord are also having a lot of chat, and everything could be included in the weekly recap. It directly shows how guilds perform in both competitive and chilling. The retention rate is quite high because I see no sign that our strong players would leave, and the new members are going to stay and increase their bonding with the guild better. 

I hope you enjoy this article about excel and the "business logic" on it 




