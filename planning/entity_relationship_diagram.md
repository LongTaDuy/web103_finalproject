# Entity Relationship Diagram

Reference the Creating an Entity Relationship Diagram final project guide in the course portal for more information about how to complete this deliverable.

## Create the List of Tables

- `quizzes`
- `questions`
- `choices`
- `quiz_attempts`
- `answers`

## Add the Entity Relationship Diagram

[👉🏾👉🏾👉🏾 Include an image or images of the diagram below. You may also wish to use the following markdown syntax to outline each table, as per your preference.]

---

## Table Definitions

### `quizzes`

| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | Primary key |
| title | text | Title of the quiz |
| description | text | Brief description of the quiz |
| category | text | Quiz category (Science, History, etc.) |
| quiz_type | text | Type of quiz (Knowledge or Personality) |
| creator_name | text | Name of the quiz creator |
| created_at | timestamp | Date the quiz was created |

---

### `questions`

| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | Primary key |
| quiz_id | integer | Foreign key referencing `quizzes.id` |
| question_text | text | Quiz question |
| question_order | integer | Order in which the question appears |

---

### `choices`

| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | Primary key |
| question_id | integer | Foreign key referencing `questions.id` |
| choice_text | text | Answer choice |
| is_correct | boolean | Indicates the correct answer for knowledge quizzes |
| personality_type | text | Personality result associated with the answer (used for personality quizzes) |

---

### `quiz_attempts`

| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | Primary key |
| quiz_id | integer | Foreign key referencing `quizzes.id` |
| username | text | Name of the user taking the quiz |
| score | integer | Final score for knowledge quizzes |
| personality_result | text | Final personality result (if applicable) |
| created_at | timestamp | Date and time the quiz was completed |

---

### `answers`

| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | Primary key |
| attempt_id | integer | Foreign key referencing `quiz_attempts.id` |
| question_id | integer | Foreign key referencing `questions.id` |
| choice_id | integer | Foreign key referencing `choices.id` |

---

### Database Relationships

- One **quiz** can have many **questions**.
- One **question** can have many **choices**.
- One **quiz** can have many **quiz attempts**.
- One **quiz attempt** can contain many **answers**.
- Each **answer** references one **question** and one selected **choice**.
