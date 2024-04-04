# Group 4 MIST 4610 Group project 1

## Team Name: 
20244 Group 4

## Team Members:

1. Ryan Overbeck https://github.com/rjo82443?tab=repositories
2. Minwoo Park
3. Brooke Carlisle
4. Mathias Flanagan
5. Connor Walker

## Problem Description:
Pretend you are the owner/operator of a Cricket club needing to build a relational database. You hired some students from the MIST 4610 class at the University of Georgia to create the database for you. They need to know more about your organization to identify which entities, attributes, and relationships are important for you. Start by describing your business as a real client.

## Data Model

Explanation of data model: 

Our model is built around a hypothetical cricket club, where various entities work together to facilitate smooth club operations and player management. At the core of our model is the membership management entity, which includes both members (players) and operational aspects such as key tasks needed to run a club like event management and financial tracking. The membership management table uses a unique memberID as its primary key, establishing a one-to-one relationship with financial management with the transactionID as a foreign key, highlighting how members interact with the club's finances. 

Next, the relationship between Member Management and Player Profiles is characterized by a one-to-one relationship, emphasizing a direct link between club membership and player profiles. This direct connection makes it easy to integrate member information with player details as all players are members of the club. In the Player Profile table, there is a one-to-many relationship with Team Management, showing how players and teams in the club interact. This relationship leads to the associative entity known as the roster, which depicts the players of each team, utilizing the teamID and playerID as foreign keys. Additionally, Team Management establishes a one-to-one relationship with Coaching and Development, signifying that each team has a single head coach. Furthermore, the Coaching and Development entity also features a one-to-one recursive relationship, representing the presence of assistant coaches within the coaching staff hierarchy. 

Examining further, the Event and Tournament entity is vital in handling the setup of cricket events and tournaments. Due to the multifaceted nature of event planning, this entity features many connections with other entities. For instance, the association with Team Management displays the inclusion of teams participating in the event via teamID as the foreign key and Umpire Management depicts the identification of umpires involved in specific events through umpireID. Sponsor ties to events are tracked in a one-to-many relationship with the Sponsorship and Partnership table, ensuring sponsorship deals are well managed. Furthermore, all newsletters pertaining to the event are highlighted in the Event and Tournament Management table through a one-to-many relationship, with newsletterID as the foreign key, enabling efficient communication with everyone involved in the event. Lastly, the inclusion of facilities and equipment used in events is depicted by a one-to-many relationship with the Facility and Equipment Management table, which further connects to the Volunteer and Staff Management section to list staff members associated with event venues. 

In essence, the relationships within our data model reflect the many interactions within the cricket club, facilitating the seamless management of members, players, teams, events, and all resources. Each entity has its own purpose, contributing to the overall seamless functioning of the club and ensuring efficient coordination across all operational domains.




