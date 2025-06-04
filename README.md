# XJTLU-SURF-0259-SeePhy

<p align="center">
  <a href="README_zh-CN.md">简体中文</a>
  ｜
  English
</p>

## Table of Contents
1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Git Basics for Non-technical Users](#git-basics-for-non-technical-users)
4. [Commit Message Guidelines](#commit-message-guidelines)
5. [Project Structure](#project-structure)
6. [Contributing](#contributing)


## Introduction
Enhancing Large Language Model Performance for Complex Physics Reasoning with Diagrams and Expressions
Challenge Website: [here](https://www.codabench.org/competitions/7925/)


## Getting Started
### Prerequisites
- Install [Git](https://git-scm.com/downloads) on your computer.
- Create a [GitHub](https://github.com/) account if you don’t have one.

### How to Download the Project (Clone)
1. Open GitHub and navigate to our project repository.
2. Click the green "Code" button and copy the HTTPS URL.
3. Open Git Bash (Windows) or Terminal (Mac/Linux).
4. Run the following command:
   ```bash
   git clone <paste-the-copied-URL-here>
   ```
5. Navigate into the project folder:
   ```bash
   cd project-name
   ```


## Git Basics for Non-technical Users
### How to Submit Your Work
1. **Update Your Local Copy** (always do this before starting work):
   ```bash
   git pull origin main
   ```
   - This fetches the latest changes from GitHub.

2. **Create a New Branch** (replace `your-feature-name` with a short description of your work):
   ```bash
   git checkout -b your-feature-name
   ```
   - Branches keep your work separate from others'.

3. **Make Changes** to the files using your preferred editor (e.g., Notepad, VS Code).

4. **Check Status** (see which files you’ve changed):
   ```bash
   git status
   ```

5. **Add Your Changes** (replace `filename` with the actual file name):
   ```bash
   git add filename
   ```
   - Or add all changed files at once:
     ```bash
     git add .
     ```

6. **Commit Your Changes** (write a clear message using the prefix guidelines below):
   ```bash
   git commit -m "Prefix: Brief description of your changes"
   ```

7. **Push to GitHub** (upload your branch to GitHub):
   ```bash
   git push origin your-feature-name
   ```

8. **Create a Pull Request (PR)**
   - Go to the GitHub repository.
   - Click "Compare & pull request" for your branch.
   - Add a description and submit the PR.


## Commit Message Guidelines
To keep our project organized, all commit messages must follow this format:

```
Prefix: Short description of the changes (50 characters or less)
```

### Required Prefixes
- **`[ADD]`** : When adding new files or features.  
  Example: `[ADD] Add README.md for project documentation`

- **`[UPDATE]`** : When modifying existing files.  
  Example: `[UPDATE] Update installation instructions in README`

- **`[FIX]`** : When fixing errors or bugs.  
  Example: `[FIX] Fix typo in main.js`

- **`[REMOVE]`** : When deleting files or features.  
  Example: `[REMOVE] Remove outdated test files`

- **`[DOCS]`** : When updating documentation (e.g., README, comments).  
  Example: `[DOCS] Add API documentation for new endpoint`

- **`[STYLE]`** : When changing code style (indentation, formatting).  
  Example: `[STYLE] Format code with Prettier`


## Project Structure  
Here’s a breakdown of the main files and folders in our project and what they contain:  

```  
project-root/  
├── images/            # Stores images corresponding to 2000 physics problems  
├── README.md          # This documentation file (available in both Chinese and English)  
├── dev.json           # Data for fine - tuning. Contains 200 dev data samples with answers.  
├── example.py         # (If applicable) Sample Python script for demonstration  
├── mini.json          # Raw problem data with 200 questions  
├── public_prediction_example.json # Expected format for final prediction submissions  
└── total.json         # Raw problem data with 2000 questions  
```  

### File Details  

#### 1. `images/` Folder  
- Stores **images corresponding to 2000 physics problems**. These visuals are crucial for understanding and solving the problems, especially those with diagrams like circuit diagrams or coordinate systems.  


#### 2. `dev.json`  
- **Purpose**: Used as the basis for fine - tuning our models.  
- **Content**: Contains 200 dev data samples with answers. The official description is: *"we have provided 200 dev data samples with answers"*.  
- **Format**:  
  ```json  
  {  
      "index": None,  
      "question": "",           # Text of the physics question  
      "subject": "",            # Type of question (e.g., CM for classical mechanics, OPT for optics)  
      "image_path": [           # List of image paths related to the question  
          
      ],  
      "img_category": "",       # Type of diagram (e.g., circuit diagrams, coordinate systems)  
      "vision_relevance": "",   # Indicates if the image has necessary info to solve the problem  
      "language": "",           # Language of the question (English/Chinese)  
      "level": None,            # Knowledge level required  
      "sig_figs": "",           # Number of significant figures in the answer  
      "caption": "",            # Textual description of images  
      "reasoning": "",          # Reasoning steps for solving the problem  
      "answer": ""              # Correct answer  
  }  
  ```  


#### 3. `mini.json` and `total.json`  
- **Purpose**: Store raw physics problem data.  
  - `mini.json`: Contains data for **200 questions**.  
  - `total.json`: Contains data for **2000 questions** (the full dataset).  
- **Format**:  
  ```json  
  {  
      "index": None,  
      "question": "",           # Text of the physics question  
      "subject": "",            # Type of question (e.g., CM, OPT)  
      "image_path": [           # List of image paths related to the question  
          
      ],  
      "img_category": "",       # Type of diagram (e.g., circuit diagrams)  
      "vision_relevance": "",   # Indicates if the image has necessary info to solve the problem  
      "language": "",           # Language of the question (English/Chinese)  
      "level": None,            # Knowledge level required  
      "sig_figs": "",           # Number of significant figures in the answer  
      "caption": ""             # Textual description of images  
  }  
  ```  


#### 4. `public_prediction_example.json`  
- **Purpose**: Serves as a template for submitting final predictions. This is the format we expect when you submit your solved problems.  
- **Format**:  
  ```json  
  {  
      "question": "",           # Text of the physics question  
      "subject": "",            # Type of question (e.g., CM, OPT)  
      "image_path": [           # List of image paths related to the question  
          
      ],  
      "sig_figs": "",           # Number of significant figures in the answer  
      "level": None,            # Knowledge level required  
      "language": "",           # Language of the question (English/Chinese)  
      "index": None,            # Index of the question  
      "img_category": "",       # Type of diagram (e.g., circuit diagrams)  
      "vision_relevance": "",   # Indicates if the image has necessary info to solve the problem  
      "caption": "",            # Textual description of images  
      "prediction": "<think>\n<think>\n\n<think>\n<think>"  # Your predicted solution (follow the think - and - answer block structure)  
  }  
  ```  

#### 5. Prediction Comparison Rules  
As per the organizer’s explanation (refer to the discussion in the project communication):  
- We primarily compare the **think - and - answer blocks** in predictions.  
- If a result does not contain such a block, the entire response will be compared instead.  

## Contributing
1. Always work on your own branch (never directly on `main`).
2. Follow the commit message prefix guidelines.
3. Test your changes before submitting a PR.
4. If you’re unsure, ask for help in the team chat!
