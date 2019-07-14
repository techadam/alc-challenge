Get The Bill
Write all Javascript strictly with ES6. This means use arrow functions instead of the function keyword. Declare variables and functions with const or let. Use const by default, and only use let if you are sure you need to re-assign values to the said variable. Use the Selector API instead of the getElementBy... or getElementsBy... APIs. See https://developer.mozilla.org/en-US/docs/Web/API/Document_object_model/Locating_DOM_elements_using_selectors

Install the JSON Viewer Chrome extension (https://chrome.google.com/webstore/detail/jsonview/chklaanhfefbnpoihckbnefhakgolnmc?hl=en), open a new tab and go to this URL (https://randomapi.com/api/006b08a801d82d0c9824dcfdfdfa3b3c). You will be making HTTP requests to that API endpoint, so spend some time looking at the structure of the response data.

Step 1
Create an appState variable and assign it an empty Object literal. This variable will hold data for the app.

Create a formatAsMoney function. It should take in an amount and a buyerCountry parameter. It will use these parameters to format the user's bill as a proper currency.

Create detectCardType, validateCardExpiryDate, and validateCardHolderName functions. Each should take in a parameter and use object de-structuring to obtain the target property of the parameter.

Create a uiCanInteract function. It will be called to setup the UI like adding event handlers to enable interactions with the app.

Create a displayCartTotal function. It should expect a parameter and should use object de-structuring to obtain results property of the parameter. This function will be called with the data from an API call and it will display the total payment bill.

Step 2
Create a fetchBill function. It should assign https://randomapi.com/api/006b08a801d82d0c9824dcfdfdfa3b3c to an api variable. It should then use the browser's fetch function to make a HTTP request to api. Using an arrow function in a .then call to the fetch function, return the response after converting it to JSON. Using another .then call to the first one, pass the JSON data to displayCartTotal. Make sure to handle errors that may occur, e.g by showing a warning message in the console.

Call the fetchBill function from inside startApp.

Step 3
In displayCartTotal, de-structure the first item in the results array into a data variable. Next, use object de-structuring to obtain the itemsInCart and buyerCountry properties of data.

Set appState.items to itemsInCart and set appState.country to buyerCountry

Use the Array .reduce function to calculate the total bill from itemsInCart Note that each item has a qty property indicating how many of that item the user bought. Assign the calculated bill to appState.bill

Go back to the formatAsMoney function. Use the .toLocaleString function on its amount and buyerCountry to format amount as a currency with the currency symbol of buyerCountry. The countries and their currency symbols are in the countries array you got in your starter code. If the buyerCountry is not in countries, then use United States and the country and format the currency accordingly.

back to where you left off in displayCartTotal, use the formatAsMoney function to set appState.billFormated to the formatted total bill. The already assigned appState.bill and appState.country should come be handy now!

Set the text content of the data-bill SPAN to the formatted bill set in appState.billFormated

Finally, call uiCanInteract to wrap up displayCartTotal

Run the app (click the play button) and see if the correct formatted bill is displayed in the UI. Next, we will allow input and interaction so that users can provide payment information.