# Assignment 5: Frontend Design and Implementation

## Heuristic Evaluation

### Usability

**Discoverability**
- Support
    - All the main functionalities (groups, milestones, posting, map, commenting) are displayed at all times on the navigation sidebar. This visibility allows users to become aware of these functions upon first entering the app.
    - The pop error messages explicitly tell the user why they are not able to perform an action on the app. For example, when on the groups page, if a new user who hasn't commented or posted tries to create a group, they are given a popup that explains they need to achieve some milestones first before they can create a group.
- Violate
    - Along the lines of the error message, the text in the error message can be confusing to first time users because they don't know what the milestones mean. There is currently no mechanism to know how to achieve the milestones other than trial and error.
- Improvements & Tradeoffs
    - Add a short tutorial section that explains milestones and how certain user actions can be unlocked. However, a tradeoff is that this will add complexity to the web app UI interface (by adding another element to the navigation bar for the tutorial page), which could decrease the pleasantness of the app UI for my target user (immigrants) since it may look too overwhelming.
    - The large error message pop up, althought very noticeable, can reduces the pleasantness the user feels when using the app as it obstructs their view and can become obnoxious as it loudly points out a user making a mistake in their user action. I could make this error message pop up smaller to make it more pleasant at the expense of a lesser information scent as the message will not be as noticeable to hint the user did something wrong.
    - Add a tutorial/help page to the app 

**Efficiency**
- Support
    - The UI is very simple, with visible buttons that users can use to perform an action on the page. There are no hidden menu buttons. For example, to join a group, once users understand that they have to click the "My Groups" button on the navigation bar to get to the groups page and then click on the "Join" button, they would easily be able to join any group they wish in the future. The path to accomplish this action and others on my UI is short to minimize complexity.

### Linguistic

**Speak a User's Language**
- Support
    - With the error messages that pop up on the group creation page, the message provides information about why the user can't create a group yet due to missing milestones.
- Violate
    - Although the error message is helpful in telling the user that something is missing, it doesn't tell the user how to achieve the milestones. Only the developers who created the web app would know what user actions need to take place in order to achieve the milestones. 
- Improvements & Tradeoffs
    - Instead of stating the milesetone name, I could instead state explicitly what actions the user hasn't done that are required in order to create a group. For example, "Oops! In order to create a group, you must make one post and one comment in another group. It looks like you haven't posted nor commented yet. Please post and comment in a group to unlock the ability to create a group." This explicit message is long and could decrease the aesthetic pleasantness of the web app, as users are being provided a lot of text to read, but at the same time this message will improve the information scent and speak the user's language moreso.
    - I could also add this information to a tutorial/help page to inform the user why they can't perform some actions yet. This way isn't as aesthetically unpleasant and doesn't get in the way of the user's experience when they use the app.


**Consistency**
- Support
    - The same name of the concepts are used throughout the UI of the web app. The main components of the web app (ie the navigation sidebar) consistently show up on the left in each screen the user navigates to. The Figma UI interface format of the web app follows a similar format of Facebook, a social media app used in the immigrant community where you can create groups, post, comment, and save content that was the inspiration of my web app. The connection map is also similarly formatted (with the sidebar on the left and content on the right) to a web app called USAHello that connects immigrants with nearby resources and centers.

### Physical

**Fitt's Law**
- Support
    - Each element on the interface of the UI (ie that navigation side bar, groups page, and posting page) that corresponds to a concept is visible to the user and is adequately spaced from other elements to allow for clickability. This enables users to to navigate to these elements without having to go through hidden menus.
- Violate
    - I believe the elements on my Figma UI are all easily clickable.
- Improvements & Tradeoffs
    - When building out the frontend, I can adjust the spacing if needed based on how the elements look on the webpage.

**Gestalt Principles**
- Support
    - On all the pages, the layout convey a specific conceptual structure of "navigation on the left and concept on the right". Like Facebook, the user navigates to a page (concept) via the sidebar on the left. Once the user clicks on the page they would like to see, the page will appear on the right while the sidebar still appears on the left. 
- Violate
    - All pages follow the conceptual structure described above.
- Improvements & Tradeoffs
    - When building out the frontend, I could play around with how much of real estate on the screen the sidebar takes up since it is a persistant element on the screen. This could increase the aesthetic pleasantness of the page (more of page user cares about, less of navbar) but could violate Fitt's Law if the navbar is too small and the buttons are hard to click.
    - A navigation bar along the top of the screen could also do the same job and is more natural for a user using a webpage to use. This would accomplish the same job as a navigation bar on the side and could use less real estate on the page, thus increasing the aesthetic pleasantness described in the point above.

## Visual Design Study

[link](https://docs.google.com/presentation/d/1tC5Y7GoHhEXailGX4NpY5uSInoi_a1AfkVNSu8R4OsY/edit?usp=sharing)

### GitHub and Deployment Links:

**GitHub for Frontend:** [link](https://github.com/br197/a5-frontend)

**GitHub for Portfolio:** [link](https://github.com/br197/portfolio-broundtree)

**Link of Deployment:** [link](https://a5-frontend-virid.vercel.app/)