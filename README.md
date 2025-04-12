# 🚀 How to Publish React Vite with Github Pages
This repo serves as a guide on how to publish a React Vite application using GitHub Pages, common issues, and their solutions.
## Steps to Publish
1.  **Add path to `vite.config.js`**: ✨
    - Add the `base` path to ensure that the app is served from the correct URL. 
    ```js
    import { defineConfig } from 'vite'
    import react from '@vitejs/plugin-react'
    import tailwindcss from '@tailwindcss/vite'

    // https://vite.dev/config/
    export default defineConfig({
    plugins: [react(), tailwindcss()],
    base: '/REPO_NAME/',       
    })

    ```
 2. **Add `homepage` to `package.json`**: ✨
    - Add the `homepage` field to your `package.json` file. This is important for React Router to work correctly.
    ```json
    {
      "name": "REPO_NAME",
      "version": "0.0.0",
      "private": true,
      "homepage": "https://USERNAME.github.io/REPO_NAME/",
      ...
    }
    ```

3. **Add `predeploy` and `deploy` scripts to `package.json`**: ✨
    - Add the `predeploy` and `deploy` scripts to your `package.json` file. This will allow you to deploy your app using the command line.
    ```json
    {
      ...
      "scripts": {
        "predeploy": "npm run build",
        "deploy": "gh-pages -d dist"
      }
    }

    <!-- Example-->
    {
    "name": "zeldawiki",
    "homepage": "https://nguyencatnguyen.github.io/ZeldaWIki/",
    "private": true,
    "version": "0.0.0",
    "type": "module",
    "scripts": {
        "dev": "vite",
        "build": "vite build",
        "lint": "eslint .",
        "preview": "vite preview",
        "predeploy": "npm run build",
        "deploy": "gh-pages -d dist"
    }
    ```

    - `build` creates a production build of your app in the `dist` folder.
    - `gh-pages -d dist` deploys the contents of the `dist` folder to the `gh-pages` branch of your repository.

4. **Build and Preview the web** ✨
    - Run the following command to build and preview your app:
    ```bash
    npm run build
    npm run preview
    ```
    - This will create a `dist` folder with the production build of your app. You can preview it by running `npm run preview`.
    - Check path for any error

5. **Deploy to GitHub Pages**: ✨
    - Run the following command to deploy your app to GitHub Pages:
    ```bash
    npm run deploy
    ```
    - This will create a `gh-pages` branch in your repository and push the contents of the `dist` folder to it.

6. **Enable GitHub Pages**: ✨
    - Go to your GitHub repository settings.
    - Scroll down to the "GitHub Pages" section.
    - Select the `gh-pages` branch as the source and save.
    - Your app should now be live at `https://USERNAME.github.io/REPO_NAME/`.

## ❗️Common Issues
### 1. Image path issues
- **Pulic Folder**
    - If you are using images from the `public` folder, make sure to use the correct path. Always add the `./` prefix to the image path.
    - Example:
        ```jsx
        <img src="./logo.png" alt="Logo" />
        ```

- **Assets Folder**
    - If you are using images from the `src/assets` folder, make sure to import them correctly.
    - Example:
        ```jsx
        import logo from './assets/logo.png';
        <img src={logo} alt="Logo" />
        ```