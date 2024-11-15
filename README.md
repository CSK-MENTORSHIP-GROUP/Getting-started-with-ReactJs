# Getting Started with React.js

This repository provides a beginner-friendly guide for setting up and developing web applications with React.js. Using Vite, a fast build tool, we streamline the React development environment for better performance and ease of use.

## Prerequisites
- [Node.js](https://nodejs.org/) (version 18,19 or 20 recommended to avoid compatibility issues) 
- [npm](https://www.npmjs.com/) or [pnpm](https://pnpm.io/)

## Installation

### Step 1: Create a New Project with Vite
To start, create a new React.js project using Vite.

#### Using npm
```bash
npm create vite@latest my-react-app -- --template react
```
#### Using pnpm
```bash
pnpx create vite@latest my-react-app --template react
```

### Step 2: Install Dependencies
Navigate to the project directory and install the required dependencies.

```bash
cd my-react-app
npm install
```
#### Using pnpm 
```bash
cd my-react-app
pnpm install
```
### Project Structure
The project structure should look like this:

```bash
my-react-app
├── node_modules
├── public
│   ├── favicon.ico
│   ├── index.html
├── src
│   ├── App.css
│   ├── App.js
│   ├── index.css
│   ├── index.js
├── .gitignore
├── package.json
├── README.md
```
### Step 3: Start the Development Server
Run the development server to start building your React application.

#### Using npm
```bash
npm run dev
```
#### Using pnpm
```bash
pnpm run dev
```
The development server should start at `http://localhost:5173`.

## Contributing
Contributions are welcome! Feel free to submit a pull request or open an issue if you have any questions or suggestions.
