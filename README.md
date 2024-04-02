# Group 4 MIST 4610 Group project 1

## Team Name: 
20244 Group 4

## Team Members:

1. Ryan Overbeck
2. Minwoo Park
3. Brooke Carlisle
4. Mathias Flanagan
5. Connor Walker

## Problem Description:
Pretend you are the owner/operator of a Cricket club needing to build a relational database. You hired some students from the MIST 4610 class at the University of Georgia to create the database for you. They need to know more about your organization to identify which entities, attributes, and relationships are important for you. Start by describing your business as a real client.

## Data Model

Explanation of data model: 

Our model is structured around a hypothetical Cricket Club, where various entities work in tandem to facilitate smooth club operations and player management. At the core of our model lies the Membership Management entity, which encapsulates both the club's members (players) and the operational aspects essential for running a club, such as financial transactions and event management. The Membership Management table utilizes the unique MemberID as its primary key, establishing a one-to-many relationship with Financial Management through the foreign key TransactionID, reflecting the diverse financial interactions members have with the club.

Moving forward, the relationship between Membership Management and Player Profiles is characterized by a one-to-one association, emphasizing the direct link between club membership and player profiles. This direct connection allows for seamless integration of member information with player data.

Transitioning to Player Profiles, we encounter a many-to-many relationship with Team Management, illustrating the dynamic interaction between players and teams within the club. This relationship gives rise to the associative entity known as Roster, which delineates the composition of players within each team, utilizing the TeamID and PlayerID as foreign keys. Furthermore, Team Management establishes a one-to-one relationship with Coaching and Development, signifying the assignment of a single head coach to each team. Additionally, the Coaching and Development entity features a one-to-one recursive relationship, representing the presence of assistant coaches within the coaching staff hierarchy.

Expanding our perspective, the Event and Tournament Management entity emerges as a pivotal component, overseeing the organization of cricket events and tournaments. Due to the multifaceted nature of event planning, Event and Tournament Management features several one-to-many relationships with other entities. For instance, the association with Team Management allows for the inclusion of participating teams via the TeamID foreign key, while the Umpire Management table facilitates the identification of umpires involved in specific events through their unique UmpireID. Similarly, the involvement of sponsors in events is tracked via a one-to-many relationship with the Sponsorship and Partnership table, ensuring comprehensive sponsorship management. Furthermore, newsletters pertinent to events are integrated into the Event and Tournament Management table through a one-to-many relationship, enabling efficient communication with stakeholders. Lastly, the inclusion of facilities and equipment utilized in events is facilitated by a one-to-many relationship with the Facility and Equipment Management table, which further links to the Volunteer and Staff Management table to list staff members associated with event venues.

In essence, the interconnected relationships within our data model reflect the intricate web of interactions within a cricket club, facilitating seamless management of members, players, teams, events, and resources. Each relationship serves a specific purpose, contributing to the holistic functioning of the club and ensuring efficient coordination across various operational domains.

![image](https://github.com/rjo82443/Cricket_Group4/assets/163200122/53f061a2-fef2-4a3e-9c55-b82dcd8a4349)



## Data Dictionary:
### Membership Management

| Column Name        | Description                            | Data Type | Size | Format         | Key? |
|--------------------|----------------------------------------|-----------|------|----------------|------|
| MemberID           | Unique identifier for members          | INT       |      |                | PK   |
| Name               | Name of the member                     | VARCHAR   | 45   | Last, First    |      |
| DateOfBirth        | Date of birth of the member            | DATE      |      | MM/DD/YYYY     |      |
| ContactInformation | Contact details of the member          | VARCHAR   | 120  | (XXX) - XXX-XXX |      |
| MembershipType     | Type of Membership                    | VARCHAR   | 45   |                |      |
| JoiningDate        | Date when the member joined            | DATE      |      | MM/DD/YYYY     |      |
| PaymentStatus      | Status of membership payment           | VARCHAR   | 45   |                |      |
| TransactionID      | Unique identifier for transactions     | INT       |      |                | FK (ref. Financial Management) |

### Player Profiles

| Column Name        | Description                            | Data Type | Size | Format         | Key? |
|--------------------|----------------------------------------|-----------|------|----------------|------|
| PlayerID           | Unique identifier for players          | INT       |      |                | PK   |
| Name               | Name of the player                     | VARCHAR   | 45   | Last, First    |      |
| DateofBirth        | Date of birth of the player            | DATE      |      | MM/DD/YYYY     |      |
| ContactInformation | Contact details of the player          | VARCHAR   | 120  | (XXX)-XXX-XXX |      |
| PositionPlayed     | Position played by the player          | VARCHAR   | 45   |                |      |
| BattingAverage     | The batting average of the player      | DECIMAL   | (1,3)| X.XXX          |      |
| BowlingAverage     | Bowling average of the player          | DECIMAL   | (1,3)| X.XXX          |      |
| MatchesPlayed      | Number of matches played               | INT       |      |                |      |
| MemberID           | Unique identifier for members          | INT       |      |                | FK (ref. Membership Management) |

### Team Management

| Column Name    | Description                          | Data Type | Size | Format   | Key? |
|----------------|--------------------------------------|-----------|------|----------|------|
| TeamID         | Unique identifier for teams          | INT       |      |          | PK   |
| TeamName       | Name of the team                     | VARCHAR   | 45   |          |      |
| AgeGroup       | The age group of the team            | VARCHAR   | 45   |          |      |
| HomeGround     | The home ground of the team          | INT       | 45   |          |      |
| MatchSchedule  | Schedule of matches                  | VARCHAR   | 500  |          |      |
| Results        | Results of matches                   | VARCHAR   | 500  |          |      |
| CoachID        | Identifier of the coach              | INT       |      |          | FK (ref. coaching and development) |

### Facility and Equipment

| Column Name          | Description                          | Data Type | Size | Format        | Key? |
|----------------------|--------------------------------------|-----------|------|---------------|------|
| FacilityID           | Unique identifier for facilities     | INT       |      |               | PK   |
| FacilityName         | Name of the facility                  | VARCHAR   | 45   |               |      |
| Location             | Location of the facility             | VARCHAR   | 45   |               |      |
| EquipmentID          | Identifier of the equipment          | INT       |      |               | PK   |
| AvailabilitySchedule | Schedule of availability             | VARCHAR   | 500  |               |      |
| MaintenanceStatus    | Status of maintenance                | VARCHAR   | 500  |               |      |
| StaffID              | Unique identifier for volunteers and staff | INT       |      |               | FK (ref. volunteer and staff management) |

### Event and Tournament Management

| Column Name        | Description                          | Data Type | Size | Format        | Key? |
|--------------------|--------------------------------------|-----------|------|---------------|------|
| EventID            | Unique identifier for events         | INT       |      |               | PK   |
| EventName          | Name of the event                    | VARCHAR   | 45   |               |      |
| Date               | Date of the event                    | DATE      |      | MM/DD/YYYY    |      |
| Venue              | Venue of the event                   | VARCHAR   | 45   |               |      |
| ParticipatingTeams | Teams participating in the event     | VARCHAR   | 500  |               |      |
| Results            | Results of the event                 | VARCHAR   | 45   |               |      |
| Awards             | Awards given in the event            | VARCHAR   | 45   |               |      |
| TeamID             | Unique identifier for teams          | INT       |      |               | FK(ref.Team Management) |
| FacilityID         | Unique identifier for Facility       | INT       |      |               | FK(ref.Facility and Equipment Management) |
| UmpireID           | Unique identifier for Umpire         | INT       |      |               | FK(ref. Umpire Management) |
| NewsletterID       | Unique identifier for newsletter     | INT       |      |               | FK(ref. Communication and Marketing) |
| SponsorID          | Unique identifier for sponsor        | INT       |      |               | FK(ref.Sponsorship and Partnerships) |

### Coaching and Development

| Column Name              | Description                          | Data Type | Size | Format       | Key? |
|--------------------------|--------------------------------------|-----------|------|--------------|------|
| CoachID                  | Unique identifier for coaches        | INT       |      |              | PK   |
| CoachName                | Name of the coach                    | VARCHAR   | 45   | Last, First  |      |
| Qualifications           | Qualifications of the coach          | VARCHAR   | 45   |              |      |
| TrainingSchedule         | Schedule of training                 | VARCHAR   | 500  | Week/ Time /Date |   |
| PlayerDevelopmentProgram | Program for player development       | VARCHAR   | 45   |              |      |
| PerformanceAssessments   | Assessments of performance           | VARCHAR   | 45   |              |      |
| Assistant Coach          | ID of Assistant Coach                | INT       |      |              | FK(ref Coaching and Development- Recursive Relationship) |

### Financial Management

| Column Name   | Description                          | Data Type | Size | Format      | Key? |
|---------------|--------------------------------------|-----------|------|-------------|------|
| TransactionID | Unique identifier for transactions  | INT       |      |             | PK   |
| Date          | Date of the transaction              | DATE      |      | MM/DD/YYYY  |      |
| Type          | Type of transaction (Income/Expense) | VARCHAR   | 45   |             |      |
| Amount        | Amount of the transaction            | DECIMAL   | (8,2)| XX.XX       |      |
| Description   | Description of the transaction       | VARCHAR   | 500  |             |      |
| BudgetCategories | Categories in the budget          | VARCHAR   | 45   |             |      |

### Communication and Marketing

| Column Name       | Description                          | Data Type | Size | Format      | Key? |
|-------------------|--------------------------------------|-----------|------|-------------|------|
| NewsletterID      | Unique identifier for newsletters    | INT       |      |             | PK   |
| Date              | Date of the newsletter               | DATE      |      | MM/DD/YYYY  |      |
| Content           | Content of the newsletter            | VARCHAR   | 450  |             |      |
| Recipients        | Recipients of the newsletter         | VARCHAR   | 450  |             |      |
| SocialMediaPosts  | Posts on social media                | VARCHAR   | 45   |             |      |
| EventParticipation | Participation in community events  | VARCHAR   | 45   |             |      |

### Volunteer and Staff Management

| Column Name         | Description                          | Data Type | Size | Format      | Key? |
|---------------------|--------------------------------------|-----------|------|-------------|------|
| StaffID             | Unique identifier for staff          | INT       |      |             | PK   |
| VolunteerID         | Identifier of the volunteer          | INT       |      |             | PK   |
| Name                | Name of the staff                    | VARCHAR   | 45   | Last, First |      |
| Role                | Role of the staff                    | VARCHAR   | 45   |             |      |
| ContactInformation  | Contact details of the staff         | VARCHAR   | 120  |             |      |
| Schedule            | Schedule of the staff                | VARCHAR   | 45   |             |      |

### Umpire Management

| Column Name         | Description                          | Data Type | Size | Format      | Key? |
|---------------------|--------------------------------------|-----------|------|-------------|------|
| UmpireID            | Unique identifier for umpires        | INT       |      |             | PK   |
| Name                | Name of the umpire                   | VARCHAR   | 45   | Last, First |      |
| Certification       | Certification status of the umpire   | VARCHAR   | 45   |             |      |
| ContactInformation  | Contact details of the umpire        | VARCHAR   | 120  |             |      |
| Availability        | Availability of the umpire           | VARCHAR   | 450  |             |      |
| PerformanceReviews  | Reviews of umpire performance        | VARCHAR   | 450  |             |      |

### Sponsorship and Partnership

| Column Name         | Description                          | Data Type | Size | Format      | Key? |
|---------------------|--------------------------------------|-----------|------|-------------|------|
| SponsorID           | Unique identifier for sponsors       | INT       |      |             | PK   |
| Name                | Name of the sponsor                  | VARCHAR   | 45   |             |      |
| Type                | Type of sponsor (Sponsor/Partner)    | INT       | 45   |             |      |
| AgreementDetails    | Details of the sponsorship agreement | INT       | 45   |             |      |
| FinancialContributions | Contributions made by the sponsor  | DECIMAL   | (8,2)| XXX.XX      |      |
| PromotionalActivities | Activities undertaken by sponsor   | VARCHAR   | 45   |             |      |

### Fan Engagement

| Column Name          | Description                          | Data Type | Size | Format      | Key? |
|----------------------|--------------------------------------|-----------|------|-------------|------|
| FanID                | Unique identifier for fans           | INT       |      |             | PK   |
| Name                 | Name of the fan                      | VARCHAR   | 45   | Last,First  |      |
| ContactInformation   | Contact details of the fan           | VARCHAR   | 120  |             |      |
| AttendanceHistory    | History of fan attendance            | VARCHAR   | 450  |             |      |
| MerchandisePurchases | Amount of money spent on merchandise | DECIMAL   | (6,2)| XX.XX       |      |
| LoyaltyPoints        | Number of loyalty points earned      | INT       |      |             |      |
| TeamID               | Identifier of team-specific fan supports | INT   |      |             | FK(ref. Team Management) |

### Player History - Associative Entity

| Column Name | Description                             | Data Type | Size | Format      | Key? |
|-------------|-----------------------------------------|-----------|------|-------------|------|
| PlayerID    | Unique identifier for players          | INT       |      |             | FK (ref.Player Profile) |
| EventID     | Unique identifier for event/tournament  | INT       |      |             | FK (ref. Event and Members) |

### Roster - Associative Entity

| Column Name | Description                          | Data Type | Size | Format      | Key? |
|-------------|--------------------------------------|-----------|------|-------------|------|
| PlayerID    | Unique identifier for players        | INT       |      |             | FK (ref.Player Profiles) |
| TeamID      | Unique identifier for Teams          | INT       |      |             | FK (ref. Team Management) |


## Queries:
| Query Identification    | Query 1 | Query 2 | Query 3 | Query 4 | Query 5 | Query 6 | Query 7 | Query 8 | Query 9 | Query 10 |
|-------------------------|---------|---------|---------|---------|---------|---------|---------|---------|---------|----------|
| Simple                  |         |         |         |         |         |         |         |         |         |          |
| Complex                 |         |         |         |         |         |         |         |         |         |          |
| Multiple Table Join     |         |         |         |         |         |         |         |         |         |          |
| Subquery                |         |         |         |         |         |         |         |         |         |          |
| Correlated Subquery     |         |         |         |         |         |         |         |         |         |          |




## Database information:

