# Ex06 BMI Calculator


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
App.jsx
```
import React from 'react';
import { BrowserRouter, Routes, Route } from 'react-router-dom';
import Home from './Home.jsx';
import Calculator from './Calculator.jsx';

const App = () => (
  <BrowserRouter>
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/calculator" element={<Calculator />} />
    </Routes>
  </BrowserRouter>
);

export default App;

// Render the app
const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(<App />);
```

Home.jsx
```
import React from 'react';
import { Link } from 'react-router-dom';

const Home = () => (
  <div className="min-h-screen bg-gray-100 flex flex-col items-center justify-center p-4">
    <h1 className="text-4xl font-bold text-blue-600 mb-6">Welcome to BMI Calculator</h1>
    <p className="text-lg text-gray-700 mb-8">Calculate your Body Mass Index to understand your health status.</p>
    <Link to="/calculator" className="bg-blue-500 text-white px-6 py-3 rounded-lg hover:bg-blue-600">
      Go to Calculator
    </Link>
  </div>
);

export default Home;
```

BMICalculator.jsx
```
import React, { useState } from 'react';
import { Link } from 'react-router-dom';

const Calculator = () => {
  const [weight, setWeight] = useState('');
  const [height, setHeight] = useState('');
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState('');

  const calculateBMI = () => {
    if (weight && height) {
      const heightInMeters = height / 100;
      const bmiValue = (weight / (heightInMeters * heightInMeters)).toFixed(1);
      setBmi(bmiValue);
      if (bmiValue < 18.5) setCategory('Underweight');
      else if (bmiValue < 25) setCategory('Normal weight');
      else if (bmiValue < 30) setCategory('Overweight');
      else setCategory('Obesity');
    }
  };

  return (
    <div className="min-h-screen bg-gray-100 flex flex-col items-center justify-center p-4">
      <h1 className="text-3xl font-bold text-blue-600 mb-6">BMI Calculator</h1>
      <div className="bg-white p-6 rounded-lg shadow-md w-full max-w-md">
        <div className="mb-4">
          <label className="block text-gray-700 mb-2">Weight (kg)</label>
          <input
            type="number"
            value={weight}
            onChange={(e) => setWeight(e.target.value)}
            className="w-full p-2 border rounded-lg"
            placeholder="Enter weight"
          />
        </div>
        <div className="mb-4">
          <label className="block text-gray-700 mb-2">Height (cm)</label>
          <input
            type="number"
            value={height}
            onChange={(e) => setHeight(e.target.value)}
            className="w-full p-2 border rounded-lg"
            placeholder="Enter height"
          />
        </div>
        <button
          onClick={calculateBMI}
          className="w-full bg-blue-500 text-white p-2 rounded-lg hover:bg-blue-600"
        >
          Calculate BMI
        </button>
        {bmi && (
          <div className="mt-4 text-center">
            <p className="text-lg">Your BMI: <span className="font-bold">{bmi}</span></p>
            <p className="text-lg">Category: <span className="font-bold">{category}</span></p>
          </div>
        )}
      </div>
      <Link to="/" className="mt-6 text-blue-500 hover:underline">
        Back to Home
      </Link>
    </div>
  );
};

export default Calculator;
```

## OUTPUT
![image](https://github.com/user-attachments/assets/7c3807c6-0dac-4f57-88f8-3282bcd0b855)


## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
