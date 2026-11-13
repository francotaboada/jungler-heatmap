# League of Legends Jungler Pathing Location Heatmaps in High Elo Games
Descriptive analysis of early-game jungler positions (minutes 0-7) in 287 high-Elo League of Legends games, using position scatterplots and heatmaps over a map of Summoner’s Rift. This project describes where junglers go. 

## Dataset

[combined_interpolated_data.csv](https://www.kaggle.com/datasets/lawsus/lol-interpolated-positions)

## Technology

### Python libraries: 

pandas (pd), matplotlib, OpenCV (cv2), numpy (np).

### Jupyter Notebook


## Quick Explanation of the Game League of Legends

League of Legends is a popular multiplayer online battle arena (MOBA) game where two teams, each composed of five players, compete to destroy the enemy's Nexus, the core building in their base.

### Each player is assigned a role that they queue up for before a match, these five roles are as follows:

* Top Laner

* **Jungler**: The jungler roams the map and defeats monsters that spawn in the jungle. Their main role is to gank lanes to assist players in the lanes.

* Middle Laner

* ADC

* Support

The jungler player usually starts in the jungle, which is in between the three lanes (top, middle, bottom), at the buff which either gives mana regeneration or health regeneration with a few more bonuses. After this buff is taken, players have a lot of leeway in the progression of their path to victory. Early game tracking on both sides is essential since decisions in the early game can determine the entire game. Being able to guess where the enemy jungler is allows for a huge advantage.
# Data
![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/6378e38e-6775-4b6b-8999-f006d11924c1)
The CSV file is separated into MatchID, Time, PlayerN Positions (x,y), Distance Between Players, and a Teamfight Flag. The fields that I focused on were MatchID and the positions of Player2 and Player7 (blue side and red side junglers, respectively).
# Graphs
In the section below are the graphs created using the dataset.
## Raw Scatterplots
This scatterplot was created using every 60th data point in the dataset to see the accuracy of the background map chosen for the players Player 2 and Player 7 (blue side and red side junglers, respectively). As seen below, the map is not perfect but gives a good example of the map being more accurate than not. Game coordinates are divided by 10 and the Y axis is flipped (Y = 1500 - Y/10) to fit a 1500x1500 map image. This is a straight linear rescale with no calibration, so the overlay is approximate.

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/6be9f53b-9350-4f38-b2e8-081f540ae752)


### Blue Side Scatterplots
Using Player2_X and Player2_Y, scatterplots can be created based on the blue-side junglers' position by the minute. These scatterplots go from minute 0 (the start of the game) to minute 7.

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/6cfdff0b-2296-4cf5-9157-811bbcffb708)

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/12b49e03-afb5-467b-80c9-137daeed93c9)

### Red Side Scatterplots
Using Player7_X and Player7_Y, scatterplots can be created based on the red-side junglers' position by the minute. These scatterplots go from minute 0 (the start of the game) to minute 7.

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/6094c8d5-be8d-4a03-80cf-d0b6a47f551a)

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/a215ad54-a8df-49fa-a810-ac3c942f1758)

### Scatterplots Based on Starting Location
Starting side is inferred from each jungler's position in the minute-2 frame: positions on the upper-left side of the diagonal through the middle lane are classed top-start, all others bottom-start. Every game is assigned to one group, so junglers not on a normal clear path at 2:00 may be misclassified. Group sizes: blue top [n], blue bot [n], red top [n], red bot [n]. Colors: dark blue = blue/top, blue = blue/bot, red = red/top, medium violet red = red/bot.

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/546e3aaf-3f7d-4792-825f-155bf7f3171d)

#### Blue Side Starting Top Side
Scatterplot that logs the positions of the blue-side junglers starting the top side buff around two minutes. At the three minute, you can see that most junglers go from the top side to the bottom side. This is different from those who start at the bottom side as you will see in the next section.

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/ddd6d2f1-5b41-44c1-9595-ad87a8418adc)
![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/050e6c79-6dd5-4a96-916b-7362d000cf2c)


#### Blue Side Starting Bot Side
Scatterplot that logs the positions of the blue-side junglers starting the bottom side buff around two minutes. As opposed to the junglers who start top-side, junglers are more volatile in their positioning after they get their jungle camps on the bottom side of the map. This can be observed in the lack of density at minute 3 as compared to the scatterplots above.

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/92b5674f-8b62-414f-a64a-85afb779d1be)
![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/de216003-2241-4eda-ae4b-9307b1177266)

#### Red Side Starting Top Side
Scatterplot that logs the positions of the red-side junglers starting the top side buff around two minutes. At the three minute, you can see that most junglers go from the top side to the bottom side. The same result as the blue-side top-side starting junglers.

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/91ac6917-823e-405f-a981-1ce4bcdb65e9)
![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/7d517e5a-6cbb-4bf2-b636-57861670af92)

#### Red Side Starting Bot Side
Scatterplot that logs the positions of the blue-side junglers starting the top side buff around two minutes. Different from the blue-side bottom-side junglers, the red-side junglers who start on the bottom side will most likely go to their top-side camps instead of going on a more erratic path. The groupings are more dense making them more uniform.

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/a359ba2e-962e-4fbe-83cc-92a89aed4a94)
![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/4e45ab37-6d32-4a7b-8d84-0634a1a0a343)

## Jungler Heatmaps
The heatmap below shows the positions of Player2 and Player7 (the blue- and red-side junglers) in all 287 games, using 16-pixel bins and counting every 60-second frame after the first.

![allmatchesgraph](https://github.com/francotaboada/jungler-heatmap/assets/18605940/422b989c-13e0-4fd5-81c9-9604368500fc)

Here is the heatmap superimposed onto the map of the summoner's rift.

![allmatchesgraph_superimposed](https://github.com/francotaboada/jungler-heatmap/assets/18605940/07d5f642-f0e7-45f1-9e41-5b6fc9c958b0)

### Blue Side Heatmaps
Match-long heatmap for the blue-side jungler.

![bluematchesgraph](https://github.com/francotaboada/jungler-heatmap/assets/18605940/acd9fdcf-36e2-4f16-9f0e-d7a3363cfcd2)

Heatmap based on the positions at minutes 0-7.

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/c57b1990-78c3-4507-a790-f528d6622926)

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/33ffef1a-5edd-4880-85aa-5e0a1ea062d4)


### Red Side Heatmaps
Match-long heatmap for the blue-side jungler.

![redmatchesgraph](https://github.com/francotaboada/jungler-heatmap/assets/18605940/18f7320f-7639-4e11-a6c7-07449da96b9f)

Heatmap based on the positions at minutes 0-7.

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/fbddceb6-80ff-41de-a329-444f8a893467)

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/90b3f373-730f-4380-9bb5-f189d4f56113)


## Limitations of Data

The Riot API records player positions once per 60 seconds. The dataset adds interpolated positions between frames, and this analysis uses every 60th row, assuming 60 rows per frame, as the real observations.

![image](https://github.com/francotaboada/jungler-heatmap/assets/18605940/744ef681-4630-4c1d-861e-978dda690fc3)

> In the scatterplots above, you can see how in most cases the blue-side jungler and the red-side jungler both stay on their side of the map around the 2-minute mark but quickly become more scattered out as time progresses.

