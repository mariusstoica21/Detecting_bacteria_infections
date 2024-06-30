<p align="left">
  <img 
    src="https://github.com/mariusstoica21/Detecting_bacteria_infections/blob/main/images/header.png"
  >
</p>

# Detecting Bacteria Infections from Hospitals using Electrochemical Sensors and a Decision Tree Classifier Solution

The objective of the application is to classify the bacteria siderophores (Pyociannina, Aerobactin, Enterobactin), and determine their concentrations.

A sample (urine or blood) is applied on the electrode (OMC, MC, Graphite, Graphene) of an electrochemical sensor. The sample is dilluted with one of the following solutions: PBS, Undilluted serum, Serrum diluted 1/2, Serrum diluted 1/5, Serum dilluted 1/10. The sollution that provides the highest discriminating coefficient is used. 

After applying the sample and sollution, the electrochemical sensor will provide a plot, having the following axis:

- X: X/V
- Y: Y/µA

Using this plot, the following features are extracted:

- Max Peak
- Number of Peaks
- Area under the curve

<p align="center">
  <img 
    src="https://github.com/mariusstoica21/Detecting_bacteria_infections/blob/main/plots/E1.png"
    width = "300"
    height = "auto"
  >
</p>

These features represent the input of the decision tree classifier. 

The output features of the decision tree classifier consists of the following combination:

- PyoC_0  
- PyoC_25 
- PyoC_50 
- PyoC_100
- AeB_0    
- AeB_25 
- AeB_50 
- AeB_100  
- EnB_0    
- EnB_25   
- EnB_50   
- EnB_100

A sample that contains 0 mmol of PyoC, 0 mmol of AeB and 0 mmol of Enb would be one-hot encoded like this:

- PyoC_0:   1	
- PyoC_25:  0	
- PyoC_50:  0
- PyoC_100: 0
- AeB_0:    1	
- AeB_25:   0	
- AeB_50:   0
- AeB_100:  0
- EnB_0:    1	
- EnB_25:   0	
- EnB_50:   0
- EnB_100:  0

Data has been provided by Iuliu Hațieganu University of Medicine and Pharmacy. 

## Architecture

<p align="center">
  <img 
    src="https://github.com/mariusstoica21/Detecting_bacteria_infections/blob/main/images/architecture3.PNG"
    width = "700"
    height = "450"
  >
</p>

## Installation
In order to run the scripts from the Demo folder, Jupyter Notebook shall be installed.

## Summary
✅ G.U.I. 

✅ Ease of installation

❌ Additional hardware needed

## Project description

### Folder structure

📁 data : contains the information needed in order to train the decision tree classifier.
- 📄 [Data.xlsx](https://github.com/mariusstoica21/Detecting_bacteria_infections/blob/main/data/Data.xlsx): read the samples (50 samples) used in order to train (40 samples) and test (10 samples) the decision tree classifier.

📁 demo: contains the demo version script, that shows how a sample from the training set looks like (plot generated after applying the combination of blood/urine sample and serum sollution).
- 📄 [Start.ipynb](https://github.com/mariusstoica21/Detecting_bacteria_infections/blob/main/demo/Start.ipynb): script that reads data from the Data.xlsx file (only one sample), plots the information (only one sample), extracts the key features from the plot (max peak, number of peaks, area under the curve), loads the decision tree classifier model and predicts the training sample, based on the model.

📁 model : contains the model (weights and biases) of the decision tree classifier
- 📄 [model.pkl](https://github.com/mariusstoica21/Detecting_bacteria_infections/blob/main/model/model.pkl): pickle file that contains the model of the decision tree classifier. the model is loaded, when needed to be used.

📁 original : contains the original version, that uses the excel file with all the 50 samples (data could not be provided due to confidentiality reasons) in order to train and test the decision tree classifier.
- 📄 [Start.ipynb](https://github.com/mariusstoica21/Detecting_bacteria_infections/blob/main/original/Start.ipynb): script that reads data from Data.xlsx file, (all the 50 samples), plots the information, extracts the key features from the plot, one-hot encodes the output, splits the data into training and testing set, trains a decision tree classifier and predicts the test sample.

📁 plots : contains an image, with a plot. the plot contains on the X axis () and on Y axis (). based on the plot, the main features (max peak, number of peaks, area under the curve) were extracted.

### Technologies

<table>
  <tr>
    <th>🔨 Tools/Framework</th>
    <th>📘 Language</th>
    <th>📃 Usage </th>
    <th>➕ Additional resources  </th>
    <th> ℹ Details  </th>
  </tr>
  <tr>
    <td>Jupyter Notebook</td>
    <td>Python</td>
    <td>Data Cleaning, Decision Tree Classifier</td>
    <td>Tensorflow</td>
    <td>
       <ul>
        <li>Read the Excel file that contains the information for each sample of the training and testing set (50 samples), one-hot encoded</li>
        <li>Parse information into dataframes</li>
        <li>For each sample, extract the key features (number of peaks, max peak, area under the curve)</li>
        <li>One-hot encode the output.</li>
        <li>Split the dataset into training set (40 samples) and test set (10 samples).</li>
        <li>Apply the decision tree classifier.</li>
        <li>Predict the test set and interpret the results.</li>
      </ul>
   </td>
  </tr>
</table>

### Results



### Use-case

As an example, we suppose a football club from Romania has a transfer budget of 2.0 million dollars in order to buy a striker. The club decides to buy a young striker, therefore the following filters are used:
<ul>
<li>Price is at most 2 mil. dollars</li>
<li>Age is at most 23 years old</li>
</ul>

The neural network displayed a number of football players that matched the criteria, and there are 3 of the possible transfers:

Borja Iglesias, currently playing at Bayer Leverkusen, has previosly played for Espanyol Barcelona and Betis Sevilla. Had a value of 1.7 mil. dollars, with a predicted value of 12 mil. dollars. 

<p align="center">
  <img 
    src="https://github.com/mariusstoica21/Football_Manager_2012/blob/main/Images/img11.PNG"
    width = "800"
    height = "auto"
  >
</p>

Iago Aspas, played most of his time at Celta Vigo. He was also capped for Spain national team, where he has 20 matches. Had a value of 0.8 mil. dollars, with a predicted value of 4.4 mil. dollars. 

<p align="center">
  <img 
    src="https://github.com/mariusstoica21/Football_Manager_2012/blob/main/Images/img12.PNG"
    width = "800"
    height = "auto"
  >
</p>

Ashley Barnes, currently playing at West Ham. He is an England international player. Had a value of 0.3 mil. dollars, with a predicted value of 3.3 mil. dollars. 

<p align="center">
  <img 
    src="https://github.com/mariusstoica21/Football_Manager_2012/blob/main/Images/img13.PNG"
    width = "800"
    height = "auto"
  >
</p>

The total sum needed to acquire all of these players was 2.8 mil dollars. The predicted price of all these 3 footballers was approx. 20 mil dollars. Of course, it is hard to believe that these young prospects would have come to Romania, and also the price needed to pay would have been a little bit higher. But, this use-case could be used as a proof that the neural network outputs valuable players, at a cost lower than it should be.

### Icons

<ul>
  <li><a href="https://www.flaticon.com/free-icons/goal" title="goal icons">Goal icons created by Freepik - Flaticon</a></li>
  <li><a href="https://www.flaticon.com/free-icons/runner" title="runner icons">Runner icons created by Leremy - Flaticon</a></li>
  <li><a href="https://www.flaticon.com/free-icons/jump" title="jump icons">Jump icons created by Leremy - Flaticon</a></li>
  <li><a href="https://www.flaticon.com/free-icons/goalkeeper" title="goalkeeper icons">Goalkeeper icons created by Muhammad_Usman - Flaticon</a></li>
  <li><a href="https://www.flaticon.com/free-icons/inspiration" title="inspiration icons">Inspiration icons created by photo3idea_studio - Flaticon</a></li>
  <li><a href="https://www.flaticon.com/free-icons/brain" title="brain icons">Brain icons created by Freepik - Flaticon</a></li>
  <li><a href="https://www.flaticon.com/free-icons/dollar-sign" title="dollar sign icons">Dollar sign icons created by Freepik - Flaticon</a></li>
  <li><a href="https://www.flaticon.com/free-icons/hourglass" title="hourglass icons">Hourglass icons created by Freepik - Flaticon</a></li>
  <li><a href="https://www.flaticon.com/free-icons/prediction" title="prediction icons">Prediction icons created by Parzival’ 1997 - Flaticon</a></li>
  <li><a href="https://www.flaticon.com/free-icons/profit" title="profit icons">Profit icons created by nawicon - Flaticon</a></li> 
</ul>
