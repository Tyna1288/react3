- In action creators, like `getFilmFromAPI`, we use a "regular expression" ---
  what is that regular expression, and what is its purpose?
  
  ANSWER: A regular expression or regex is a sequence of characters that define a search pattern. Regex is commonly used to find patterns in text, in our case we are looking to match all digits in a string to find the id. In JavaScript, the match function accepts a regex (which starts and ends with a forward slash) and returns an array to us with the first value being the first match we find. This particular use of regex is to extract the number from the SWAPI API, which returns URLs, like https://swapi.dev/api/films/17/
  
- We're persisting the Redux store, so if you re-visit the app, it will remember
  the topics you've visited. Where is this stored? How is this done?
 
  ANSWER: We're storing this information in localStorage as changes to the Redux state occur. This is done using a module called redux-persist. Most of the logic for this is done in index.js. We make sure that the <App> component is not rendered, until the Redux state is hydrated (using a component called <PersistGate>)
    
- What does `combineReducers` do? Why are we using it? 
   
   ANSWER: The combineReducers function is a utility provided by Redux and simplifies the process of managing the state of multiple sub-components in an app.
However, with multiple sub-components that each need their own slice of the state, one can create a separate reducer for each sub-component, and using combineReducers, you can easily combine these individual reducers into a single, unified reducer that manages the entire state of the app.

- How does the "Reset to Fresh Exploration" feature work?

  ANSWER: The "Reset to Fresh Exploration" feature works by creating a new, fresh state object whenever the feature is triggered, which effectively resets the entire application state to its initial values.
This is implemented in Redux by defining a new state object in the reducer that manages the root state of the application, and when the "Reset to Fresh Exploration" action is dispatched, the reducer that manages the root state will return this new, fresh state object.
However, It dispatches an action with a type of RESET_ALL which is matched by every reducer and returns a copy of the initial state, clearing all Redux state in the application.

- Why are `FilmList.js`, `PlanetList.js`, and 
  `PersonList.js` all simple components that use an `ItemList`?
  Why is this a good design?
 
  ANSWER: These three components simply import the ItemList component which contains the presentation logic. The ItemList component is re-usable, but depends on data which FilmList, PlanetList and PersonList provide. This separation allows us to not attach our redux state with our react components all together, making the components more flexible and testable.
  
- In the `HomePage` component we use the `useSelector` hook to save only a single fact---
  whether the first film is loaded, We could instead have selected all the
  films, and had the check for whether the first film is loaded in our
  `render` function. Why is this worse? What would the performance implications
  be?
  
  ANSWER: Instead of making an API request or fetching larger pieces of Redux state, we only need to find one film at a time. Minimizing the amount of API calls or searches that we need to do will help us speed up the application.
  
- What good ideas for designing and organizing React apps have you learned from
  studying this code?
  
  ANSWER: The code is an excellent example of structuring and organizing a React app by incorporating modern React concepts and best practices.
**Break Down Components into Smaller Units:** By breaking down the HomePage component into smaller units, the code becomes more manageable and easier to understand. This approach can also make it easier to isolate and debug specific parts of the app.
Utilize Redux Selectors: The code demonstrates the effective use of Redux selectors. The app can minimize unnecessary re-renders and improve performance by selecting only the necessary data.
**Consider Component Reusability:** When designing components, it's essential to consider whether they can be reused in other parts of the app. By adhering to this principle, the code promotes better modularity and maintainability. 
Implement Performance-First Strategy: The code prioritizes performance optimization by using selectors and minimizing unnecessary re-renders. This approach can lead to a more responsive and efficient app.
**Embrace Best Practices:** The code adheres to various best practices in React development, such as using functional components, employing hooks like useSelector, and implementing efficient data-fetching strategies. These practices can contribute to a robust and maintainable app.

- Which Star Wars character would make the best React developer, and why?

 ANSWER: The Star Wars character would be Chewbacca because of the factors below, and it's important to note that other characters may have unique strengths and skills that could also contribute to their effectiveness in this role.
The factors are;
**Dependability:** As a loyal Wookiee, Chewbacca is a reliable and trustworthy partner. Similarly, a dependable React developer can be counted on to produce high-quality work on time.
**Passion for Details:** Wookiees are known for their fierce protectiveness and attention to detail. Similarly, a skilled React developer will obsess over ensuring that every aspect of their code is correct and optimized.
**Excellent Communication Skills:** While Wookiees are not known for their proficiency in spoken language, Chewbacca's growls and body language are a powerful form of communication. This makes him an ideal teammate, as he can effectively convey his ideas and thoughts.
**Resilience:** Chewbacca's rough and tough exterior hides a sensitive soul. He may be unable to read every emotion or motivation behind a teammate's decisions, but he can persevere through complex challenges.

