
# Development

### Link to Deployed Website
`https://happydragon227.github.io/React_Dev/`

### Goal and Value of the Application
-> The goal of this application is for user to find the bakery they want to buy easily by using the sort and filter features.

### Usability Principles Considered
-> It is very effective, because it is very easy to use and easy to understand how to use it. \
-> It is very efficient, because user can get the bakeryitems they want by filtering and sorting. \
-> It is very consistent, because all the similar items are having the same format. 

### Organization of Components
-> The main file is the index.js file, and inside the index.js, we have our App.js file which contains all our app functions. \
-> The data I used in this app is stored in the bakery-data.jason file which I copied from the studio 5 and made some modification on it. \
-> Inside the app.js file, it calls 4 components which are CategoryButtons.js, CategoryButtons2.js, SortButtons.js, and BakeryItem.js. \
-> There are 6 state in app.js file: "count", "stuff", "list", "sorted", "filter1", "filter2". And 1 state "booll" in CategoryButtons2.js file.

### How Data is Passed Down Through Components
-> The "count" state stores the total value that you add to the shopping cart. \
-> The "Stuff" state stores the the item you added into the shopping cart. \
-> The "list" state stores all the filtered, sorted items. \
-> The "sorted" state stores the option you choose to sort the items, which are either "Prices" or "Ratings". \
-> The "filter1" state stores the current "bakery type" option you are selecting, which are either "All", "bread", "cake", or "cookie". \
-> The "filter2" state stores the list of Dietary Restrictions you had selected. \
-> The CategoryButtons is for filtering the type of the bakery. \
    -> The default setup for "filter1" state is "All", because originally, the application should display all the items. \
    -> Because a bakery cannot be a bread or cake or cookie at the same time, making it into a checkbox selection may confuse user, so I make it into radio button.\
    -> The data is passed down through app.js to CategoryButtons.js by the function "filterCategory1", it takes the current catogory you've clicked, and replace the "filter1" state. Then we reset the list based on the values in the "filter1" state and "filter2" state, which causes the rerendering. \
-> The CategoryButtons2 is for filtering the Dietary Restrictions. \
    -> The default setup for "filter2" state is "[]", because originally, no boxes are checked. \
    -> Each category has their own "booll" state which defaults to be "true", once it is clicked, it will be set to false. If clicked again, it will be set to true.\
    -> Because a bakery can have multiple Dietary Restrictions at the same time, I made it into a checkbox selection. \
    -> The data is passed down through app.js to CategoryButtons2.js by the function "filterCategory2", if you clicked a category once, it will be appened to the "filter2" state. If clicked twice, it will be removed from the "filter2" state. Finally, we reset the list based on the values in the "filter1" state and "filter2" state, which causes the rerendering. \
    
-> The SortButtons is for sorting items by prices or ratings. The default sorting method is price. \
    -> The default setup for "sorted" state is "Price", because originally, the default sort method is by price. \
    -> Because a bakery cannot be sorted in different methods at the same time, I made it into a radio selection. \
    -> The data is passed down through app.js to SortButtons.js by the function "handleSort", it takes the current catogory you've clicked, and replace the "sorted" state. Everytime the item is displayed, it will call the sort method to sort the items. \
    
-> The BakeryItem is a card which contains all the information about this item, and a add or remove button inside. \
    -> The default "list" state is set to the bakeryData, because originally, it should display all the item in the BakeryData. \
    -> The default "stuff" state is set to "[]", because originally, there are no items in the shopping cart. \
    -> The data is passed down through app.js to BakeryItem.js by the function "handleCount", it passes back the item value, whether to remove or add boolean, and its name. 
    
### How the User Triggers State Changes
-> They are all triggered by click. 
-> When you click a bakery type category, it will call the function "filterCategory1", which will change the "filter1" state to the one you clicked. \
-> When you click a Dietary Restrictions category once, it will set this specific category's "booll" state to false, it will then call the function "filterCategory2", which will add this category to the "filter2" state. If this button is clicked again, it will remove this category from the "filter2" state. \
-> When you click a sort category, it will call the function "setOrder", which will either be sorted by "price" or "ratings". \
-> Everytime we display the items onto the screen, we will call the sort method to sort it. On default, all the add or remove button for each items shows "Add", and when you click it, it will add the item to the shopping cart and add the value to the total price. But if this item appears in the "stuff" state, it will then be rendered as "remove", and when you click on remove, it remove the item from the shopping cart and subtract the value from the total price.
