# 🌍 Country Data Package

A comprehensive npm package that provides all countries' information like names, flags, states, currencies, and languages in a simple and ready-to-use way.

To install the package, run:  
`npm install @omprakashkumar/country-data-package`

It provides 5 methods:  
`getCountries()` returns all countries.  
`getStatesByCountry('IN')` returns all states of a country by code.  
`getCurrencyByCountry('IN')` returns currency.  
`getLanguagesByCountry('IN')` returns official languages.  
`getFlagByCountry('IN')` returns the flag URL.

Here’s a simple working React example:

```jsx
import './App.css';
import React, { useState } from 'react';
import {
  getCountries,
  getStatesByCountry,
  getCurrencyByCountry,
  getLanguagesByCountry,
  getFlagByCountry,
} from '@omprakashkumar/country-data-package';

function App() {
  const [selectedCountry, setSelectedCountry] = useState('');
  const [states, setStates] = useState([]);
  const [flag, setFlag] = useState('');
  const [currency, setCurrency] = useState('');
  const [languages, setLanguages] = useState([]);

  const handleCountryChange = (e) => {
    const code = e.target.value;
    setSelectedCountry(code);
    setStates(getStatesByCountry(code));
    setFlag(getFlagByCountry(code));
    setCurrency(getCurrencyByCountry(code));
    setLanguages(getLanguagesByCountry(code));
  };

  return (
    <div className="App">
      <h1>🌎 Country Selector</h1>
      <select onChange={handleCountryChange}>
        <option value="">-- Select Country --</option>
        {getCountries().map((c) => (
          <option key={c.code} value={c.code}>{c.name}</option>
        ))}
      </select>

      {states.length > 0 && (
        <select>
          <option>-- Select State --</option>
          {states.map((s) => (
            <option key={s.code} value={s.code}>{s.name}</option>
          ))}
        </select>
      )}

      {flag && <div><h3>Flag</h3><img src={flag} width="100" /></div>}
      {currency && <p><b>Currency:</b> {currency}</p>}
      {languages.length > 0 && (
        <div>
          <b>Languages:</b>
          <ul>{languages.map((l, i) => <li key={i}>{l}</li>)}</ul>
        </div>
      )}
    </div>
  );
}

export default App;

### CSS Section  ### 

.App {
  max-width: 500px;
  margin: auto;
  padding: 20px;
  font-family: sans-serif;
  background: #f5f5f5;
  border-radius: 8px;
}
select, img, p, ul {
  margin-top: 15px;
  width: 100%;
}
img {
  border: 1px solid #ccc;
  border-radius: 4px;
}
ul {
  padding: 0;
  list-style: none;
}
ul li {
  background: #eee;
  margin-bottom: 5px;
  padding: 6px;
  border-radius: 4px;
}


### Output 
![alt text](image-1.png)

