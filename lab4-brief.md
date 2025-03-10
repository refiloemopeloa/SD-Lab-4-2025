# REST Countries API Lab

## Objective
The objective of this lab is to assess your ability to fetch data from an API and update the DOM using JavaScript. You will create a web page that fetches data from the REST Countries API and displays information about a specific country entered by the user, along with information about its neighboring countries.

## Instructions

1. **Setup**
   - Create a new repository for this lab assignment named `<Your_Student_Number>-lab-4-sd`.
   - Inside the directory, create the following files:
     - `index.html`
     - `styles.css`
     - `script.js`

2. **HTML Structure**
   - In `index.html`, create a basic HTML structure with the following elements:
     - An input field for the user to enter the name of a country.
     - A button to submit the country name.
     - A `<section>` with the id `country-info` to display the country information.
     - A `<section>` with the id `bordering-countries` to display the list of bordering countries and their flags.

3. **Styling**
   - In `styles.css`, add some basic styling to make the page look presentable.

4. **JavaScript Functionality**
   - In `script.js`, write JavaScript code to achieve the following:
     - Fetch data from the REST Countries API (https://restcountries.com/) when the user submits the country name.
     - Parse the JSON response to extract the following relevant country information:
       - Capital
       - Population
       - Region
       - Flag
       - A list of the neighbouring countries (Full name) and their flags.
     - Update the DOM to display the retrieved country information.
     - Handle errors gracefully and display appropriate error messages to the user where neccesary.

5. **Example**
   - Given the country name "South Africa", the page should display:
     - Capital: Pretoria
     - Population: 59,308,690
     - Region: Africa
     - Flag: ![South Africa Flag](https://flagcdn.com/za.svg)
     - Bordering Countries:
       - Namibia: ![Namibia Flag](https://flagcdn.com/na.svg)
       - Botswana: ![Botswana Flag](https://flagcdn.com/bw.svg)
       - Zimbabwe: ![Zimbabwe Flag](https://flagcdn.com/zm.svg)
       - Mozambique: ![Mozambique Flag](https://flagcdn.com/mz.svg)
       - Eswatini: ![Eswatini Flag](https://flagcdn.com/sz.svg)
       - Lesotho: ![Lesotho Flag](https://flagcdn.com/ls.svg)

6. **Submission**
   - Demo your page before the end of the lab.
   - Zip your project directory and submit it as `<student-id>-lab4.zip`.
   - Push your changes to your new repo.

## Evaluation Criteria
- Correct implementation of the API fetch and data parsing.
- Proper handling of the JSON response to extract the relevant information.
- Correct updating of the DOM to display the retrieved information.
- Graceful handling of errors and display of appropriate error messages.
- Code readability and organization.

Good luck!
