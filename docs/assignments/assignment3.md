# Assignment 3: Covergent Design

## Pitch 
Are you new to the US and are looking for support? Find it tough to navigate US culture, find resources, and connect with other immigrants who share your experiences? You are not alone. Often times, newly arrived immigrants have many questions and have a hard time finding the resources they need and people they can talk to in order to understand a new culture. Introducing HelloUSA: a social media app intended to help working age immigrants (18+) adjust to life in the US with ease. Whether you need help finding local resources such as ESL classes, want answers to your questions, or want to find a supportive community who understand your experiences, HelloUSA can help! Unlike other apps that either focus on connecting immigrants with resources or facilitating community, HelloUSA aims to provide both of these services in one place. Start your journey in the US off right and join HelloUSA today! [add concepts]

## Concepts
1. Posting
Purpose: Allows users to create items for others to view
Operational Principle: After a user makes a post, other users can view the post. If a user is the author of the original post, that user can update the post's content or delete the post.

State: 

postAuthor -> one User
postContent -> String
setOfPosts -> set Items
timeCreated -> one Date

Action:
add_post(author: User, time: int, content: String)
    set Item's timeCreated to time
    set Item's creator to author
    set Item's contents to content
    add Item to setofPosts

remove_post(postRemover: User)
    require postAuthor is the postRemover
    remove Item from setOfPosts

update_post(postUpdater: User, newContent: String)
    requre postAuthor is postUpdater
    update post's content with newContent

2. Commenting
Purpose: allows users to add replies to viewable items
Operational Principle: after making a comment on an item, users can view the comment on the item whenever the item is brought up and the original user can delete or update the comment they made.

State:

set of comments
user_who_commented -> one User
comment_content -> String
item_commented_on -> one Item

Action:
add_comment()
delete_comment()
update_comment()

3. Mapping
Purpose: allows users to find nearby items
Operational Principle: each user and some items have a location. we can map users to items that have a location nearby the user's location.

State:

user_location -> one Location 
item_location -> one Location

Action:
find_nearby(user_location: Location, item_location: Location)

4. Grouping
Purpose: allows items that share commonalities to be viewed together
Operational Principle: each item has characteristics. we can join items with other items that share similar characteristics.
State:

group_owner
set of groups

Action: 
add_to_group()
remove_from_group()
create_group()
delete_group()

5. Saving
Purpose: rank items by popularity
Operational Principle: after a series of items are upvoted, the items appear ranked by their popularity in votes
State:
Action: 
add_upvote()
remove_upvote()

6. Sessioning
Purpose: encourage users to interact with and create items 
Operational Principle: levels of access are associated with a minimum number of karma points. points can be earned when users create items or contribute to an item in some positive way, else points will be lost. if a user at least meets this minimum, they are granted access to capabilities that can be performed at this level.
State:
Action: 
add karma()
remove karma()

7. Authenticating
Purpose: allow people to use an application as their corresponding user persona
Operational Principle: after a person registers with a username and password, they can 
authenticate themselves as a online user of the application each time they provide the username and password to the application
State:

username -> one String
password -> one String
registered -> set User

Action: 
register()
verify()
login()

## Dependency Diagram


## Wireframes
TBD

## Design Iteration
*Did some collaborative brainstorming with Israel Wong

1. Flag Identifiers

The flag of the users' country is displayed on their profile so users are able to easily find others who come from the same country as them and most likely speak their language.

2. Verification Check Tag

A indicator visible on a user's profile that represents that the user has provided their government ID to verify they are a real person to enhance authenticity and security on the app.

3. Karma Points

Points that are awarded to users when they interact with posts or make posts of their own that are well-intended to encourage users to be active on the app by asking and answering questions as well as make sure users are posting content that is credible and agreeable.

4. Group Intent Evaluation

Users are prompted to answer a short questionnaire about their intent on joining a community within the app to reduce the number of mal-intended users joining communities and to ensure communities are built witha member base that is truly interested in their purpose.

5. Saved Content Groupings

Content that users save are stored in one location and users have the ability to organization the content as they wish by grouping content (ie saved posts, resources, etc).

6. Location + Flag Filtering

A search filter that allows users to view other users that come from their country and live in nearby areas.

7. Personalized Milestones

A checklist for milestones such as the driver's exam, getting a job, etc. that users can check complete to earn badges.

8. AI Quick Answers

An AI chatbot that can provide quick answers to users' questions in the case that a user's questions hasn't been answered for a while or they don't want to wait for someone to respond.

9. Resources Map

A map that displays nearby resources (as pins on the map) in various domains such as healthcare, legal, ESL classes, job centers, etc. so immigrants know where to find resources near them.

10. Multilingual Translations

Users can receive resource information and post content in their respective languages to reduce the language barrier when trying to ask questions and learning from answers to those questions.

11. Community Groups

Users can join groups based on their respective countries, hobbies/interests, location, etc. to meet other immigrants who share commonalities with them and to build a support system.

12. Knowledge Hub

Users can share resources that they have used to learn about the US (ie ESL resources, guides, etc.) to provide another mode of answering other users' questions and to foster a giving community.

13. Upvoting

Users can upvote questions to make relatable questions more visible in discussion threads and can upvote resources as well to indicate how helpful the resource is.

14. Discussion Threads

Users can make posts and other users can respond to these posts to keep an ongoing conversation around a question a user asks. This allows users to ask follow up questions and provide new insights after the initial post is made.

15. Opportunity Board

Users can post about various opportunities on a specialized board such as job openings, events, etc. that can be helpful to the greater community.

16. People Recommendations

Users are recommended to other users if they come from the same country, live in nearby locations, or share mutual connections with other users. 

17. Private Messaging

Users are able to communicate with other users individually to share information or discuss without their conversations being displayed on public discussion forums.

18. Mentor Matching

Users who have been in the US for a while can sign up to be matched to a user who has recently gotten to the US and lives in their area to chat about navigating the US.

19. Anniversaries

When the user has been on the app for 1 year, they will get a notification about their 1 year anniversary on HelloUSA and same for each subsequent year.

20. User Compatibility

Users are able to specify what they are looking for in using HelloUSA and match with people with similar aspirations.

## Design Tradeoffs

a). ***Observation: Stakeholders - Variation in Human Ability*** HelloUSA's resource map (Feature 9) feature may be tough to navigate for someone who has visual impairments, especially if there are multiple location pins clustered together. The map can also be difficult for someone who has limited motor control as zooming in/out and scrolling through the map could be difficult.

b). ***Design Response:*** Provide an side bar option where users can scroll through the locations and view the same information displayed on the map to provide a UI that is easier to navigate for those with limited motor control and screen readers to read off the informational content.

