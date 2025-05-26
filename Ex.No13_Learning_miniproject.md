# Ex.No: 13 Learning – Use Supervised Learning                                                            
### REGISTER NUMBER : 212222043001
### AIM: 
To write a program to train the classifier for -----------------.
###  Algorithm:
Step 1: Import packages Step 2: Get the data Step 3: Split the data Step 4: Scale the data Step 5: Instantiate model Step 6: Create a function for gradio Step 7: Print Result
### Program:
```
import numpy as np
import pandas as pd
pip install gradio
pip install typing-extensions --upgrade
pip install --upgrade typing
pip install typing-extensions --upgrade
import gradio as gr
data = pd.read_csv('/content/diabetes.csv')
data.head()
print(data.columns)
x = data.drop(['Outcome'], axis=1)
y = data['Outcome']
print(x[:5])
#split data
from sklearn.model_selection import train_test_split

x_train, x_test, y_train, y_test= train_test_split(x,y)

from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
x_train_scaled = scaler.fit_transform(x_train)
x_test_scaled = scaler.fit_transform(x_test)

from sklearn.neural_network import MLPClassifier
model = MLPClassifier(max_iter=1000, alpha=1)
model.fit(x_train, y_train)
print("Model Accuracy on training set:", model.score(x_train, y_train))
print("Model Accuracy on Test Set:", model.score(x_test, y_test))

def diabetes(Pregnancies, Glucose, Blood_Pressure, SkinThickness, Insulin, BMI,Diabetes_Pedigree, Age):
    x = np.array([Pregnancies,Glucose,Blood_Pressure,SkinThickness,Insulin,BMI,Diabetes_Pedigree,Age])
    prediction = model.predict(x.reshape(1, -1))
    if(prediction==0):
      return "NO"
    else:
      return "YES"

outputs = gr.Textbox()
app = gr.Interface(fn=diabetes, inputs=['number','number','number','number','number','number','number','number'], outputs=outputs,description="Detection of Diabeties")
app.launch(share=True)
```
### Output:
1.Dataset

![447404270-104a8fbc-279c-41aa-95c1-aa1549ea76ea](https://github.com/user-attachments/assets/c2b4bb33-c148-4ca8-8fd0-79b85ce557b8)

2.Accuracy

![447404353-7a1eae35-e978-478c-976c-b05a23d253b4](https://github.com/user-attachments/assets/b7db61a7-c06c-4bd8-81aa-e0517f2b867c)


3.Output

![447404469-960eb83d-05c6-4d67-9922-36803fcdccd9](https://github.com/user-attachments/assets/23ffa403-6e13-4ac1-9eaa-30565d74c523)


### Result:
Thus the system was trained successfully and the prediction was carried out.
