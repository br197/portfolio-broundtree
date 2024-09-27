# Assignment 3: Covergent Design

## Pitch 
Are you new to the US and are looking for support? Find it tough to navigate US culture, find resources, and connect with other immigrants who share your experiences? You are not alone. Often times, newly arrived immigrants have many questions and have a hard time finding the resources they need and people they can talk to in order to understand a new culture. Introducing HelloUSA: a social media app intended to help working age immigrants (18+) adjust to life in the US with ease. Whether you need help finding local resources such as ESL classes, want answers to your questions, or want to find a supportive community who understand your experiences, HelloUSA can help! Unlike other apps that either focus on connecting immigrants with resources or facilitating community, HelloUSA aims to provide both of these services in one place. Start your journey in the US off right and join HelloUSA today! 

**Key Features:**
- **Nearby User and Resource Mapping:** Find other users and resources nearby your location to find the help you need 
                                    and make connections!

- **Progress Milestones:** Track your progress in engaging with HelloUSA and adjusting to the US by earning badges
                        that help you unlock new features on the app! When you log into HelloUSA, you will automatically earn your first milestone badge, allowing you to join community groups on the app.

- **Community Groups:** Join groups that share similar backgrounds and goals as you! When you are logged in, you can post content and comment on other users' content within groups to interact with the HelloUSA community.

- **Personalized Boards:** Customize your experience on HelloUSA by grouping posts, resources, and other content onto
                            boards organized by a topic of your choice!


## Concepts

### concept Posting[User, Item, Date]

- **Purpose:** Allows users to create items for others to view

- **Operational Principle:** After a user creates a post, another user can view the post. If a user is the author of the original post, that user can update the post item or delete the post item. Users can also view the posts they have personally made

- **States:**

    - postAuthor: Item -> one User
    - postContent: Item -> one String
    - postDateCreated: Item -> one Date
    - userPosts: User -> set Item

- **Actions:**

    **createPost(author: User, date: Date, content: String)**

        set item's postDateCreated to date
        set item's postAuthor to author
        set item's postContent to content
        add item's to userPosts

    **removePost(postToRemove: Item, postRemover: User)**

        require that postAuthor of the post is the postRemover
        remove postToRemove from userPosts

    **updatePost(postUpdater: User, newContent: String, post: Item)**

        require that the postAuthor of the post is the postUpdater
        update postContent of post with newContent
    
    **getPosts(user: User, out userPosts)**
    
        posts in userPosts of user

### concept Commenting[User, Reply, Item, Date]

- **Purpose:** Allow users to reply to viewable items

- **Operational Principle:** After adding a comment on an item, users can view the comment on the item whenever the item is in view and the original user can delete or update the comment they made.

- **State:**
    - setOfComments: Item -> set Reply
    - commentAuthor: Reply -> one User
    - commentContent: Reply -> one String
    - commentTimeCreated: Reply -> one Date

- **Actions:**

    **addComment(author: User, itemToReplyTo: Item, date: Date, content: String)**

        set comment's commentAuthor to author
        set comment's commentTimeCreated to date
        set comment's commentContent to content
        add comment to setOfComments for itemToReplyTo

    **deleteComment(commentRemover: User, deleteReply: Reply, repliedItem: Item)**

        require that commentRemover is commentAuthor
        remove deleteReply from setofComments for repliedItem

    **updateComment(commentUpdater: User, newContent: String, comment: Reply)**

        require that commentUpdater is commentAuthor
        replace original content of comment with newContent

### concept Mapping[Location]

- **Purpose:** Allows items to find nearby items

- **Operational Principle:** Each item has a location. We can map an item to items that have nearby locations to find nearby items.

- **States:**
    - itemLocation: Item -> one Location
    - radius: one int
    - setofLocations: set Location

- **Actions:**

    **findNearbyItems(itemLocation1: Location, locations: Location, radius: int, out nearbyLocations: Location)**

        require that itemLocation1 and location in locations is within radius units

### concept Grouping[Item, Collection]

- **Purpose:** Allows items that share commonalities to be viewed together

- **Operational Principle:** Each item has characteristics. We can group items that share similar characteristics together. Items can join groups, create, and leave groups. If the item owns the group, it can edit the group name, description, and delete the group.

- **State:**
    - groupMembers: set Item
    - setOfGroups: set Collection
    - groupName: Collection -> one String
    - groupOwner: Collection -> one User
    - groupDescription: one String

- **Actions:** 

    **joinGroup(item: Item, groupName: String)**

        require item not already in groupMembers

        when item is joining group with groupName, add item to groupMembers 
        of group 

    **leaveGroup(item: Item, groupName: String)**

        require that item is in groupMembers

        when user is leaving group with groupName, remove item from groupMembers of the
        group

    **createGroup(user: User, groupName: String, description: String)**

        require that group with groupName is not in setOfgroups
        set groupOwner to user
        set groupDescription to description
        add group with groupName to setOfGroups
        

    **deleteGroup(groupName: String, deleter:User)**

        require that group with groupName is in setOfgroups and deleter is groupOwner
        remove group with groupName from setOfGroups
    
    **editGroupName(user:User, newName: String)**

        require that user is groupOwner of group
        replace group's groupName with newName
    
    **editGroupDescription(user:User, newDescription: String)**

        require that user is groupOwner of group
        replace group's groupDescription with newDescription

