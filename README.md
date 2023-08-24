# League of Legends Jungler Pathing Location Heatmaps in High Elo Games
Using data found on Kaggle to predict the jungler player's movements in the first few minutes of the game in high elo games using heatmaps.

## Dataset

https://www.kaggle.com/datasets/lawsus/lol-interpolated-positions

## Technology

### Python libraries: 

pandas (pd), matplotlib, OpenCV (cv2), numpy (np).

### Jupyter Notebook

## Dataset

### combined_interpolated_data.csv

## Quick Explanation of the Game League of Legends

### League of Legends is a popular multiplayer online battle arena (MOBA) game where two teams, each composed of five players, compete to destroy the enemy's Nexus, the core building in their base.

### Each player is assigned a role that they queue up for before a match, these five roles are as follows:

* Top Laner

* **Jungler**: The jungler roams the map and defeats monsters that spawn in the jungle. Their main role is to gank lanes to assist players in the lane.

* Middle Laner

* ADC

* Support

## Limitations of Data

Since the data is generated using the Riot API, the API only tracks the location of players in a "frame" which is every 60 seconds. For our data, this means that every 60th entry in the interpolated values is the most accurate portrayal of the player's location. Due to the nature of League of Legends fast-paced gameplay, junglers can move very quickly around the map in 60 seconds. In between each frame, junglers in the game have many options for objectives and assisting other players in the game. This volatile gameplay makes tracking players later in the game very difficult as one team gaining an advantage shifts the players towards one side of the map (top right or bottom left).

![image](https://github.com/francotaboada/LoL-Jungler-Location-Heatmap/assets/18605940/045a2e75-4a09-486c-8a8a-d275497277b2)

> In the scatterplots above, you can see how in most cases the blue-side jungler and the red-side jungler both stay on their side of the map at the 3-minute mark but quickly become more scattered out as time progresses.

