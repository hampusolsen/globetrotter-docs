
# Project Description

**Project name:** [Globetrotter](#)<br/>
**Project administrator:** [Hampus Olsen](https://github.com/hampusolsen)

<br/>

<!-- omit in toc -->
## Table of Content

+ [Abstract](#abstract)
+ [Purpose and Goal](#purpose-and-goal)
+ [Strategy and Scope](#strategy-and-scope)
  + [OAuth2 and local authentication strategies](#oauth2-and-local-authentication-strategies)
  + [Testing with Cypress and Jest](#testing-with-cypress-and-jest)
  + [Bringing interactivity into the mix](#bringing-interactivity-into-the-mix)
  + [Integrating Google Maps API](#integrating-google-maps-api)
+ [Limitations](#limitations)
+ [Technical Specification](#technical-specification)
  + [Front-end](#front-end)
  + [Back-end](#back-end)
  + [Testing](#testing)
+ [Addendum](#addendum)
  + [UI Design Standards](#ui-design-standards)
  + [Mockups and Wireframes](#mockups-and-wireframes)
  + [E/R-diagram](#er-diagram)
  + [Gantt Schedule](#gantt-schedule)

<br/>

## Abstract

Globetrotter aims to be a fully functional user-driven travel diary web application, enabling friends, family and strangers to connect through travel experiences. The Application will mainly be divided into two views: one full screen map view for easy travel representation and one blog view for further reading.

[_To the top_](#table-of-contents)

<br/>


## Purpose and Goal

With this project I will dive deeper into authenticating and authorizing users, broaden my knowledge regarding database management while continuing to sharpen my full stack development skills.

During the year that has lapsed I have learned a great deal and invested many hours into taking in not only course material, but really looked into and implemented anything hastily mentioned by both of our lecturers Viktor Silfverström and Andreas Argelius. So I really feel like I have gotten a good grasp on how the various parts of a web application works _**in isolation**_.

That is why I have chosen to not only immerse myself into one of the cogs and springs that drive the machine, but into deeply understanding it as a whole. Everything inbetween a user's first impression and the last row of the database index. I want to make it connect and watch the data flow throughout.

After project completion I will have experience in or understanding of:
* Production-ready user authentication and authorization
* Effective NoSQL database querying and entity relations
* Code comprehension and maintainability through comments, documentation and naming conventions
* Global state management for React
* Caching server responses and user sessions
* Integrating third-party APIs
* Custom error handling in ExpressJS

[_To the top_](#table-of-contents)

<br/>

## Strategy and Scope

### OAuth2 and local authentication strategies

### Testing with Cypress and Jest

### Bringing interactivity into the mix

### Integrating Google Maps API

[_To the top_](#table-of-contents)

<br/>

## Limitations

Due to the ambitious nature of the project, as well as taking into consideration the practical tone of our school, I have limited the project scope by not focusing too much on justifying design and technical implementations. Instead I have chosen to provide brief rationalization in regards to choices made, and let quality of the final product convey level of competence.

_**Accessibility**_ _(a11y)_ will also be widely overlooked to avoid unneccessary complexity, but will be kept in mind in regards to using semantic HTML elements and preparations will be made to ease future implementation.

Further, I will be limiting _**internationalization**_ _(i18n)_ to using **English** as the project *locale*; all documentation, code comments and theory will be written as such. _Dates_ and _timestamps_ will be in Coordinated Universal Time _(UTC)_.

[_To the top_](#table-of-contents)

<br/>

## Technical Specification

To make the lookup of technical specifications easier it has been broken up into categories: _front-end_, _back-end_ and _testing_.

<br/>

### Front-end

* [React](https://reactjs.org/): _A JavaScript library for building user interfaces_
* [React Query](https://react-query.tanstack.com/): _Performant and powerful data synchronization for React_
* [Axios](https://github.com/axios/axios): _Promise based HTTP client for the browser and node.js_
* [Framer Motion](https://www.framer.com/motion/): _A production-ready motion library for React_
* [styled-components](https://styled-components.com/): _Visual primitives for the component age_

### Back-end

* [Express](https://expressjs.com/): _Fast, unopinionated, minimalist web framework for Node.js_
* [express-validator](https://express-validator.github.io/): _A set of express.js middlewares that wraps validator.js validator and sanitizer functions_
* [express-session](https://github.com/expressjs/session): _Simple session middleware for Express_
* [Passport](http://www.passportjs.org/): _Simple, unobtrusive authentication for Node.js_
* [mongoose](https://mongoosejs.com/): _Elegant MongoDB object modeling for Node.js_

### Testing

* [eslint](https://github.com/wesbos/eslint-config-wesbos): _Code validation and formatting by Wes Bos' variation of Airbnb's ES6 standards_
* [Jest](https://jestjs.io/): _A delightful JavaScript Testing Framework with a focus on simplicity_
* [Cypress](https://www.cypress.io/): _Fast, easy and reliable testing for anything that runs in a browser_
  

[_To the top_](#table-of-contents)

<br/>

## Addendum

### UI Design Standards

Content

[_To the top_](#table-of-contents)

<br/>

### Mockups and Wireframes

Content

[_To the top_](#table-of-contents)

<br/>

### E/R-diagram

[![er diagram](https://i.ibb.co/82Gz0cG/er-diagram.png)](https://ibb.co/0Z1Bct1)

_Using Crow's foot notation._ 

[_To the top_](#table-of-contents)

<br/>

### Gantt Schedule

[![gantt schedule](https://i.ibb.co/f4DBC65/gantt-schedule.jpg)](https://ibb.co/QrDz6SR)

[_To the top_](#table-of-contents)