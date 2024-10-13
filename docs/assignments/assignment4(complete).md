# Assignment 4: Backend Design & Implementation (revised)

## Data Modeling

### Posting[Item, User]

**States:**
- setOfPosts: set of Item
- postAuthor: setOfPosts -> one User
- postContent: setOfPosts -> one String
- postDateCreated: setOfPosts -> one Date

<img src="/assets/images/postingmodel.jpeg" width="400px" height="400px">

### Commenting[Item, User, Comment]

**States:**
- setOfComments: Item -> set Comment
- commentAuthor: Comment -> one User
- commentContent: Comment -> one String
- commentTimeCreated: Comment -> one Date

<img src="/assets/images/newcommentingmodel.jpeg" width="400px" height="400px">

### Mapping[User, Maps]

**States:**
- setofMaps: set Maps
- user: setOfMaps -> one User
- city: setOfMaps -> String
- state: setOfMaps -> String

<img src="/assets/images/revisedmapping.jpeg" width="400px" height="400px">

### Grouping[Collection, User, Items]

**States:**
- setOfGroups: set Collection
- groupMembers: setOfGroups -> set Items
- groupName: setOfGroups -> one String
- groupOwner: setOfGroups -> one User
- groupDescription: setOfGroups -> one String

<img src="/assets/images/groupingmodel.jpeg" width="400px" height="400px">

### Milestone-ing[Milestone, User]

**States:**
- setOfMilestones -> set Milestone
- userMilestone: Milestone -> set Users

<img src="/assets/images/milestoningmodel.jpeg" width="400px" height="400px">

### Sessioning[User]

**States:**
- session: set Sessions
- activeUser: session -> one User

<img src="/assets/images/sessioningmodel.jpeg" width="400px" height="400px">

### Authenticating

**States:**
- registered: set User
- username: registered -> one String
- password: registered -> one String

<img src="/assets/images/newauthmodel.jpeg" width="400px" height="400px">

## App

***include Milestone***

***include Authenticating***

***include Collection***

***include Maps***

***include Sessioning[Authenticating.User]***

***include Posting[String, Sessioning.User]***

***include Commenting[Posting.setOfPosts, Sessioning.User, String]***

***include Mapping[Sessoning.User, Maps]***

***include Grouping[Collection, Sessioning.User, Authenticating.Registered, Posting.setOfPosts, Comments.setOfComments]***

***include Milestone-ing[Milestone, Sessioning.User]***

## Global Data Model
<img src="/assets/images/refinedglobalmodel.jpeg" width="400px" height="400px">

## Code:

**Deployed Service:** --

**GitHub Repository:** [link](https://github.com/br197/a4-backend)

## Design Reflection

While working on the backend, I had to make several changes to my concept as I found some actions missing and rethought how I wanted concepts (such as mapping) to function. To keep this reflection succinct, I will highlight some of the most prominent design changes I made. The first change I made was to the Grouping Concept. I wanted to identify the groups created as either a resource group (store information) or user group (store members), but my current states for groups didn't support this. So, I added a state called resource that was true if the group is a resource group and false otherwise. I thought of creating another concept, but wanted to reuse as much of the code I had to implement user groups as possible. In adding a state rather than a concept, I was able to reuse my Group concept functions and synchronizations with minimal modification.


Another big change I made was to the Mapping Concept. I realized that the only resources (information sources) I had in my app were posts and comments, which don’t have locations associated with them, so it didn’t make sense to have a findNearbyResources action since there would be no locations to compare. Another realization I had was that I didn’t have enough states and actions for the Mapping Concept. Based on feedback from A3, I removed the location state from my Authenticating Concept, which meant that I would lose where I stored the location state of users in my app. Due to this, I rethought where/how I wanted to store location and link location information to the user, which led me to create states in the Mapping Concept directly that represented location information and the user the location belonged to. I also added concepts other than the findNearbyUsers (GET) action I had which would allow for more flexibility for users to opt in and out of sharing their location and to update their location. I did think about creating a new Profiling concept to store location, but wanted to keep location information close to the concept I was using it in.


Some honorable mentions were lowering barriers of access to creating resource groups. Initially I required that users post, comment, and join another group in order to be able to create a resource group to store information material. However, I thought about the purpose of my app: to  help users find information, so I didn’t want to put up obstacles when they were trying to do so.


Overall, I made changes to make implementation and the user experience of my app less ambiguous and more complete. I also thought about the purpose of my app and made changes with this purpose in mind to better fulfill this purpose.
