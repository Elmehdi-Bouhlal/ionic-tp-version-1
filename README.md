# Repository Setup for Ionic Project with Yarn and Angular

name: Ionic Project CI/CD

on:
  push:
    branches:
      - main # Trigger CI/CD when changes are pushed to the main branch

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    # Step 1: Checkout the code from the repository
    - name: Checkout code
      uses: actions/checkout@v3

    # Step 2: Set up Node.js (Ensure the required version is available)
    - name: Set up Node.js
      uses: actions/setup-node@v3
      with:
        node-version: '16' # Specify the required Node.js version here

    # Step 3: Install dependencies using Yarn
    - name: Install dependencies
      run: |
        yarn install

    # Step 4: Build the Ionic project (Ensure Angular build is included)
    - name: Build the project
      run: |
        yarn build

    # Step 5: Test the project (optional)
    - name: Run tests
      run: |
        yarn test # This will run unit tests if defined in the Angular project

    # Step 6: Push changes or deploy (Optional step based on your setup)
    - name: Deploy or Push changes
      run: |
        echo "Deploy or push changes to production"
        # Replace with your deployment or push logic if applicable

# Instructions for Pulling or Cloning the Repository Manually
manual_steps:
  - Cloning the Repository:
      description: |
        To clone the repository to your local machine, run the following command:
        ```
        git clone https://github.com/your-username/your-repository.git
        ```
        Then navigate into the project directory:
        ```
        cd your-repository
        ```

  - Installing Dependencies:
      description: |
        After cloning the repository, use Yarn to install all project dependencies:
        ```
        yarn install
        ```

  - Running the Development Server:
      description: |
        Once dependencies are installed, you can run the project locally:
        ```
        yarn start
        ```
        This will start the Ionic development server and open the app in your default browser.

  - Pulling the Latest Changes:
      description: |
        To pull the latest changes from the repository, use the following command:
        ```
        git pull origin main
        ```

  - Pushing Changes:
      description: |
        After making changes locally, commit them and push them back to the repository:
        ```
        git add .
        git commit -m "Your commit message"
        git push origin main
        ```
