# Assignment 4: Backend Design & Implementation

## Data Modeling

### Posting[Item, User, Date]

**States:**
- setOfPosts: set of Item
- postAuthor: setOfPosts -> one User
- postContent: setOfPosts -> one String
- postDateCreated: setOfPosts -> one Date

<img src="/assets/images/postingmodel.jpeg" width="400px" height="400px">

### Commenting[Item, User, Date, Reply]

**States:**
- setOfComments: Item -> set Reply
- commentAuthor: Reply -> one User
- commentContent: Reply -> one String
- commentTimeCreated: Reply -> one Date

<img src="/assets/images/commentingmodel.jpeg" width="400px" height="400px">

### Mapping[Item, Location]

**States:**
- itemLocation: Item -> one Location

<img src="/assets/images/mappingmodel.jpeg" width="400px" height="400px">

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
- setofMilestones: set Milestone
- userMilestone: Milestone -> set User

<img src="/assets/images/milestoningmodel.jpeg" width="400px" height="400px">

### Sessioning[User]

**States:**
- session: set of Sessions
- activeUser: session -> one User

<img src="/assets/images/sessioningmodel.jpeg" width="400px" height="400px">

### Authenticating[Location]

**States:**
- registered: set User
- username: registered -> one String
- password: registered -> one String
- location: registered -> one Location

<img src="/assets/images/authmodel.jpeg" width="400px" height="400px">

## App
***include Date***

***include Location***

***include Milestone***

***include Authenticating[Location]***

***include Sessioning[Authenticating.User]***

***include Posting[String, Sessioning.User, Date]***

***include Commenting[Posting.Post, Sessioning.User, Date, String]***

***include Mapping[Sessoning.User, Location]***

***include Grouping[Collection, Sessioning.User, Authenticating.Registered]***

***include Milestone-ing[Milestone, Sessioning.User]***

## Global Data Model
<img src="/assets/images/globaldatamodel.jpeg" width="400px" height="400px">

## Code

**Deployed Service:** ---
**GitHub Repository:** [link](https://github.com/br197/a4-backend)

## Design Reflection

While working on the backend, I had to make several changes to my concepts. For example, when I was implementing milestones, instead of getting all milestones possible, I changed it to getting only milestones for a user to make the milestoning concept more personable. I also made a lot of changes to how I wrote out my concept states when making my data models, such as element the userPosts state. In regards to my group concept, I decided to only focus on grouping users rather than other items (ie resources) in order to ensure that my backend was working properly for at least one case. I wanted to extend grouping to resources, but decided to focus on only one item type (User) given the time constraint.