### concept Milestone-ing[Milestone, User]

- **Purpose:** Allow the user to track their progress 

- **Operational Principle:** After a user completes a milestone, they receive a badge 
to recognize completing that milestone. Users can view all the badges they have earned as well.

- **States:**

    - setOfMilestones: set Milestone
    - badge: one Milestone
    - userMilestones: User -> set Milestone

- **Actions:**

    **receiveBadge(user:User, badge: Milestone)**

        require that badge is not already in userMilestones of the user 

        when a user completes a milestone from setOfMilestones, add badge to 
        userMilestones

    **getBadges(user:User, out badges: Milestone)**

        output userMilestones of user

### concept Sessioning[Session]

- **Purpose:** enable authenticated actions for an extended period of time

- **Operational Principle:** after a session starts for a user, as long as their session is active, 
the user can perform authenticated actions until the session is ended.

- **State:**
    - activeUser: one User
    - sessions: set Session

- **Action:**

    **startSession(user:User, out session:Session)**

        set user to activeUser

    **isActive(user:User, out session:Session)**

        require that user is an activeUser

    **endSession(user:User, session: Session)**

        require that the user is an activeUser
        remove user as the activeUser and their session from sessions


### concept Authenticating[User, Location]

- **Purpose:** allow person to use an application as their corresponding user persona

- **Operational Principle:** after a person registers with a username, password, and provides 
their location, they can authenticate themselves as a online user of the application each time login 
with their provide the username and password to the application. They can stop being their user persona 
by logging out.

- **States:**
    - username: User -> one String
    - password: User -> String
    - registered: set User
    - loggedIn: User -> one User
    - location: one Location

- **Action:**

    **register(username: String, password: String, location: Location, out user:User)**  

        require that user with username and password is not already in registered
        set user username to username
        set user password to password
        set user location to location
        add User to registered

    **login(username: String, password:String, out user:User)**

        require that user is in registered and not already loggedIn

        when user provides application with username and password, set loggedIn to user

    **logout(user: User)**

        require that user is loggedIn
        when user logs out, remove user from loggedIn

## Synchronizations

**app HelloUSA**

    **include** Posting[User, Post, Date]
    **include** Commenting[User, Reply, Post, Date]
    **include** Mapping[User.Location]
    **include** Mapping[Resource.Location]
    **include** Grouping[Resource, Group]
    **include** Grouping[User, Group]
    **include** Milestone-ing[Milestone, User]
    **include** Sessioning[Session]
    **include** Authenticating[User, Location]
    
    
**sync register(username: String, password:String, location:Location, out user:User)**

    Authenticating.register(username, password, location)
    Milestone-ing.receiveBadge(user) called Created Account

**sync login(username: String, password: String, out user: User, out session:Session)**

    Authenticating.login(username, password)
    Sessioning.startSession(user, session)

**sync logout(user:User)**

    Sessioning.endSession(user)
    Authenticating.logout(user)

**sync receiveBadge(user:User, badge: Milestone)**

    Sessioning.isActive(user)
    Milestone-ing.receiveBadge(user, badge, milestone)

**sync getBadges(user:User, out badges:Milestone)**

    Sessioning.isActive(user)
    Milestone-ing.getBadges(user)

**sync joinUserGroup(user: User, user:User, groupName: String)**

    Sessioning.isActive(user)
    if Milestone-ing.getBadges(user) has create account badge:
        Grouping.joinGroup(user, groupName)
        if it is the first time a user is joining a group: 
            Milestone-ing.receiveBadge(user) called Building Community

**sync joinResourceGroup(user:User, resource:Resource, groupName: String)**

    Sessioning.isActive(user)
    if Milestone-ing.getBadges(user) has create account badge:
        Grouping.joinGroup(resource, groupName)
        if it is the first time a user adds resource to a group: 
            Milestone-ing.receiveBadge(user) called Resource Groups

**sync leaveUserGroup(user:User, groupName: String)**

    Sessioning.isActive(user)
    Grouping.leaveGroup(user, groupName)

**sync leaveResourceGroup(resource:Resource, groupName: String)**

    Sessioning.isActive(user)
    Grouping.leaveGroup(resource, groupName)

**sync createUserGroup(user: User, groupName: String, description: String, out group: Group)**

    Sessioning.isActive(user)
    if Milestone-ing.getBadges(user) has posting, commenting, and Created Account badge:
        Grouping.createGroup(user, groupName, description)

