# Med64 — GitHub Central Question Bank

## What this version does
- No login
- No Supabase
- No database
- Questions are centrally hosted in the GitHub repository
- `questions/index.json` controls which question files are loaded
- All users get the same GitHub question bank
- Progress, accuracy and mistakes are stored separately in each user's browser
- Progress is displayed Overall -> Section -> Category
- Custom exams, section/category filters, timer, auto-submit, results review and mistakes practice
- JSON upload/preview/template tools
- Question Bank search

## Repository structure

    index.html
    questions/
      index.json
      pharmacology.json
      cardiology.json

You can add files such as `pathology.json` and then add the filename to `questions/index.json`.

## Question format

    {
      "id": "pharma-001",
      "section": "Pharmacology",
      "category": "Autonomic Drugs",
      "question": "Question text",
      "options": ["A", "B", "C", "D"],
      "correctIndex": 0,
      "explanation": "Explanation"
    }

IDs MUST be unique across the entire repository. Do not reuse `q1`, `q2` in different files.

## Updating questions for everyone

1. Open the GitHub repository.
2. Open `questions/`.
3. Upload/edit the JSON file.
4. If adding a new file, add its filename to `questions/index.json`.
5. Commit the changes.
6. Open the website and click **Refresh from GitHub**.

The website never contains a GitHub access token. This is intentional: putting a write token in browser JavaScript would expose the repository.

## Progress limitation

Progress is local to each browser/device because there is no login or database. Clearing browser storage removes that device's progress. GitHub updates do not erase existing progress as long as question IDs remain stable.

## Important exam-security limitation

Because this is a no-login, browser-based exam, the answer key is delivered to the browser and a technically advanced user can inspect it. This version is designed for study/practice rather than high-security proctored examinations.


## Exam answer display
The exam customization screen lets you choose:
- **Show answer immediately after selection** — the answer is checked immediately, the correct answer and explanation are shown, and the options are locked.
- **Show answers after finishing** — the selected answer is highlighted, but correctness is not revealed until the exam is submitted.

Each question stores only one answer. In finish mode, selecting another option replaces the previous selection.
