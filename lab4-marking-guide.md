# REST Countries API Lab Marking Guide

## Objective
The objective of this lab is to assess students' ability to fetch data from an API and update the DOM using JavaScript. Students will create a web page that fetches data from the REST Countries API and displays information about a specific country entered by the user, along with information about its neighboring countries.

## Marking Rubric

| Criteria                          | Points | Description                                                                 |
|-----------------------------------|--------|-----------------------------------------------------------------------------|
| **HTML Structure**                | 20     | Correct use of semantic HTML elements and structure.                        |
| **Styling**                       | 10     | Basic styling applied to make the page presentable.                         |
| **API Fetch Implementation**      | 30     | Correct implementation of the API fetch and data parsing.                   |
| **DOM Update**                    | 20     | Proper updating of the DOM to display the retrieved information.            |
| **Error Handling**                | 10     | Graceful handling of errors and display of appropriate error messages.      |
| **Code Readability and Organization** | 10 | Code is well-organized and easy to read.                                    |
| **Total**                         | 100    |                                                                             |

## Detailed Marking Criteria

### HTML Structure (20 points)
- Correct use of semantic HTML elements (`<header>`, `<main>`, `<section>`, `<footer>`) instead of generic `<div>`s. (10 points)
- Proper structure and hierarchy of content (e.g., `<h1>` before `<h2>`, etc.). (10 points)

### Styling (10 points)
- Basic styling applied to make the page look presentable. (10 points)

### API Fetch Implementation (30 points)
- Correctly fetches data from the REST Countries API when the user submits the country name. (15 points)
- Parses the JSON response to extract the relevant country information (capital, population, region, flag, neighboring countries). (15 points)

### DOM Update (20 points)
- Properly updates the DOM to display the retrieved country information. (10 points)
- Properly updates the DOM to display the list of neighboring countries and their flags. (10 points)

### Error Handling (10 points)
- Gracefully handles errors and displays appropriate error messages to the user. (10 points)

### Code Readability and Organization (10 points)
- Code is well-organized and easy to read. (10 points)

## Example Submission

### HTML Structure
```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Country Info</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <header>
    <h1>Country Information</h1>
  </header>
  <main>
    <input type="text" id="country-input" placeholder="Enter country name">
    <button id="submit-btn">Submit</button>
    <section id="country-info"></section>
    <section id="bordering-countries"></section>
  </main>
  <script src="script.js"></script>
</body>
</html>
```

### JavaScript Functionality
```javascript
document.getElementById('submit-btn').addEventListener('click', async () => {
  const countryName = document.getElementById('country-input').value;
  try {
    const response = await fetch(`https://restcountries.com/v3.1/name/${countryName}`);
    if (!response.ok) throw new Error('Country not found');
    const [country] = await response.json();
    const { capital, population, region, flags, borders } = country;

    document.getElementById('country-info').innerHTML = `
      <h2>${countryName}</h2>
      <p>Capital: ${capital}</p>
      <p>Population: ${population}</p>
      <p>Region: ${region}</p>
      <img src="${flags.svg}" alt="Flag of ${countryName}">
    `;

    const borderingCountries = await Promise.all(borders.map(async (border) => {
      const borderResponse = await fetch(`https://restcountries.com/v3.1/alpha/${border}`);
      const [borderCountry] = await borderResponse.json();
      return `<li>${borderCountry.name.common}: <img src="${borderCountry.flags.svg}" alt="Flag of ${borderCountry.name.common}"></li>`;
    }));

    document.getElementById('bordering-countries').innerHTML = `
      <h3>Bordering Countries</h3>
      <ul>${borderingCountries.join('')}</ul>
    `;
  } catch (error) {
    document.getElementById('country-info').innerHTML = `<p class="error-message">${error.message}</p>`;
  }
});
```

### CSS Styling
```css
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f0f0f0;
}

header {
  background-color: #4CAF50;
  color: white;
  text-align: center;
  padding: 1em 0;
}

main {
  padding: 1em;
}

input, button {
  display: block;
  margin: 1em 0;
}

#error-message {
  color: red;
}
```

## Notes
- Ensure that the file names and required texts such as commit messages and text on HTML pages appear EXACTLY as briefed.
- Incorrect file names and text will be considered a fail and will not be remarked.

Good luck!
