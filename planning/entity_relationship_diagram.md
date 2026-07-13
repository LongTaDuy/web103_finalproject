# Entity Relationship Diagram

Reference the Creating an Entity Relationship Diagram final project guide in the course portal for more information about how to complete this deliverable.

## List of Tables

<!-- [👉🏾👉🏾👉🏾 List each table in your diagram] -->
- `quizzes`: Table of created quizzes
- `questions`: Table of questions created for quizzes

## Entity Relationship Diagram

<!-- [👉🏾👉🏾👉🏾 Include an image or images of the diagram below. You may also wish to use the following markdown syntax to outline each table, as per your preference.] -->

<!-- | Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | primary key |
| name | text | name of the shoe model |
| ... | ... | ... | -->

### `quizzes` Table
| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | primary key |
| title | text | Title of the quiz |
| created_at | timestamp | Date and time the quiz was created |
| image | text | Header image for the quiz |
| num_taken | integer | number of times the quiz has been taken |
| type | enum | Type of quiz ('regular', 'personality') |
| results | text[] | list of possible results for personality quizzes |

### `questions` table

| Column Name | Type | Description |
|-------------|------|-------------|
| id | integer | primary key |
| quiz_id | integer (foreign key) | id of the associated quiz |
| question | text | question |
| choices | answer_choice[] (composite type) | answer choices for personality quiz questions |
| correct_answer | text | correct answer to the question (for regular quizzes only) |

The `choices` column of the `questions` table will make use of a custom composite type to represent the question's answer choices.

```sql
CREATE TYPE answer_choice AS (
    content text,
    result  text
)
```

The `content` field represents the text content of the answer choice that is visible to the user, while `result` is the personality result that the choice is linked to. For example, if an answer choice has the value `('Red', 'ISTJ')`, and this answer choice is chosen by the user, then one point is added to the score for `'ISTJ'`, and the user's result would be the value with the most points. However, if the question is made for a regular quiz, then the `result` field will be `NULL`.
