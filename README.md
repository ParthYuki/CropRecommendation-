# Crop Recommendation System

## Overview

The Crop Recommendation System is designed to predict the best crop to cultivate based on specific soil and environmental parameters. Using machine learning algorithms, this system analyzes data such as nutrient content, pH level, and other soil properties to recommend the most suitable crop.

## Features

- **Decision Tree**
- **Naive Bayes**
- **Support Vector Machine (SVM)**
- **Logistic Regression**
- **Random Forest**

## Dataset

The dataset contains the following features for each sample:

- N (Nitrogen) in ppm
- P (Phosphorus) in ppm
- K (Potassium) in ppm
- pH
- EC (Electrical Conductivity) in mS/cm
- S (Sulfur) in ppm
- Cu (Copper) in ppm
- Fe (Iron) in ppm
- Mn (Manganese) in ppm
- Zn (Zinc) in ppm
- B (Boron) in ppm

The target variable is the type of crop which includes:

- Grapes
- Mango
- Mulberry
- Pomegranate
- Potato
- Ragi

## Model Performance

The accuracy of the models is as follows:

| Model                | Accuracy |
|----------------------|----------|
| Decision Tree        | 0.94     |
| Naive Bayes          | 0.97     |
| SVM                  | 0.91     |
| Logistic Regression  | 0.96     |
| Random Forest        | 0.97     |

## Usage

### Predicting Crop

1. **Train the Model**: Train the model using the dataset and the chosen algorithms.
2. **Make Predictions**: Input the soil parameters into the trained model to get the crop recommendation.

### Sample Predictions

```python
# Sample data for prediction
data = np.array([[150,70,217,6,0.6,0.25,10,116,60,55,22]])

# Using Random Forest model for prediction
prediction = RF.predict(data)
print(prediction)  # Output: ['pomegranate']
```

## GUI Application

A GUI application is provided using `tkinter` to make it user-friendly for predictions.

### Running the GUI Application

1. **Install Dependencies**: Ensure you have `tkinter` and other dependencies installed.
2. **Run the Application**: Execute the provided script to launch the GUI.

```python
import tkinter as tk
from tkinter import ttk

# Function to predict crop
def predict_crop():
    # Get values from entry fields
    data = [float(entry.get()) for entry in entry_fields]

    # Make prediction
    prediction = RF.predict([data])

    # Update result label
    result_label.config(text=f'Predicted Crop: {prediction[0]}')

# Create main window
root = tk.Tk()
root.title("Crop Prediction")
root.geometry("500x400")

# Create entry fields for each feature
labels = ['N (Nitrogen)', 'P (Phosphorus)', 'K (Potassium)', 'pH', 'EC (Electrical Conductivity)', 'S (Sulfur)', 
          'Cu (Copper)', 'Fe (Iron)', 'Mn (Manganese)', 'Zn (Zinc)', 'B (Boron)']
entry_fields = []
units = ['ppm', 'ppm', 'ppm', '', 'mS/cm', 'ppm', 'ppm', 'ppm', 'ppm', 'ppm', 'ppm']
for idx, label in enumerate(labels):
    ttk.Label(root, text=f"Enter the value for {label} ({units[idx]}):").grid(row=idx, column=0, padx=10, pady=5, sticky="e")
    entry = ttk.Entry(root)
    entry.grid(row=idx, column=1, padx=10, pady=5, sticky="w")
    entry_fields.append(entry)

# Button to predict
predict_button = ttk.Button(root, text="Predict", command=predict_crop)
predict_button.grid(row=len(labels), column=0, columnspan=2, pady=10)

# Label to display prediction
result_label = ttk.Label(root, text="")
result_label.grid(row=len(labels)+1, column=0, columnspan=2)

root.mainloop()
```

## Conclusion

This Crop Recommendation System leverages machine learning to provide accurate and reliable crop suggestions based on soil properties. The integration of multiple algorithms ensures robustness and high performance, making it a valuable tool for farmers and agronomists.