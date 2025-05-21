# Ex06 BMI Calculator
## Date:20.05.25

## AIM
To create a BMI calculator using React Router 

## ALGORITHM
### STEP 1 State Initialization
Manage the current page (Home or Calculator) using React Router.

### STEP 2 User Input
Accept weight and height inputs from the user.

### STEP 3 BMI Calculation
Calculate the BMI based on user input.

### STEP 4 Categorization
Classify the BMI result into categories (Underweight, Normal weight, Overweight, Obesity).

### STEP 5 Navigation
Navigate between pages using React Router.

## PROGRAM
## App.jsx
```
import React, { useState } from 'react';

function BMICalculator() {
  const [height, setHeight] = useState('');
  const [weight, setWeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState('');

  const calculateBMI = () => {
    if (height > 0 && weight > 0) {
      const heightInMeters = height / 100;
      const bmiValue = weight / (heightInMeters * heightInMeters);
      setBmi(bmiValue.toFixed(2));

      // BMI categories based on WHO
      if (bmiValue < 18.5) setCategory('Underweight');
      else if (bmiValue < 24.9) setCategory('Normal weight');
      else if (bmiValue < 29.9) setCategory('Overweight');
      else setCategory('Obese');
    } else {
      setBmi(null);
      setCategory('');
    }
  };

  return (
    <div style={{ padding: '20px', maxWidth: '400px', margin: 'auto', textAlign: 'center' }}>
      <h2>BMI Calculator</h2>
      <div>
        <input
          type="number"
          placeholder="Height (cm)"
          value={height}
          onChange={(e) => setHeight(e.target.value)}
        />
      </div>
      <div style={{ marginTop: '10px' }}>
        <input
          type="number"
          placeholder="Weight (kg)"
          value={weight}
          onChange={(e) => setWeight(e.target.value)}
        />
      </div>
      <button style={{ marginTop: '15px' }} onClick={calculateBMI}>
        Calculate BMI
      </button>

      {bmi && (
        <div style={{ marginTop: '20px' }}>
          <p><strong>Your BMI:</strong> {bmi}</p>
          <p><strong>Category:</strong> {category}</p>
        </div>
      )}
    </div>
  );
}

export default BMICalculator;
```
## main.jsx
```
import React from 'react';
import { createRoot } from 'react-dom/client';
import App from './App';
import './index.css'; // Optional: include if you have global styles

const container = document.getElementById('root');
const root = createRoot(container);

root.render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

## OUTPUT
![image](https://github.com/user-attachments/assets/3bf2eb28-566b-492b-bdab-1c8fb9a37be3)

## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
