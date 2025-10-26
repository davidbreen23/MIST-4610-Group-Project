# MIST-4610-Group-Project

## Team Members
1. David Breen (dlb86798@uga.edu)https://github.com/davidbreen23/MIST-4610-Group-Project/blob/main/README.md
2. 1. Jacob Greenwald [@jg79522](https://github.com/jg79522) 
3. Iliana Venegas [@imv2ven](https://github.com/imv2ven) 
4. Alexa Persad [@aepersad](https://github.com/aepersad) 
5. Allison Chaloupek [@allisonchaloupek](https://github.com/allisonchaloupek)

## Problem Description: 
The task at hand is to model and build a relational database for the general operations of a film production company network. The central entity in the model is the ProductionCompany entity, which represents each studio that finances, manages, and oversees film projects. Each production company works collaboratively with agents, actors, crew members, and distribution partners to bring movies from concept to release. The model captures the company’s relationships with agents and contracts, which govern talent representation and project negotiations. It also tracks movies, their filming locations, and production sites, as well as assignments connecting crew members and personnel to those sites. Beyond production, the model reflects the distribution side of operations, linking movies to theaters and corresponding revenue reports that provide insight into financial performance. We will accurately model these relationships, generate sample data, and populate the entities with representative information. We will also perform functioning queries on this data so they may yield valuable business insights into the film production process, such as tracking movie profitability, analyzing agent partnerships, and evaluating personnel and site utilization across projects. 

## Data Model: 
Our model represents the structure of a hypothetical film production network that captures how production companies, agents, personnel, and partners interact throughout the filmmaking process. 
At the top level, the ProductionCompany entity represents different studios that oversee and finance film projects. Each production company works with multiple Agents to secure talent, negotiate agreements, and manage contracts. Similarly, each agent can work with several production companies at once. This many-to-many relationship between ProductionCompany and Agent is represented by the Contract entity, which serves as an associative entity containing details such as compensation, start dates, and end dates. 
Each Agent manages multiple Persons, including actors, directors, and technical staff, establishing a one-to-many relationship between Agent and Person. Every Person can be assigned to various ProductionSites, and each ProductionSite can host multiple people working on different aspects of a film. This many-to-many relationship between Person and ProductionSite is represented by the Assignment entity, which serves as the associative table. The Assignment entity stores key details such as department, assignment ID, and start and end dates. 
The Movie entity is central to the model. Each Movie can be filmed at several Locations, and each location can host multiple movies, creating a many-to-many relationship represented by the ProductionSite associative entity. The ProductionSite table includes information about the filming location name, the site permit, and the start and end dates. 
Movies are also distributed through various TheaterCompanies. Because each movie can be shown by multiple theater companies, and each theater company can screen many movies, this many-to-many relationship is represented by the RevenueReport associative entity. The RevenueReport table captures financial details such as ticket sales and release dates.
Additionally, movies are linked to the Persons who contributed to them—such as actors, directors, and editors—through the Credits associative entity. This many-to-many relationship between Movie and Person records each individual’s credit type and character name if they have one. 
Finally, since a single ProductionCompany can oversee the creation of multiple movies, there is a one-to-many relationship between ProductionCompany and Movie. This ties together the creative, operational, and financial aspects of filmmaking under one company, providing a comprehensive structure for managing the full production lifecycle within the data model. 

<img width="912" height="1097" alt="ProjectDataModel_Final" src="https://github.com/user-attachments/assets/bc8dcba3-c26c-44e4-bcdf-fc8dd76379d7" />

## Data Dictionary:

<img width="706" height="347" alt="Agent" src="https://github.com/user-attachments/assets/4dd76c77-068e-4f75-ad96-4d40578140de" />

<img width="579" height="638" alt="Assignment" src="https://github.com/user-attachments/assets/499ed097-c58f-4727-9e50-85315eb71de0" />

<img width="565" height="637" alt="RevenueReport" src="https://github.com/user-attachments/assets/16797677-c35a-4b75-ba51-945e9769aca9" />

<img width="578" height="610" alt="TheaterCompany" src="https://github.com/user-attachments/assets/c04f05ef-f544-4792-93e1-fe126e8e7c7c" />

## Queries:

<img width="550" height="357" alt="Query_Table" src="https://github.com/user-attachments/assets/a438a616-fb94-4c52-bf6f-6e7afc4da82f" />

1. Query 1: 

Query 1 lists the total ticket sales for movies that did not break even. It does this by comparing the ticket revenue (tickets sold (in thousands) x theater price) the budget for the film. By utilizing LEFT JOIN, the films with no recorded revenue will still be included in the results. Then, it filters the results of the sales of the movies to those that are less than or equal to their budget and orders them by descending total sales. 

<img width="1618" height="827" alt="Query_1" src="https://github.com/user-attachments/assets/2d608ac4-03b1-4920-88cb-82200d4f469a" />

Query 1 allows managers to identify the films that resulted in losses. They can then makes investigate the causes of these losses and can make different decisions in regards to marketing, distribution, writing, or budgeting. This identification can guide the process and greenlighting of future projects. 

2. Query 2: 

Query 2 lists each agent’s name, salary, and number of actors they represent. It uses REGEXP to ensure that the output of the query only returns clients that are actors then sorts the agents alphabetically by last name. 

<img width="1615" height="822" alt="Query_2" src="https://github.com/user-attachments/assets/4caff73b-388b-40e7-9468-44332d597d4d" />

Query 2 provides insight into the agents with the largest client bases which often correlates to the amount of influence and negotiation power they have in the industry. Knowing which agents have the most influence and power allows the production companies to determine which agents to cast through and what to expect in their contracts when budgeting. 

3. Query 3: 

Query 3 lists each actor’s name, the number of films they were in, and the average contract base salary negotiated by their agent (if available). The results are then filtered by film count to show those who have appeared in more films than others. 

<img width="1616" height="827" alt="Query_3" src="https://github.com/user-attachments/assets/5ca98b80-207c-4cd9-9c3e-60f0473f89e5" />

Query 3 assists managers in assessing an actor’s experience and the cost of hiring them. More experience actors would cost more to contract on a film but would most likely yield higher audiences. This information is helpful for making casting decisions while factoring in budgets and movie performance. 

4. Query 4: 

Query 4 calculates the average number of tickets sold for movies, their rating, and their average runtime. It uses a subquery to calculate the total ticket sales per movie before averaging them across movie rating. Then, it orders the results by average ticket volume. 

<img width="1608" height="792" alt="Query_4" src="https://github.com/user-attachments/assets/d6da9c33-f8e7-42e8-ab54-db2db0aa2625" />

Query 4 analyzes the different performances of different movie ratings and allows managers to make informed decisions about which films to endorse. Certain ratings and runtimes may outperform others so studios may allocate more resources towards producing and greenlighting those profitable movies. 

5. Query 5: 

Query 5 counts the number of productions that began at each set location during the first half of the year by filtering the start dates of production sites to the ones that occur between January and June. 

<img width="1604" height="824" alt="Query_5" src="https://github.com/user-attachments/assets/af6f1c04-097f-4498-89b5-186d987d70df" />

Query 5 identifies which locations are the most popular during the busiest time for movie production. This information would assist managers in allocating resources, staff, capacity and contracts. 

6. Query 6: 

Query 6 lists each member of the crew, the number of movies they’ve worked on, and the total number of assignments they’d been responsible for. It filters the results using REGEXP to include only members of the crew without the cast members. It orders by the number of assignments to highlight the most active crew member. 

<img width="1597" height="794" alt="Query_6" src="https://github.com/user-attachments/assets/05a0fcbb-6732-4de9-9ca9-cc97ef2bcdc7" />

Query 6 allows managers to identify the top-performing crew members who have the most experience. This information assists managers with staffing allocations, promotions, and future team planning. 

7. Query 7: 

Query 7 identifies the movies that have a higher budget than the average budget of films with the same maturity rating. It uses a correlated subquery to compare budgets and the query orders the films by ticket sales to display the most popular sales with their specific budget and rating. 

<img width="1606" height="807" alt="Query_7" src="https://github.com/user-attachments/assets/fbbfc366-8d23-4578-a0af-09c8cb2cc20d" />

Query 7 allows managers to see if higher budgets in specific ratings correlate to higher or lower ticket sales. This information would assist in budgeting, production involvement risk, and greenlighting decisions. 

8. Query 8: 

Query 8 ranks theaters based on the total revenue generated by ticket sales. It multiplies ticket volume (in thousands) by the price offered by the particular theater to determine the revenue and then orders the theaters according to the highest to lowest revenue. 

<img width="1606" height="808" alt="Query_8" src="https://github.com/user-attachments/assets/22ca48df-5e9f-4465-beb6-ca05a4ee83a0" />

Query 8 shows the highest performing theaters which would allow managers to make decisions on where to distribute their films to aim for the highest profit. They can use these results to optimize marketing efforts, locations for exclusive events, and distribution strategies. 

9. Query 9: 

Query 9 calculates the average number of days required to complete productions at each set location. It takes the difference between start and end dates to determine the time frame and then orders the locations by the shortest time frames to the largest. 

<img width="1606" height="819" alt="Query_9" src="https://github.com/user-attachments/assets/75f7ac7e-e043-421f-8e86-71de584192c8" />

Query 9 provides managers with the efficiency of each location. They can use these metrics to create strategies for which locations to schedule productions more frequently, which location to pick for a particular film’s timeline, and overall budgeting for production timing.

10. Query 10: 

Query 10 identifies movies that have no revenue reports by checking the existence of the report for each film. 

<img width="1604" height="800" alt="Query_10" src="https://github.com/user-attachments/assets/65443d83-49d4-416c-a33f-d7e9f71e5852" />

Query 10 flags the potential missing data associated with films or the films who have generated 0 sales. Managers use this to check for errors within the revenue reporting department or address possible issues to prevent a null value within their records. 

## Database Information: 

Name of the database: ns_F25MIST4610_59925_Group1 

Additional information: Each query listed above is marked in the database using stored procedures which can be called using the following format: CALL TP_Q1(); 