![image](https://github.com/rjo82443/Cricket_Group4/assets/163200122/53f061a2-fef2-4a3e-9c55-b82dcd8a4349)



## Data Dictionary:

### Membership Management

| Column Name        | Description                            | Data Type | Size | Format           | Key? |
|--------------------|----------------------------------------|-----------|------|------------------|------|
| memberID           | Unique identifier for members          | INT       |      |                  | PK   |
| Name               | Name of the member                     | VARCHAR   | 45   | Last, First      |      |
| DateOfBirth        | Date of birth of the member            | DATE      |      | MM/DD/YYYY       |      |
| ContactInformation | Contact details of the member          | VARCHAR   | 120  | (XXX) - XXX-XXXX |      |
| MembershipType     | Type of Membership                    | VARCHAR   | 45   |                  |      |
| JoiningDate        | Date when the member joined            | DATE      |      | MM/DD/YYYY       |      |
| PaymentStatus      | Status of membership payment           | VARCHAR   | 45   |                  |      |
| financialManagement_transactionID      | Unique identifier for transactions     | INT       |      |                  | FK (ref. Financial Management) |

### Player Profiles

| Column Name        | Description                            | Data Type | Size | Format           | Key? |
|--------------------|----------------------------------------|-----------|------|------------------|------|
| PlayerID           | Unique identifier for players          | INT       |      |                  | PK   |
| Name               | Name of the player                     | VARCHAR   | 45   | Last, First      |      |
| dateofBirth        | Date of birth of the player            | DATE      |      | MM/DD/YYYY       |      |
| contactInfo | Contact details of the player          | VARCHAR   | 120  | (XXX)-XXX-XXX   |      |
| positionPlayed     | Position played by the player          | VARCHAR   | 45   |                  |      |
| battingAverage     | The batting average of the player      | DECIMAL   | (1,3)| X.XXX            |      |
| BowlingAverage     | Bowling average of the player          | DECIMAL   | (1,3)| X.XXX            |      |
| MatchesPlayed      | Number of matches played               | INT       |      |                  |      |
| MemberID           | Unique identifier for members          | INT       |      |                  | FK (ref. Membership Management) |

### Team Management

| Column Name    | Description                          | Data Type | Size | Format        | Key? |
|----------------|--------------------------------------|-----------|------|---------------|------|
| TeamID         | Unique identifier for teams          | INT       |      |               | PK   |
| teamName       | Name of the team                     | VARCHAR   | 45   |               |      |
| ageGroup       | The age group of the team            | VARCHAR   | 45   |               |      |
| homeGround     | The home ground of the team          | INT       | 45   |               |      |
| matchSchedule  | Schedule of matches                  | VARCHAR   | 500  |               |      |
| Results        | Results of matches                   | VARCHAR   | 500  |               |      |
| CoachingandDevelopment_CoachID        | Identifier of the coach              | INT       |      |               | FK (ref. coaching and development) |

### Facility and Equipment

| Column Name          | Description                          | Data Type | Size | Format        | Key? |
|----------------------|--------------------------------------|-----------|------|---------------|------|
| facilityID           | Unique identifier for facilities     | INT       |      |               | PK   |
| facilityName         | Name of the facility                  | VARCHAR   | 45   |               |      |
| location             | Location of the facility             | VARCHAR   | 45   |               |      |
| euipmentID          | Identifier of the equipment          | INT       |      |               | PK   |
| availabilitySchedule | Schedule of availability             | VARCHAR   | 500  |               |      |
| maintenanceStatus    | Status of maintenance                | VARCHAR   | 500  |               |      |
| voulAndStaffManagement_StaffID              | Unique identifier for volunteers and staff | INT       |      |               | FK (ref. volunteer and staff management) |

### Event and Tournament Management

| Column Name        | Description                          | Data Type | Size | Format        | Key? |
|--------------------|--------------------------------------|-----------|------|---------------|------|
| eventID            | Unique identifier for events         | INT       |      |               | PK   |
| eventName          | Name of the event                    | VARCHAR   | 45   |               |      |
| DATE               | Date of the event                    | DATE      |      | MM/DD/YYYY    |      |
| venue              | Venue of the event                   | VARCHAR   | 45   |               |      |
| teams | Teams participating in the event     | VARCHAR   | 500  |               |      |
| Results            | Results of the event                 | VARCHAR   | 45   |               |      |
| AWARDS             | Awards given in the event            | VARCHAR   | 45   |               |      |
| teamManagement_teamID             | Unique identifier for teams          | INT       |      |               | FK(ref.Team Management) |
| facilityAndEquipment_facilityID         | Unique identifier for Facility       | INT       |      |               | FK(ref.Facility and Equipment Management) |
| umpireManagement_umpireID           | Unique identifier for Umpire         | INT       |      |               | FK(ref. Umpire Management) |
| CommAndMark_newsletterID       | Unique identifier for newsletter     | INT       |      |               | FK(ref. Communication and Marketing) |
| sponsorshipAndPartnerships_sponsorID          | Unique identifier for sponsor        | INT       |      |               | FK(ref.Sponsorship and Partnerships) |

### Coaching and Development

| Column Name              | Description                          | Data Type | Size | Format          | Key? |
|--------------------------|--------------------------------------|-----------|------|-----------------|------|
| coachID                  | Unique identifier for coaches        | INT       |      |                 | PK   |
| coachName                | Name of the coach                    | VARCHAR   | 45   | Last, First     |      |
| qualifications           | Qualifications of the coach          | VARCHAR   | 45   |                 |      |
| trainingSchedule         | Schedule of training                 | VARCHAR   | 500  | Week/ Time /Date |      |
| playerDevelopmentProgram | Program for player development       | VARCHAR   | 45   |                 |      |
|performanceAssessments   | Assessments of performance           | VARCHAR   | 45   |                 |      |
| AssistantCoaches          | ID of Assistant Coach                | INT       |      |                 | FK(ref Coaching and Development- Recursive Relationship) |

### Financial Management

| Column Name   | Description                          | Data Type | Size | Format      | Key? |
|---------------|--------------------------------------|-----------|------|-------------|------|
| transactionID | Unique identifier for transactions  | INT       |      |             | PK   |
| Date          | Date of the transaction              | DATE      |      | MM/DD/YYYY  |      |
| type          | Type of transaction (Income/Expense) | VARCHAR   | 45   |             |      |
| Amount        | Amount of the transaction            | DECIMAL   | (8,2)| XX.XX       |      |
| Description   | Description of the transaction       | VARCHAR   | 500  |             |      |
| BudgetCategories | Categories in the budget          | VARCHAR   | 45   |             |      |

### Communication and Marketing

| Column Name       | Description                          | Data Type | Size | Format      | Key? |
|-------------------|--------------------------------------|-----------|------|-------------|------|
| newsletterID      | Unique identifier for newsletters    | INT       |      |             | PK   |
| date              | Date of the newsletter               | DATE      |      | MM/DD/YYYY  |      |
| Content           | Content of the newsletter            | VARCHAR   | 450  |             |      |
| recipients        | Recipients of the newsletter         | VARCHAR   | 450  |             |      |
| socialMediaPosts  | Posts on social media                | VARCHAR   | 45   |             |      |
| eventParticipation | Participation in community events  | VARCHAR   | 45   |             |      |

### Volunteer and Staff Management

| Column Name         | Description                          | Data Type | Size | Format      | Key? |
|---------------------|--------------------------------------|-----------|------|-------------|------|
| staffID             | Unique identifier for staff          | INT       |      |             | PK   |
| VolunteerID         | Identifier of the volunteer          | INT       |      |             | PK   |
| NAME                | Name of the staff                    | VARCHAR   | 45   | Last, First |      |
| Role                | Role of the staff                    | VARCHAR   | 45   |             |      |
| contactInfo  | Contact details of the staff         | VARCHAR   | 120  |             |      |
| Schedule            | Schedule of the staff                | VARCHAR   | 45   |             |      |

### Umpire Management

| Column Name         | Description                          | Data Type | Size | Format      | Key? |
|---------------------|--------------------------------------|-----------|------|-------------|------|
| umpireID            | Unique identifier for umpires        | INT       |      |             | PK   |
| name                | Name of the umpire                   | VARCHAR   | 45   | Last, First |      |
| certification       | Certification status of the umpire   | VARCHAR   | 45   |             |      |
| contactInfo  | Contact details of the umpire        | VARCHAR   | 120  |             |      |
| Availability        | Availability of the umpire           | VARCHAR   | 450  |             |      |
| performanceReviews  | Reviews of umpire performance        | VARCHAR   | 450  |             |      |

### Sponsorship and Partnership

| Column Name         | Description                          | Data Type | Size | Format      | Key? |
|---------------------|--------------------------------------|-----------|------|-------------|------|
| sponsorID           | Unique identifier for sponsors       | INT       |      |             | PK   |
| Name                | Name of the sponsor                  | VARCHAR   | 45   |             |      |
| Type                | Type of sponsor (Sponsor/Partner)    | INT       | 45   |             |      |
| agreementDetails    | Details of the sponsorship agreement | INT       | 45   |             |      |
| FinancialContributions | Contributions made by the sponsor  | DECIMAL   | (8,2)| XXX.XX      |      |
| PromotionalActivities | Activities undertaken by sponsor   | VARCHAR   | 45   |             |      |

### Fan Engagement

| Column Name          | Description                          | Data Type | Size | Format      | Key? |
|----------------------|--------------------------------------|-----------|------|-------------|------|
| fanID                | Unique identifier for fans           | INT       |      |             | PK   |
| Name                 | Name of the fan                      | VARCHAR   | 45   | Last,First  |      |
| contactInfo   | Contact details of the fan           | VARCHAR   | 120  |             |      |
| attendanceHistory    | History of fan attendance            | VARCHAR   | 450  |             |      |
| merchandisePurchases | Amount of money spent on merchandise | DECIMAL   | (6,2)| XX.XX       |      |
| LoyaltyPoints        | Number of loyalty points earned      | INT       |      |             |      |
| teamManagement_teamID               | Identifier of team-specific fan supports | INT   |      |             | FK(ref. Team Management) |

### Player History - Associative Entity

| Column Name | Description                             | Data Type | Size | Format      | Key? |
|-------------|-----------------------------------------|-----------|------|-------------|------|
| memberID    | Unique identifier for players/members           | INT       |      |             | FK (ref.Player Profile) |
| eventID     | Unique identifier for event/tournament   | INT       |      |             | FK (ref. Event and Members) |

### Roster - Associative Entity

| Column Name | Description                          | Data Type | Size | Format      | Key? |
|-------------|--------------------------------------|-----------|------|-------------|------|
| PlayerID    | Unique identifier for players        | INT       |      |             | FK (ref.Player Profiles) |
| teamID      | Unique identifier for Teams          | INT       |      |             | FK (ref. Team Management) |


## Queries:
| Query Identification    | Query 1 | Query 2 | Query 3 | Query 4 | Query 5 | Query 6 | Query 7 | Query 8 | Query 9 | Query 10 |
|-------------------------|---------|---------|---------|---------|---------|---------|---------|---------|---------|----------|
| Simple                  |         |     X    |      X   |         |   X      |     X    |         |         |         |          |
| Complex                 |   X      |         |        |  X       |        |         |    X     |    X     |  X       | X         |
| Multiple Table Join     |     X    |         |     X    |   X      |    X     |         |         |         |         |          |
| Subquery                |         |         |         |         |         |         |     X    |   X      |    X     |    X      |
| Correlated Subquery     |         |         |         |         |         |         |    X     |         |         |          |

1. Write a query to find the names, positions, batting averages, bowling averages, and membership types of cricket players whose batting averages are greater than 65. Order the Results in descending order.

<img width="522" alt="Query1 " src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/1333ea18-917b-4416-92b1-6a4b7b40016a">
<img width="726" alt="Query1 Results" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/0ff3e7a7-d7cd-4cb2-bc0e-d0141a609643">

Query 1 retrieves information about players along with their membership type and if they have a batting average greater than 65. It helps in understanding the performance of players who are also members of the organization.

2. Write a query that can calculate the total expenses incurred in the first half of the year 2024 and provide the result.

<img width="518" alt="Query 2" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/d614cbce-4999-477a-bb8f-78b5000f2240">
<img width="604" alt="Query2 Results" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/62d6c4ed-75ae-4e5c-aa1f-aeb1580081cd">

Query 2 calculates the total expenses incurred between January 1, 2024, and May 31, 2024, from the financial management. It filters the data based on the transaction type being an expense and then uses the SUM() function to calculate the total amount. This is beneficial because it helps the club determine how much money was spent in the first half of the year and any updates they may need to make to their budget for the second half of the year.

3. Write a query that showcases information such as name, position, and batting average of Bowler(position), Alice Smith.
   
<img width="557" alt="Query3" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/263d65b0-b34a-4c34-8dfc-2169444a38c4">
<img width="523" alt="Query3 Results" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/fde579fc-63ed-48b0-8b35-6c2c2d1cb812">

Query 3 joins the MembershipManagement table and the playerProfiles table based on the memberID in the MembershipManagement table and the PlayerID in the playerProfiles table. As a result, it retrieves the name (Name), position (positionPlayed), and batting average of specific players.

4. Write a query to find the name of the coach of each team who has qualifications that are in Level 3.

    <img width="444" alt="Query4" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/39c46a7d-384e-4b39-85eb-8a458e2b6fa4">
<img width="506" alt="Query4 Results" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/3d9cdde3-75cb-48ed-9938-e76904eec0f0">

Query 4 joins the CoachingandDevelopment table with the teamManagement table so that it can retrieve the Coach and match them to their team. It also refines the retrieval of data to only coaches that have a qualification level of 3.

5. Formulate an SQL query to calculate the total number of matches played and the average batting performance for each player?
<img width="807" alt="Query5" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/1b7da8fb-caca-40bb-886a-76390e591f15">  
<img width="370" alt="Query5 Results" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/ee55d48c-5ab7-4d6c-a1ad-7962a09485b6">

Query 5 calculates the total number of matches played and the average batting average for each player. Evaluating player performance and optimizing team composition are essential for this information. Understanding players' participation and performance metrics can help adjust training programs or make strategic decisions.

6. List the Number of new members that joined in February 2024.

<img width="433" alt="Query6" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/99d85cb2-1804-46f4-871d-1888a14c8642">
<img width="270" alt="Query6 Results" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/f306e7a7-15af-4002-9b32-e8809baa2b75">

Query 6 calculates the number of new members who have joined in the Feb 2024. It's used to assess the organization's growth trend and the effectiveness of efforts to attract new members. Analyzing membership trends can help adjust marketing strategies.

7. Write a Query that lists the players with a batting average above the overall average batting average of all players.
   
<img width="540" alt="Query7" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/d062c29c-d663-4bfe-a212-6e3245b64819">
<img width="512" alt="Query7 Results" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/848bb93d-9add-488b-ba73-651f68d64424">

Query 7 returns a list of players whose batting average is above the average. It helps in identifying key players and improving the overall performance of the squad. Opportunities can be given to high-performing players or considered for incentives.

8. Write a query to calculate and display the percentage change in revenue compared to the previous month.
   
<img width="790" alt="Query8" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/54032d39-c9d5-4c58-9845-84c03aeee941">
<img width="523" alt="Query8 Results" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/a27def8f-b0b3-4e86-9bd0-9985ec9fc4d5">

Query 8 calculates the percentage change in revenue for the current month compared to the previous month. Monitoring financial status and evaluating the effectiveness of revenue-generating strategies. Tracking revenue changes can inform actions to maintain the organization's financial health.

9. Write an SQL script that retrieves a comprehensive list of players who have participated in every single match throughout the tournament.
    
<img width="942" alt="Query9" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/e5f68d29-d282-4426-a130-48edd0633280">
<img width="987" alt="Query9 Results" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/1f2e409d-c350-4b50-b615-06c627ac88aa">

Query 9 returns a list of players who have participated in all matches. It aids in identifying key players for the team and managing player appearances. Incentives or additional training could be considered for key performing players.

10. Write an SQL query that calculates the average batting and bowling averages for cricket players and also counts the number of players whose batting average is higher than the average batting average or whose bowling average is lower than the average bowling average

<img width="604" alt="Query10" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/3ff6c526-b983-4064-b10f-64eeb0bd92fd">
<img width="720" alt="Query10 Results" src="https://github.com/rjo82443/Cricket_Group4/assets/163200089/3a517980-0bcf-40e7-948b-5795c378ce6b">

Query 10 calculates the average batting and bowling averages and counts players exceeding these averages. Analyzing player performances to identify strengths and weaknesses can help develop personalized training programs and incorporate high performers into team strategies. The provided query uses three independent subqueries to calculate the average batting average, the average bowling average, and the number of players who have performed above these averages, respectively. This approach is a commonly used pattern when you need to utilize the results of aggregate functions in conjunction with other conditions.


## Database information:

