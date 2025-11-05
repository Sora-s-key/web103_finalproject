# Entity Relationship Diagram

Reference the Creating an Entity Relationship Diagram final project guide in the course portal for more information about how to complete this deliverable.

## Create the List of Tables

[👉🏾👉🏾👉🏾 List each table in your diagram]

1. Users
2. Workouts
3. Exercises
4. Goals
5. Milestones
6. Achievements
7. User Achievements

## Add the Entity Relationship Diagram

[👉🏾👉🏾👉🏾 Include an image or images of the diagram below. You may also wish to use the following markdown syntax to outline each table, as per your preference.]

![ERD Diagram](./FitTrack.png)

### users
| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | primary key, auto-increment |
| username | varchar | user's username |
| email | varchar | user's email address |
| password_hash | varchar | hashed password for security |
| role | varchar | user role (default: 'athlete') |
| created_at | timestamp | account creation timestamp (default: now()) |

### workouts
| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | primary key, auto-increment |
| user_id | integer | foreign key referencing users.id |
| workout_date | date | date of the workout |
| duration_minutes | integer | workout duration in minutes |
| notes | text | optional notes about the workout |
| created_at | timestamp | record creation timestamp (default: now()) |

### exercises
| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | primary key, auto-increment |
| workout_id | integer | foreign key referencing workouts.id |
| exercise_name | varchar | name of the exercise |
| sets | integer | number of sets performed |
| reps | integer | number of reps per set |
| weight_lbs | decimal | weight used in pounds |

### goals
| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | primary key, auto-increment |
| user_id | integer | foreign key referencing users.id |
| goal_type | varchar | type of goal (e.g., distance, weight) |
| target_value | decimal | target value to achieve |
| current_value | decimal | current progress value (default: 0) |
| description | text | description of the goal |
| deadline | date | goal deadline date |
| is_completed | boolean | completion status (default: false) |
| created_at | timestamp | goal creation timestamp (default: now()) |

### milestones
| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | primary key, auto-increment |
| goal_id | integer | foreign key referencing goals.id |
| percentage | integer | milestone percentage (25, 50, 75, 100) |
| target_value | decimal | calculated target value for this milestone |
| is_completed | boolean | completion status (default: false) |
| completed_at | timestamp | timestamp when milestone was completed |

### achievements
| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | primary key, auto-increment |
| name | varchar | name of the achievement |
| description | text | description of how to earn it |
| badge_icon_url | varchar | URL to badge icon image |
| criteria_type | varchar | type of criteria (e.g., streak, workout_count) |
| criteria_value | integer | value needed to unlock achievement |

### user_achievements
| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | primary key, auto-increment |
| user_id | integer | foreign key referencing users.id |
| achievement_id | integer | foreign key referencing achievements.id |
| earned_at | timestamp | timestamp when achievement was earned (default: now()) |
