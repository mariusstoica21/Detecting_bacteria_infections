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
    src="https://github.com/mariusstoica21/Detecting_bacteria_infections/blob/main/images/architecture2.PNG"
    width = "1500"
    height = "200"
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

A prediction was made based on the test set (10 samples). The results are as followed: from the 10 test samples, only one was correctly predicted.

<p align="center">
  <img 
    src="https://github.com/mariusstoica21/Detecting_bacteria_infections/blob/main/images/results1.PNG"
    width = "800"
    height = "auto"
  >
</p>

The results are pretty close to be correct. For instance, the prediction of the first sample from the test set was Pyoc_0, AeB_0, EnB_25, while the test set had PyoC_0, AeB_25, EnB_25. For the second sample from the test set, the prediction was PyoC_50, AeB_25, EnB_0, while the test set had PyoC_25, AeB_100, EnB_0.

<p align="center">
  <img 
    src="https://github.com/mariusstoica21/Detecting_bacteria_infections/blob/main/images/results2.PNG"
    width = "800"
    height = "auto"
  >
</p>

Accuracy is 0.1, since, from the 10 test samples, test sample 5 was correctly predicted.

<p align="center">
  <img 
    src="https://github.com/mariusstoica21/Detecting_bacteria_infections/blob/main/images/results3.PNG"
    width = "400"
    height = "auto"
  >
</p>


### Icons

<ul>
  <li><a href="https://www.flaticon.com/free-icons/bacteria" title="bacteria icons">Bacteria icons created by Good Ware - Flaticon</a></li>
  <li><a href="https://www.flaticon.com/free-icons/urine-test" title="urine test icons">Urine test icons created by Freepik - Flaticon</a></li>
  <li><a href="https://www.flaticon.com/free-icons/blood" title="blood icons">Blood icons created by Freepik - Flaticon</a></li>
  <li><a href="https://www.flaticon.com/free-icons/serum" title="serum icons">Serum icons created by Good Ware - Flaticon</a></li>
</ul>
