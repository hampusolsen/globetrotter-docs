<!-- omit in toc -->
Globetrotter Project Description
================================

**Project name:** Globetrotter<br>
**Project administrator:** [Hampus Olsen](https://github.com/hampusolsen)

<br>
<br>
<br>
<br>
<br>
<br>

<p align="center">
  <img src="./design/svgs/Logo.svg" width="30%">
</p>

<br>
<br>

<!-- omit in toc -->
Abstract
--------

<br>

Globetrotter aims to be a fully functional user-driven travel diary. A web application enabling friends and family to share travel experiences. The application will mainly be divided into two views: one full screen map view for easy travel representation and one blog view for further reading.

<br>
<br>

<!-- omit in toc -->
Table of Contents
-----------------

+ [Purpose and Goal](#purpose-and-goal)
+ [Scope](#scope)
  + [Limitations](#limitations)
    + [Responsive Design](#responsive-design)
    + [I18n, A11y and L10n](#i18n-a11y-and-l10n)
    + [Testing](#testing)
  + [Methodology](#methodology)
+ [Strategy and Implementation](#strategy-and-implementation)
  + [The Design Pattern](#the-design-pattern)
  + [Responsive User Interface](#responsive-user-interface)
  + [Version Control with Git](#version-control-with-git)
  + [Setting up the Workspace](#setting-up-the-workspace)
    + [Environment Variables and Configuration](#environment-variables-and-configuration)
    + [Containerization](#containerization)
  + [Technical Documentation](#technical-documentation)
  + [Database Management](#database-management)
    + [Caching Data](#caching-data)
    + [Distributed and Document-based](#distributed-and-document-based)
  + [Authentication and Authorization](#authentication-and-authorization)
    + [Honorable Mentions](#honorable-mentions)
    + [Stateful and Stateless Web Services](#stateful-and-stateless-web-services)
  + [Global State Management](#global-state-management)
+ [Discussion](#discussion)
+ [Technical Specification](#technical-specification)
  + [Frontend](#frontend)
  + [Backend](#backend)
  + [Testing and Style Enforcement](#testing-and-style-enforcement)
  + [Documentation, Diagrams and Graphics](#documentation-diagrams-and-graphics)
+ [API & Database Specifications](#api--database-specifications)
  + [E/R-diagram](#er-diagram)
  + [Documentation](#documentation)
+ [Addendum](#addendum)
  + [Gantt Schedule](#gantt-schedule)
  + [Mockups and Styleguide](#mockups-and-styleguide)

<br>
<br>

Purpose and Goal
----------------
<br>

During the year that has lapsed I have learned a great deal. Many hours were invested into not only course material, but also looking into and implementing anything hastily mentioned by both of our wonderful lecturers Viktor Silfverström and Andreas Argelius. So I really feel like I have gotten a good grasp on how the various parts of a web application works *in isolation*.

That is why I, in this project, have chosen to not only immerse myself in a cog or spring that drive a machine, but instead attempt to deeply understand it as a whole. Everything from a user's first impression to the very last row of a database. I want to make it run and know that I truely am in control of everything. Fully aware of what is lacking, and sure that these are conscious decisions made due to the limitations in place.

<br>

*[To the top](#table-of-contents)*

<br>
<br>

Scope
-----
<br>

### Limitations
Due to the ambitious nature of the project as well as taking into consideration the practical tone of our school, the project scope is limited by focusing mainly on writing the web application. Obviously the report will mirror this decision. Alas, its functionality will be to describe the project, in detail, more so than act as a typical scientific report.

<br>

#### Responsive Design
The goal was always to make Globetrotter's UI responsive and largely customized for the most common breakpoints in a *small/medium/large* fashion, albeit taking a mobile-first approach and placing the rest in the backlog on a low priority.

<br>

#### I18n, A11y and L10n
*Accessibility* is widely overlooked to avoid unneccessary complexity, but has been kept in mind in regards to using semantic HTML elements and preparations were made to ease future implementation. Further, *internationalization* has been limited by only using English as the project language and *localization* set to American English; all documentation, code comments and theory is written as such, though dates are localized.

<br>

#### Testing
A subject in itself, tests do not to cover any desirable amount of the code base, and those written are simpler integration and unit tests for the frontend client. Initial wishful thinking consisted of a much more test-driven development, but was later discarded due to lack of practical experience. Specifically with regards to end-to-end tests.

<br>

*[To the top](#table-of-contents)*

<br>
<br>

### Methodology
Doing a fullstack project like this, planning it all out sometimes felt overwhelming or stressful and it was close to impossible knowing if everything got covered. Realistically, the planning phase of a project can often be more long-lived than implemention and testing combined. Not something that I could afford, all things considered.

While contemplating my work process I started with tasks that I knew would be of aid during development and demanding no prerequisite work. Such as defining a design styleguide, creating mockups and wireframes as well as E/R and auth flow-schematics. With these things in place it was much easier to produce code. Notes were continuously kept as the codebase grew in size and complexity, and could later be used as fallbacks when writing the project description.

<br>

*[To the top](#table-of-contents)*

<br>
<br>

Strategy and Implementation
---------------------------
<br>

### The Design Pattern
The [*Model-View-Controller* pattern](https://www.codecademy.com/articles/mvc) is currently dominating fullstack web applications' architecture and it is becoming increasingly hard to find frameworks not building upon this concept. With its fairly simplistic approach that invites to a logical organization of a projects file structure, it is no wonder that the pattern is widely used. Understanding how the different parts work together is, as hinted at, relatively easy, and so in turn also eases development as functionality is clearly defined. For this project the backend provides both model and controller functionality by Mongoose models and route handlers respectively whilet the frontend, powered by React, works as the view layer.

<br>

*[To the top](#table-of-contents)*

<br>
<br>

### Responsive User Interface
As previously mentioned in the project scope, the application was made with the intention of being responsive with three breakpoints. A very common approach that satisfies all types of devices. While mobile devices' screens are evolving with every generation, growing larger and larger, and pixel density also improves, so does the optimal breakpoints also shift. Of course, every consumer does not upgrade their phone on each generational swap, but to make sure the latest and greatest is supported it might be a good idea to update ones breakpoints. An effortless task if these are saved as constants, either with environment variables or in a simple `.js`-file. Globetrotter applies this by setting the breakpoints at pixel values of 414, 800 and 1080 using a `min-width` media query, representing [current market availability of phone, tablet and laptop screens' resolution](https://gs.statcounter.com/screen-resolution-stats/), adhereing to mobile-first design philosophy.

<br>

Mobile-first is a relatively new yet universally adopted concept, born out of the fact that [more than half of daily internet users are using a mobile device](https://www.gsma.com/mobilefordevelopment/wp-content/uploads/2019/07/Mobile-Internet-Connectivity-Global-Factsheet.pdf) to browse the web. Developing in a mobile-first way means prioritizing development and optimization for smaller screens, and adapting to larger ones later. Taking pointers from [Facebook's statistics](https://www.statista.com/statistics/377808/distribution-of-facebook-users-by-device/), which show that 98.3% of their visitors used mobile devices to access the site, coupled with the fact that Globetrotter is a type of social media platform, a mobile-first approach almost seems non-negotiable. An astonishing 79.9% exclusively used their smartphone on the web application.

<br>

*[To the top](#table-of-contents)*

<br>
<br>

### Version Control with Git
+ github
+ awkward when solo programming / great history tracker / reminder
+ commits after session or task completed

[comment]: # (https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow)
workflow

[comment]: # (https://medium.com/@fredrikmorken/why-you-should-stop-using-git-rebase-5552bee4fed1)
non-linear vs linear history

[comment]: # (https://www.conventionalcommits.org/en/v1.0.0/#summary)
commit naming convention

<br>

*[To the top](#table-of-contents)*

<br>
<br>

### Setting up the Workspace
Content

<br>

#### Environment Variables and Configuration
+ natural selection of environment variables

<br>

#### Containerization
Content

[comment]: # (https://www.ibm.com/cloud/blog/containers-vs-vms)
containers vs virtual environments

<br>

*[To the top](#table-of-contents)*

<br>
<br>

### Technical Documentation
In an effort to make the task of writing documentation not so overwhelming, I believed it to be a good idea to spread it throughout the projects duration. Documenting functions and data structures close before or after their creation helps with keeping the documentation correct as well as easy and fast to write. Usually technical documentation tends to be automatically generated by tools such as [Swagger](https://swagger.io/), but as I possessed no prior knowledge of their utilization and already felt as if there were enough things to consider, adding another tool and also learning how to use it  was out of the question.

After having read so much documentation on Github and elsewhere I knew I could not possibly write my own in any other syntax than *[Markdown](https://en.wikipedia.org/wiki/Markdown)*, even though *[reStructuredText](https://en.wikipedia.org/wiki/ReStructuredText)* is a solid contender and widely used; picking anything else would feel like committing a crime. 

To accomodate the widest array of platforms and pursuit the highest percentage of compatibility I found the [commonmark specification](https://spec.commonmark.org/0.29/) to align closest with my writing style while achieving these goals. So I have followed their syntax guidelines while writing this report, only deviating when it comes commenting, where I found this [interesting stackoverflow post](https://stackoverflow.com/questions/4823468/comments-in-markdown/32190021#32190021), proving `[comment]: # (<comment here>)` with an empty line above, to provide best platform coverage.

<br>

*[To the top](#table-of-contents)*

<br>
<br>

### Database Management
Content

<br>

#### Caching Data
Content

<br>

#### Distributed and Document-based
Content

<br>

*[To the top](#table-of-contents)*

<br>
<br>

### Authentication and Authorization
A collectively deemed complex and persistant subject of debate is the topic of how to handle authentication of users. Without a method of identification there would be no way to personalize the user experience, and without verification of identity, neither would there be a way to secure it.

Before even beginning to write about authentication and authorization, we must first clearly define both terms. More often than not they are swapped around or used semantically indistinguishable from oneanother although there is a clear cut difference:

+ **Authentication** equals *verifying identity*, such as when a user provides a combination of an e-mail address and a password.

+ **Authorizing** means *granting access* to a restricted resource or method, like granting access to a sectioned off part of a website or allowing someone to read and write to a database.

<br>

> “Encryption works ... Unfortunately, endpoint security is so terrifically weak ...”

*[Edward Snowden](https://twitter.com/snowden)*

<br>

Handling user data in a safe and responsible manner has been proven to be very difficult and is a task with many ways to fail. Having spent days upon days searching for a surefire way as to how authentication should be implemented, I was forced to forfeit in favor of preserving time. There is no holy grail of authentication and the methods available are continuously changing.

Though myself and Mr. Snowden just might have implied that no one seems to know how authentication works because it is impossible to get right, this is far from the truth. There exists a few well established strategies which can be interwoven, extended and used in parallela and I will write more in-depth about the particular ones I have adhered to. 

<br>

#### Honorable Mentions
For this project I will not be using the following methods, but felt as they were worth mentioning:

+ [Role-Based Access Control (RBAC)](https://auth0.com/docs/authorization/rbac): The choice was made to treat all authenticated users the same in terms of their privileges. *Guest role* indirectly exists, since unregistered users must have a way to sign up or log in.

+ [Attribute-Based Access Control (ABAC)](https://www.zehntec.com/blog/permission-based-authorization-in-asp-net-core/): Expanding on role-based authorization by breaking down permission rights into smaller pieces, ABAC is common in many large-scale applications and content management systems (CMS). Roles can be created and tailored, granting different access rights to different users. Because users in my case need the same set of mostly self-modifying permissions, this way of granting user privileges was quickly rejected.

+ [Multi-Factor Authentication (MFA)](https://brocku.ca/information-technology/service-catalogue/security-and-access/multi-factor-authentication/): A great way to add another layer of security and can be implemented with relative ease on top of any existing method. MFA has become a must for any application that needs as high a level of security it can get. A great example is the combination of BankID and a swedish personal number.
  
+ [JSON Web Token-Based Authentication (JWT)](https://auth0.com/learn/token-based-authentication-made-easy/): This was initially planned and scheduled for as it is easier to implement, but comes with a few potential drawbacks with respect to *security*, *data farming* and *user experience* as it is completely stateless, meaning that JWTs does not store any data and are solely used for authorization. Data farming is an interesting aspect and something I would like to research more down the line. As such I have made preparations for, though not implemented it, in this project.

<br>

#### Stateful and Stateless Web Services
Also known as stateful authentication or just sessions for short, the method, as briefly mentioned above, presents more options to closely observe how clients actually use an application as well as many possibilities of tailoring the experience to each individual user. Let me illustrate with a quick example of something that would ***not*** be possible using a simple JWT strategy:

*You are on a e-commerce site and have put several items in your shopping cart. Items which you have spent a considerable amount of time carefully picking out among hundreds of other items. Suddenly your computer runs out of battery and shuts down, terminating all running processes, including your browser. Or perhaps your internet connection is lost. With sessions implemented you can rest assured that the shopping cart data was stored in the session storage on the server, while if the application only had been using stateless JWT tokens you would have had to find and add the items again.*

Not at a fault of the site owner, but this might just make them lose that one customer.

What enables a stateful web service to provide a solution to such a scenario is a storage module dedicated for session-related data that does not need to outlive the session. Basically, when the session lifetime ends, a user logs out or it is invalidated by the server, any stored data pertaining to it will be forgotten. This data, or part of it, can of course be stored permanently in another database before being discarded if so chosen.

[There are many pros and cons](https://github.com/OpenIdentityPlatform/OpenAM/wiki/Stateful-vs-Stateless-Authentication) to weigh against eachother when deciding on a correct strategy for ones own application.

In terms of security, stateful web services comes out on top when compared to a stateless application. The main reason being: security is inhereted by the very nature of statefulness. For authorization strategies using stateful JSON Web Tokens, all session data is stored inside the token itself. Meaning that anyone who is in possession of said token would be able to decode it and read potentially sensitive information. In contrast, merely an identifier of the session is being sent back and forth between client and the authentication server for a stateful web service. Not only is session-related data openly embedded in the token used for a stateless strategy, authorization is also impossible to revoke should a token be compromized. In such a case, an attack is possible until the end of the token lifetime. Hence, why they are usually short lived. Meanwhile, in a stateful application, access can simply be withdrawn by removing corresponding session value from the cache database. One could even go as far as to construct elaborate mechanisms to try and track an abuser. As I felt comfortable implementing it, the stateful variant won in terms of security due to its many natural advantages.

Concentrating further on the difference between what is being sent in cookies, stateless JWT versus simple session identifier, there is a lot to be said about how this has a direct impact on resource demand. As more data is needed for a session, stateless JWT gets heavier. A heavier JWT means a heavier network load. This is not an issue as long as the session state is kept simple, but becomes a problem as features are added and it grows in complexity, as many inbound requests could result in a network bottleneck. On the other hand, stateful session requires as mentioned a place to store session data server-side. Databases management and communication of course adds not only to code complexity, but could just as well become an issue in regards to memory. A lot of testing and cost analysis is required to decide which process is more advantageous and if there are any breakpoints. In my case it was purely decided on what would grant the most personal development, as I had not previously built a stateful application.

<br>

*[To the top](#table-of-contents)*

<br>
<br>

### Global State Management
Content

* "overrated" / "hyped", often unneccessary with a truely global state
* per view / several view contexts
* complexity.. jotai/recoil -> context -> redux/rxjs/mobx

<br>

*[To the top](#table-of-contents)*

<br>
<br>

Discussion
----------
<br>

Blehe

<br>

*[To the top](#table-of-contents)*

<br>
<br>

Technical Specification
-----------------------
<br>

### Frontend
+ [React](https://reactjs.org/): *A JavaScript library for building user interfaces*
+ [Axios](https://github.com/axios/axios): *Promise based HTTP client for the browser and node.js*
+ [styled-components](https://styled-components.com/): *Visual primitives for the component age*
+ [Formik](https://formik.org/): *The World's most popular open source form library for React and React Native*
+ [Yup](https://github.com/jquense/yup): *Dead simple Object schema validation*

<br>

### Backend
+ [Express](https://expressjs.com/): *Fast, unopinionated, minimalist web framework for Node.js*
+ [express-validator](https://express-validator.github.io/): *A set of express.js middlewares that wraps validator.js validator and sanitizer functions*
+ [express-session](https://github.com/expressjs/session): *Simple session middleware for Express*
+ [Passport](http://www.passportjs.org/): *Simple, unobtrusive authentication for Node.js*
+ [mongoose](https://mongoosejs.com/): *Elegant MongoDB object modeling for Node.js*
+ [ioredis](https://github.com/luin/ioredis): *A robust, performance-focused and full-featured Redis client for Node.js*

<br>

### Testing and Style Enforcement
+ [eslint](https://github.com/wesbos/eslint-config-wesbos): *Code validation and formatting according to Airbnb's ES6 standards*
+ [prettier](https://prettier.io/): *An opinionated code formatter*
+ [jest](https://jestjs.io/): *Jest is a delightful JavaScript Testing Framework with a focus on simplicity.*

<br>

### Documentation, Diagrams and Graphics
+ [draw.io](http://draw.io): *Easily create and share professional diagrams*
+ [Illustrator](https://adobe.com/products/photoshop.html): *The state of the art of illustration*
+ [iconmonstr](http://iconmonstr.com): *A wide variety of free SVG icons.*
+ [Adobe Color](https://color.adobe.com/): *Color palette, the color scheme for artists*

<br>

*[To the top](#table-of-contents)*

<br>
<br>

API & Database Specifications
-----------------------------
<br>

### E/R-diagram
<br>
<br>

<p align="center">
  <a href="https://ibb.co/0Z1Bct1">
    <img src="https://i.ibb.co/82Gz0cG/er-diagram.png">
  </a>
  <br>
  <br>
  <em>Using Crow's foot notation.</em>
</p>

<br>

*[To the top](#table-of-contents)*

<br>
<br>

<hr>

### Documentation
<br>

Click [here](https://github.com/hampusolsen/globetrotter-server/blob/master/docs/api-specification.md) to go to the Globetrotter backend API documentation.

<br>

*[To the top](#table-of-contents)*

<br>
<br>

<hr>

Addendum
--------
<br>

### Gantt Schedule
<br>

<p align="center">
  <a href="https://ibb.co/QrDz6SR">
    <img src="https://i.ibb.co/f4DBC65/gantt-schedule.jpg">
  </a>
</p>

*[To the top](#table-of-contents)*

<br>
<br>

### Mockups and Styleguide
<br>

<p align="center">
  <img src="./design/mockups/Phone.png" width="30%">
  <br>
  <em style="font-size:12px">Mobile landing page</em>
</p>

<br>
<br>

<p align="center">
  <img src="./design/mockups/Desktop.png" width="70%">
  <br>
  <em style="font-size:12px">Desktop breakpoint landing page</em>
</p>

<br>
<br>

<p align="center">
  <img src="./design/mockups/styleguide.svg" width="70%">
  <br>
  <em style="font-size:12px">Design styleguide</em>
</p>

<br>
<br>

*[To the top](#table-of-contents)*