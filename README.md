### Tripleten Code Jam 2024

This is a project created for the June 2024 Code Jam at Tripleten. It was created using HTML, CSS, and Javascript, based on a given design brief.

Created by the Redwood Rangers: Grace Persion, Laura Ferguson, Mike Twersky, and Dale Myers

## Project Features

- Responsive design for desktop, tablet, and mobile views
- CSS Grid
- Hover effects with transitions
- Flat BEM file structure and organization
- Interactive data visualization

## Link

You can view and interact with the site here: https://g-dilek.github.io/Tripleten-Code-Jam-2024

### Results

## Introduction

The data collected and used for this project was downloaded from Kaggle. It can be accessed here. Collected through scraping, The dataset contains information on all 63 US national parks.

The data includes:

• park names
• locations in state and latitude and longitude
• a description of each park
• the area of each park as of 2021, in acres
• the number of visitors in 2021
• the date each park was established

Before we could analyze the data, preprocessing was required. Each row in the data set represents a park. There were no duplicate values. The ‘Image’ and ‘Unnamed’ columns were empty and meaningless, so they were dropped. Then, the columns were renamed to fit style guidelines. We then used a locate to reduce the data set down to the 9 parks located in California. The date the park was established was then converted from a string to datetime format.

Next, feature engineering was required to extract the latitude and longitude as numeric data types from the location columns. We created a new dataframe named location to split the state name from the coordinates, split the coordinates into two new columns, and wrote a function to convert the coordinates from minute format to degree decimal format. Finally, these new formatted longitude and latitude columns and state columns were added back to the original dataframe, and the original location column was dropped.
After that, the name and state columns were further cleaned.

## Visualizations

Our first visualization plots the year each park was established, the number of visitors in 2021, and allows the end-user to toggle which park is being viewed. This scatterplot shows visually the lack of a relationship between the age of the park and its number of visitors in the year 2021.

The second visualization viewable is a regplot showing the minimal correlation between the size of each park and its number of visitors in 2021. This correlation coefficient was found to be .228, little to no correlation. As the size of each park in acres gets bigger, the number of visitors in 2021 only very slightly increases, if at all.

The next visualization plots the location of each of the 9 national parks on a US map. The size of each point correlates to the popularity of each park in 2021, while the color code corresponds to the dataframe index of each park. The end-user can toggle which indices are viewable at a time and deduct visually and numerically each parks popularity.

## Model

To prepare the model, we first created a distance matrix. This is a matrix of all distances between each park. To create it, we first wrote a function to get those distance from the latitude and longitude coordinates using the OSRM API. We then took those distances and put them into a second function that returns a distance matrix. Finally, the values of the distance matrix were converted to an array so that it could fed into the model.

The approach that we took was the brute force method. This method calculates all possible combinations of routes between all the parks, without going to the same park twice, and returns the optimal order and shortest total distance travelled. To implement the brute force method, we used the python TSP library’s solve_tsp_brute_force package.

## Conclusion

The optimal route determined using the brute force method was as follows:
Channel Islands > Joshua Tree > Death Valley > Yosemite > Lassen Volcanic > Redwood > Pinnacles > Sequoia > Kings Canyon.
The total distance traveled over this route is 3,925,723 meters, or 2,439 miles.