**sync createResourceGroup(user:User, resource: Resource, groupName: String, description: String, out group: Group)**

    Sessioning.isActive(user)
    if Milestone-ing.getBadges(user) has posting, commenting, and Created Account badge:
        Grouping.createGroup(resource, groupName, description)

**sync deleteUserGroup(groupName: String, deleter:User)**

    Sessioning.isActive(user)
    Grouping.deleteGroup(groupName, deleter)

**sync editGroupName(user:User, newName: String)**

    Sessioning.isActive(user)
    Grouping.editGroupName(user, newName)
    
**sync editGroupDescription(user:User, newDescription: String)**

    Sessioning.isActive(user)
    Grouping.editGroupDescription(user, newDescription)

**sync findNearbyUsers(userLocation: User.Location, locations:Location, radius: int)**

    Sessioning.isActive(user)
    Mapping.findNearbyItems(userLocation, locations, radius)
    if it is the first time a user tries to find nearby users: 
        Milestone-ing.receiveBadge(user) called Branching Out

**sync findNearbyResources(resourceLocation: Resource.Location, locations:Location, radius: int)**

    Sessioning.isActive(user)
    Mapping.findNearbyItems(resourceLocation, locations, radius)
    if it is the first time a user tries to find nearby resources: 
         Milestone-ing.receiveBadge(user) called Knowledge Power

**sync createPost(author: User, date: Date, content: String)**

    Sessioning.isActive(author)
    Posting.createPost(author, date, content)
    if it is the first time a user makes a post: 
        Milestone-ing.receiveBadge(user) called Post Superstar
    

**sync removePost(postToRemove: Post, postRemover: User)**

    Sessioning.isActive(postRemover)
    Posting.removePost(postToRemove, postRemover)

**sync updatePost(postUpdater: User, newContent: String, post: Post)**

    Sessioning.isActive(postUpdater)
    Posting.updatePost(postUpdater, newContent, post)
    
**sync getPosts(user: User, out userPosts: Post)**

    Sessioning.isActive(user)
    Posting.getPosts(user)

**sync addComment(author: User, itemToReplyTo: Post, date: Date, content: String)**

    Sessioning.isActive(user)
    Commenting.addComment(author, itemToReplyTo, date, content)
    if it is the first time a user is commenting: 
        Milestone-ing.receiveBadge(user) called Comment Guru

**sync deleteComment(commentRemover: User, deleteReply: Reply, repliedItem: Post)**

    Sessioning.isActive(user)
    Commenting.deleteComment(commentRemover, deleteReply, repliedItem)

**sync updateComment(commentUpdater: User, newContent: String, comment: Reply)**

    Sessioning.isActive(user)
    Commenting.updateComment(commentUpdater, newContent, comment)


## Dependency Diagram
<img src="/assets/images/6.1040a3.jpeg" width=400 height=400>

## Wireframes
Link to wireframe: "https://www.figma.com/design/JFFW1SFc0OThzSqxOTEjVK/A3-HelloUSA?node-id=4-668&t=SZzqRqLpxy3cbB4l-1"

## Design Iteration

- ### Authorized Creation of Groups
    - **Options:** Allow everyone to create a group, limit who can create groups, 
               have broad pre-existing list of groups (no group creation)

    - **Rationale:** I wanted to implicitly enforce integrity on HelloUSA and allow users to
                    create communities of their own on the app. I thought about having a broad pre-existing
                    list of groups that can't be added onto to provide users with a variety of communities to choose
                    from. However, I felt that this would limit the freedom of users to connect with others and make
                    the app their own. I also thought about the other side of allowing all users to freely create 
                    groups without barriers. This, however, can have app integrity consequences as people or bots can
                    abuse this functionality by creating harmful or a plethora of groups at once. I landed on 
                    limiting who can create groups by providing a barrier through achievable milestones. This 
                    ensures that group creators are active and agreeable on the app.

- ### Where to Post?
    - **Options:** Posting in a public feed, posting in community groups

    - **Rationale:** I wanted to organize posts based on topic but also provide a way for users to see a collection
                    of posts when they log in. I thought about allowing posting on a public feed, but realized
                    that post topics may be cluttered. Since one of the purposes of my app is to provide
                    answers to immigrants' questions, I didn't want the questions topics of posts to get mixed up
                    and become hard to follow by my users. So, I opted to have posting solely in community groups. 
                    Community groups have a defined title and description so if posts were made in the groups,
                    users will have an idea of what type of posts/questions they will see and what type of topics 
                    they can discuss via posts/comments in the group.


- ### Connections via Location
    - **Options:** Connecting users via location, connecting users via background similarities, connecting users via
                    language

    - **Rationale:** I wanted a method to connect users who share a similarity. While I recognize that background,
                    language, and location are all important, I thought it would be most practical given the time constraint to connect users via location (ie connecting users who are nearby each other). Location
                    implicitly entails similarity in background and sometimes language.
