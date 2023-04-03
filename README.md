# Heart_Attack_analysis 

This dataset is obtained from Kaggle. It consists of multiple features which are recorded during diagnosis of patients and which are then used to 
find the probability of a person having a heart attack; 0 => Low probability, 1 => High Probability

-- About the dataset -- 

Age : Age of the patient

Sex : Sex of the patient

exang: exercise induced angina (1 = yes; 0 = no)

ca: number of major vessels (0-3)

cp : Chest Pain type chest pain type

Value 1: typical angina Value 2: atypical angina Value 3: non-anginal pain Value 4: asymptomatic

trtbps : resting blood pressure (in mm Hg)

chol : cholestoral in mg/dl fetched via BMI sensor

fbs : (fasting blood sugar > 120 mg/dl) (1 = true; 0 = false)

rest_ecg : resting electrocardiographic results

Value 0: normal Value 1: having ST-T wave abnormality (T wave inversions and/or ST elevation or depression of > 0.05 mV) Value 2: showing probable or definite left ventricular hypertrophy by Estes' criteria thalach : maximum heart rate achieved

target : 0= less chance of heart attack 1= more chance of heart attack


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

1. Observation and initial analysis

![image](https://user-images.githubusercontent.com/77953290/229472614-bf4a78a8-a122-440f-97ee-9bfba12cc1c4.png)


2. ![image](https://user-images.githubusercontent.com/77953290/229472799-2391841d-16bd-4d84-9c21-393cc9296a32.png)

![image](https://user-images.githubusercontent.com/77953290/229472883-3ca368c9-c8a3-4e4f-ab17-87cfa4c0f44f.png)


3. Plotting the same in a missing plot, to get a good overview:

![image](https://user-images.githubusercontent.com/77953290/229473027-762cd961-ab28-428f-b11c-a8315c37ba1f.png)

4. Checking distribution of variables

![image](https://user-images.githubusercontent.com/77953290/229473206-251947b0-6bd1-45ed-a82e-48d3b1511ea7.png)

![image](https://user-images.githubusercontent.com/77953290/229473281-83219df7-2afe-4a76-8908-e7d28bb10d17.png)


-- Univariate Analysis --

title_font = { "family":"arial", "color":"red", "weight":"bold", "size":15   }
axis_font = {   "family":"arial", "color":"blue", "weight":"bold", "size":10    }

numeric_axis_name = ["Age of Patient", "Resting Blood Pressure", "Cholestrol", "Maximum heart rate achieved", "ST Depression"]
list(zip(numeric_var.index, numeric_axis_name)) #Zipping values together to run in for loop

for i,z in list(zip(numeric_var.index, numeric_axis_name)): #i will store index values, whereas, z will store modified values
  plt.figure(figsize = (8,6), dpi = 80)
  sns.distplot(df[i], hist_kws = dict(linewidth = 1, edgecolor = 'k'))

  plt.title(i, fontdict = title_font)
  plt.xlabel(z, fontdict = axis_font) #We customized the x-label
  plt.ylabel("Density", fontdict = axis_font)
  plt.tight_layout()
  plt.show()


![image](https://user-images.githubusercontent.com/77953290/229473620-e1d30d0b-7f21-469c-842d-381bea7fb027.png)


![image](https://user-images.githubusercontent.com/77953290/229473685-c07b8bf3-2593-41d8-a93b-6b751373b5d6.png)


![image](https://user-images.githubusercontent.com/77953290/229473740-5632594d-5ae6-4198-b574-adc11b0cbdbf.png)


![image](https://user-images.githubusercontent.com/77953290/229473776-0c17d2fa-e136-4da7-bee2-780cb821fdee.png)


![image](https://user-images.githubusercontent.com/77953290/229473824-61ab820d-7fc3-4c33-a903-9ab77bb75d63.png)


Analysis

Age: There is a decrease in patients (against the trend) b/w ages 47-50,for reasons not yet known and no outliers
Resting blood pressure: Values between 110 - 140, with some outliers
Cholestrol: Some outliers
Heart rate: Values before 80 are outliers
ST depression: Within this variable, the values range from 0-1.5 and after 2.5, we can say that they are outliers


Using pie chart for categorical feature plotting

![image](https://user-images.githubusercontent.com/77953290/229474120-dd39725d-55ca-490d-88c3-d1a9c7a08568.png)


![image](https://user-images.githubusercontent.com/77953290/229474166-1a57fe27-f1c8-400b-b5db-005c45f28d53.png)


![image](https://user-images.githubusercontent.com/77953290/229474213-1d3a6bfa-84c3-4512-939c-4a134fff1fc6.png)


![image](https://user-images.githubusercontent.com/77953290/229474261-672637d7-9c9e-4f8e-96b1-c98787e92b80.png)


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-- Bivariate Analysis (Numerical features) --

![image](https://user-images.githubusercontent.com/77953290/229474613-e3f0017b-a4de-4bc6-8436-58af56c9e86b.png)

![image](https://user-images.githubusercontent.com/77953290/229474947-326861ae-1875-4288-ba9c-45509600e691.png)

![image](https://user-images.githubusercontent.com/77953290/229475072-da3f31cc-e76e-41a1-9992-2f62770e96dc.png)

![image](https://user-images.githubusercontent.com/77953290/229475114-f6790de7-587a-4185-9c62-26957d35c851.png)



-- Bivariate Analysis (Categorical features) --

Using countplot, to analyze the categorical features with target variable

![image](https://user-images.githubusercontent.com/77953290/229475475-08e4403a-eeb8-497e-884e-3e30502edbed.png)

![image](https://user-images.githubusercontent.com/77953290/229475515-56d5a3a2-8c19-4132-bd33-f8b4106bedfd.png)

![image](https://user-images.githubusercontent.com/77953290/229475562-6663e34a-1ef8-43d8-8a77-dd6df4c03511.png)

![image](https://user-images.githubusercontent.com/77953290/229475608-ccad0de7-096d-4efa-bb11-7bc79cb00159.png)

![image](https://user-images.githubusercontent.com/77953290/229475657-39ef4053-eb29-4a63-86a2-51ea5139fb39.png)

Analysis of Output:

On patients with sex = 0, i.e woman, risk of heart attack is half of those of men (1)
CP is the type of pain: probability of heart attack is almost none for 0 but 3x times higher on other cases
Fasting blood sugar, patients with fasting blood sugar higher than 120 are more susceptible to heart attacks
Rest ECG of value 1: Probability of having a HEART attack is 2x whereas is different in other cases
exang: Exercise induced angina: PAIN DUE TO EXERCISE, does not affect heart attack, as showed by graph with value 1
Slope: Patients with slope variable of 2 are 3 times more riskier of having a heart attack
CAA: Patients with a CAA value of 0 have a highers chance of having a heart attack than the other patients
thall: For thall: 2, we find that the value that draws our attention is the value 2, we can say that for other values that the incidence is reversed
Patients of having a risk of heart attack are more.



-----------------------------------------------------------------------------------------------------------------------------------------------------------------------


Feature Scaling: We are using Robust Scaler to scale our numeric features. Robust Scaler gives better results in data with outliers, because it removes the outliers and places them in the 1st and 3rd quartile of the data


Concatenating with the categorical variables and our scaled features:

Pivoting the table contents,  to then using swarm plots and box plots for variable analysis, i.e numerical variables with each categorical variables:


As we can see on the plot, 



