# Brief Explanation:

Loads the Iris dataset from a JSON file, performs data cleaning, and calculates the average sepal width and length for each species, which are then visualized using bar plots. 
The code utilizes Pandas for data manipulation and Seaborn & matplotlib for visualization

# Code:

import json
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt

# Indlæs JSON-data fra filen
def load_json_data(filepath):
    with open(filepath, 'r') as f:
        return json.load(f)

# Indlæs data fra iris.json
dataset = load_json_data('iris.json')

# Konverter JSON-data til en Pandas DataFrame
dataFrame = pd.DataFrame(dataset)

# Udforsk dataene
print(dataFrame.head())

# Tjek for manglende værdier
print(dataFrame.isnull().sum())

# Fjern rækker med manglende værdier, hvis der er nogen
dataFrame = dataFrame.dropna()

# Beregning af gennemsnit for sepal bredder og længder for hver art
setosaSepalWidths = dataFrame[dataFrame['species'] == 'setosa']['sepalWidth']
versiColorSepalWidths = dataFrame[dataFrame['species'] == 'versicolor']['sepalWidth']
virginicaSepalWidths = dataFrame[dataFrame['species'] == 'virginica']['sepalWidth']

setosaSepalLength = dataFrame[dataFrame['species'] == 'setosa']['sepalLength']
versiSepalLength = dataFrame[dataFrame['species'] == 'versicolor']['sepalLength']
virginicaSepalLength = dataFrame[dataFrame['species'] == 'virginica']['sepalLength']

setosaAverage = setosaSepalWidths.mean()
versiAverage = versiColorSepalWidths.mean()
virgiAverage = virginicaSepalWidths.mean()

sepalLengthAverage = [setosaSepalLength.mean(), versiSepalLength.mean(), virginicaSepalLength.mean()]
averageWidth = [setosaAverage, versiAverage, virgiAverage]

species = ['setosa', 'versicolor', 'virginica']

# Visualisering af gennemsnitlig sepal bredde efter art
plt.title("Sepal Width Average by Species")
sns.barplot(x=species, y=averageWidth)
plt.show()

# Visualisering af gennemsnitlig sepal længde efter art
plt.title("Sepal Length Average by Species")
sns.barplot(x=species, y=sepalLengthAverage)
plt.show()

# Visuals
![Skærmbillede 2024-09-02 kl  12 50 54](https://github.com/user-attachments/assets/523728c5-f32f-4d51-82e6-c542b3a64914)
