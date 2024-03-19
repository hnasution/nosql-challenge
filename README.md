# Module 12 - NOSQL Challenge

Before You Begin
1. Create a new repository for this project called  nosql-challenge . Do not add this homework to an existing repository.
2. Clone the new repository to your computer.
3. Add your Jupyter notebook starter  les and your Resources folder containing  establishments.json  to this folder.
4. Push the changes to GitHub.

Instructions
The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. You've been
contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics
decide where to focus future articles.

Part 1: Database and Jupyter Notebook Set Up
Use  NoSQL_setup_starter.ipynb  for this section of the challenge.

1. Import the data provided in the  establishments.json   le from your Terminal. Name the database  uk_food  and the collection  establishments .
Copy the text you used to import your data from your Terminal to a markdown cell in your notebook.
2. Within your notebook, import the libraries you need: PyMongo and Pretty Print ( pprint ).
3. Create an instance of the Mongo Client.
4. Con rm that you created the database and loaded the data properly:
List the databases you have in MongoDB. Con rm that  uk_food  is listed.
List the collection(s) in the database to ensure that  establishments  is there.
Find and display one document in the  establishments  collection using  find_one  and display with  pprint .
5. Assign the  establishments  collection to a variable to prepare the collection for use.

Part 2: Update the Database
Use  NoSQL_setup_starter.ipynb  for this section of the challenge.
The magazine editors have some requested modi cations for the database before you can perform any queries or analysis for them. Make the
following changes to the  establishments  collection:
1. An exciting new halal restaurant just opened in Greenwich, but hasn't been rated yet. The magazine has asked you to include it in your analysis.
Add the following information to the database:
{
    "BusinessName":"Penang Flavours",
    "BusinessType":"Restaurant/Cafe/Canteen",
    "BusinessTypeID":"",
    "AddressLine1":"Penang Flavours",
    "AddressLine2":"146A Plumstead Rd",
    "AddressLine3":"London",
    "AddressLine4":"",
    "PostCode":"SE18 7DY",
    "Phone":"",
        "LocalAuthorityCode":"511",
    "LocalAuthorityName":"Greenwich",
    "LocalAuthorityWebSite":"http://www.royalgreenwich.gov.uk",
    "LocalAuthorityEmailAddress":"health@royalgreenwich.gov.uk",
    "scores":{
        "Hygiene":"",
        "Structural":"",
        "ConfidenceInManagement":""
    },
    "SchemeType":"FHRS",
    "geocode":{
        "longitude":"0.08384000",
        "latitude":"51.49014200"
    },
    "RightToReply":"",
    "Distance":4623.9723280747176,
    "NewRatingPending":True
}

2. Find the BusinessTypeID for "Restaurant/Cafe/Canteen" and return only the  BusinessTypeID  and  BusinessType   elds.
3. Update the new restaurant with the  BusinessTypeID  you found.
4. The magazine is not interested in any establishments in Dover, so check how many documents contain the Dover Local Authority. Then, remove
any establishments within the Dover Local Authority from the database, and check the number of documents to ensure they were deleted.
5. Some of the number values are stored as strings, when they should be stored as numbers.

1. Use  update_many  to convert  latitude  and  longitude  to decimal numbers.
2. Use  update_many  to convert  RatingValue  to integer numbers.

## Part 3: Exploratory Analysis
Eat Safe, Love has speci c questions they want you to answer, which will help them  nd the locations they wish to visit and avoid.
Use  NoSQL_analysis_starter.ipynb  for this section of the challenge.
Some notes to be aware of while you are exploring the dataset:
RatingValue  refers to the overall rating decided by the Food Authority and ranges from 1-5. The higher the value, the better the rating.

## Question 1. Which establishments have a hygiene score equal to 20?
# Answer: There are 41 documents in the result

## Question 2. Which establishments in London have a `RatingValue` greater than or equal to 4?
# Answer: There are 33 establishments in London with a RatingValue greater than or equal to 4.

## Question 3. What are the top 5 establishments with a `RatingValue` rating value of 5, sorted by lowest hygiene score, nearest to the new restaurant added, "Penang Flavours"?
## Answer: 
1. Ancient and Brave
2. Texaco Service Station
3. Eltham Green School Nursery Ltd	
4. Gill's eells
5. Monkey Puzzle Eltham

## Question 4. How many establishments in each Local Authority area have a hygiene score of 0?
# Answer: 55