## Predicting Building Electricity Consumption
# Introduction
After exploring AI through projects like the AI Trading Bot that I uploaded a few days ago and delving into sentiment analysis earlier, I wanted to tackle a core engineering and data science problem. This project moves away from financial markets and focuses on a practical, real-world challenge. The goal is to analyse building energy data, uncover the main factors driving electricity use, and build an accurate predictive model. This work showcases a complete data analysis workflow from cleaning the data to developing and improving a machine learning model.

# Project Objectives
The main goals for this project were straightforward.

* First, to take a large, messy dataset and clean it up so it is ready for analysis.

* Second, to explore the data to find any clear patterns in electricity consumption.

* Finally, to build a machine learning model that can predict a building's energy usage based on factors like the time and weather.

# Discussion and Thought Process
The project started with three separate files for electricity readings, building details, and weather data. The first big challenge was that the electricity data was in a 'wide' format with each building as its own column. This format used too much memory when I tried to reshape it. To solve this, I worked with a smaller sample of 50 buildings which made the process much more manageable.

Once the data was cleaned and merged, I moved on to exploring it with visualisations.

The first time-series plot of total energy use immediately showed a data quality problem. The readings before mid-2016 were very low and unreliable, so I filtered the dataset to only use the clean data from that point on. This plot also gave the first clue that there was a strong seasonal pattern with energy use peaking in the summer.

Next, I used boxplots to look at the daily and weekly schedules. These plots told a very clear story. Energy use drops significantly on weekends and follows a typical workday cycle from Monday to Friday. This strongly suggested the buildings in the sample were mostly commercial properties like offices or schools.

The final piece of the puzzle was understanding the impact of weather. The scatter plot below shows that as the air temperature rises above 20°C, energy consumption increases sharply. This confirmed that air conditioning is a major driver of electricity use in these buildings.

With these insights, I built an initial machine learning model using a LightGBM Regressor. The first model only used time and temperature as inputs and had a Mean Absolute Error (MAE) of 87.62. This was a good start but the error was quite high.

To improve the model, I added more features that the analysis showed were important. These included the building's size in square feet and its primary purpose like office, education, or retail. After retraining the model with this extra information, the MAE dropped to just 13.61. This was a huge improvement and showed how important feature engineering is.

The final "Actual vs. Predicted" plot shows the new model's high accuracy. The points are tightly clustered around the red line which represents a perfect prediction.

# Conclusion
This project was a success from start to finish. The analysis uncovered that a building's electricity consumption is mainly driven by its schedule, the outside air temperature, and its physical characteristics like size and purpose.

The final machine learning model was able to predict hourly energy use with a high degree of accuracy, achieving a Mean Absolute Error of 13.61. This shows that a practical and reliable model can be built from just a few key features.

# Future Works
The model is performing well but there are always ways to improve it further.

* The analysis could be scaled up to include all the buildings in the dataset instead of just a sample.

* More features could be added, like humidity and wind speed from the weather data, or even public holiday information.

* The model's internal settings could be tuned to see if the error can be reduced even more.
