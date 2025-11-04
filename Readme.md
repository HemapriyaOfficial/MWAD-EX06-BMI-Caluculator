# Ex06 BMI Calculator
## Date:

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
App.js

```
import { BrowserRouter as Router, Routes, Route, Link } from "react-router-dom";
import Home from "./pages/Home";
import Calculator from "./pages/Calculator";

function App() {
  const navStyle = {
    backgroundColor: "#1a1a1a",
    padding: "15px",
    textAlign: "center"
  };
  const linkStyle = {
    color: "white",
    margin: "0 15px",
    textDecoration: "none",
    fontSize: "18px",
    fontWeight: "bold"
  };

  return (
    <Router>
      <nav style={navStyle}>
        <Link style={linkStyle} to="/">Home</Link>
        <Link style={linkStyle} to="/calculator">BMI Calculator</Link>
      </nav>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/calculator" element={<Calculator />} />
      </Routes>
    </Router>
  );
}

export default App;

```
Home.js

```
import { Link } from "react-router-dom";

function Home() {
  const container = {
    textAlign: "center",
    marginTop: "80px"
  };

  const button = {
    padding: "12px 24px",
    borderRadius: "10px",
    background: "#0A84FF",
    color: "#fff",
    fontSize: "18px",
    border: "none",
    marginTop: "20px",
    cursor: "pointer"
  };

  return (
    <div style={container}>
      <h1 style={{ fontSize: "40px", color: "#222" }}>BMI Calculator</h1>
      <p style={{ fontSize: "20px", color: "#555" }}>
        Quickly check your Body Mass Index
      </p>
      <Link to="/calculator">
        <button style={button}>Start Now</button>
      </Link>
    </div>
  );
}

export default Home;
```

Calculator.js
```
import { useState } from "react";

function Calculator() {
  const [weight, setWeight] = useState("");
  const [height, setHeight] = useState("");
  const [bmi, setBmi] = useState(null);
  const [category, setCategory] = useState("");

  const calculateBMI = () => {
    if (weight > 0 && height > 0) {
      const h = height / 100;
      const value = (weight / (h * h)).toFixed(2);
      setBmi(value);

      if (value < 18.5) setCategory("Underweight");
      else if (value < 24.9) setCategory("Normal Weight");
      else if (value < 29.9) setCategory("Overweight");
      else setCategory("Obesity");
    }
  };

  const card = {
    width: "380px",
    margin: "60px auto",
    padding: "30px",
    borderRadius: "14px",
    background: "#ffffffdd",
    boxShadow: "0 4px 12px rgba(0,0,0,0.2)",
    textAlign: "center"
  };

  const input = {
    width: "90%",
    padding: "12px",
    fontSize: "16px",
    borderRadius: "10px",
    border: "1px solid #aaa",
    marginTop: "12px"
  };

  const button = {
    marginTop: "20px",
    padding: "12px 20px",
    borderRadius: "10px",
    background: "#0A84FF",
    color: "#fff",
    fontSize: "18px",
    border: "none",
    cursor: "pointer"
  };

  return (
    <div style={card}>
      <h2 style={{ color: "#111" }}>BMI Calculator</h2>

      <input
        style={input}
        type="number"
        placeholder="Weight (kg)"
        value={weight}
        onChange={(e) => setWeight(e.target.value)}
      />

      <input
        style={input}
        type="number"
        placeholder="Height (cm)"
        value={height}
        onChange={(e) => setHeight(e.target.value)}
      />

      <button style={button} onClick={calculateBMI}>
        Calculate BMI
      </button>

      {bmi && (
        <div style={{ marginTop: "20px" }}>
          <h3>Your BMI: {bmi}</h3>
          <h4 style={{ fontWeight: "bold", color: "#117A65" }}>
            {category}
          </h4>
        </div>
      )}
    </div>
  );
}

export default Calculator;
```

## OUTPUT

<img width="1919" height="1079" alt="Screenshot 2025-11-04 103843" src="https://github.com/user-attachments/assets/76eeb9cd-aa77-47ee-8631-1b09d804c139" />

<img width="1919" height="1079" alt="Screenshot 2025-11-04 103909" src="https://github.com/user-attachments/assets/4eeba9bb-afdb-4b38-bb0a-5ab725c66592" />

<img width="1919" height="1079" alt="Screenshot 2025-11-04 103948" src="https://github.com/user-attachments/assets/c35f7c05-b280-4f8e-add0-f336ea9c7a42" />













## RESULT
The program for creating BMI Calculator using React Router is executed successfully.
