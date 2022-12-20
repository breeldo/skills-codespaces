# Develop code using Codespaces and Visual Studio Code!

<!--step0

GitHub offers Codespaces which is a development environment that's hosted in the cloud.

- **Who this is for**: Developers, DevOps Engineers, Engineering Managers, Product managers
- **What you'll learn**: How create Codespaces, push code from a Codespace, select a custom image, and customize a Codespace
- **What you'll build**: Codespaces, devcontainer.json files, Codespace customizations, Codespace personalizations.
- **Prerequisites**: Codespaces enabled. To see how to get a free trial click  [codespace](https://github.com/features/codespaces)
- **Timing**: This course is four steps long and can be completed in under an hour

<summary><h2> How to start this course!</h2></summary>
 
1. Above these instructions, right-click **Use this template** and open the link in a new tab.
   ![Use this template](https://user-images.githubusercontent.com/1221423/169618716-fb17528d-f332-4fc5-a11a-eaa23562665e.png)
2. In the new tab, follow the prompts to create a new repository.
   - For owner, choose your personal account or an organization to host the repository.
   - We recommend creating a public repository—private repositories will use [Actions minutes](https://docs.github.com/en/billing/managing-billing-for-github-actions/about-billing-for-github-actions).
   ![Create a new repository](https://user-images.githubusercontent.com/1221423/169618722-406dc508-add4-4074-83f0-c7a7ad87f6f3.png)
3. After your new repository is created, wait about 20 seconds, then refresh the page. Follow the step-by-step instructions in the new repository's README.

endstep0-->


<details id=1>
<summary><h2>Step 1: Create your first codespace and push code</h2></summary>

_Welcome to "Develop code using Codespaces and Visual Studio Code"! :wave:_

**What's the big deal about using a Github codespace for software development**: A codespace is a development environment that's hosted in the cloud. You can customize your project for GitHub Codespaces by committing Configuration-as-Code files, which creates a repeatable codespace configuration for all users of your project. Each codespace runs on a virtual machine hosted by GitHub. You can choose the type of machine you want to use, depending on the resources you need.

GitHub offers a range of features to help your development team customize a Codespace to reach peak configuration and performance needs. Some features of Codespaces are:

- Create a Codespace from your repository 
- Push code from the Codespace to your repository
- Use VS Code to develop code
- Customize the codespace with custom images
- Manage the Codespace
   
**What is a Codespace**: A Codespace is a development environment that's hosted in the cloud, it is accessible by one click on the homepage from your repository.

### :keyboard: Activity: Start a Codespace.

**We recommend opening another browser tab to work through the following activities so you can keep these instructions open for reference.**

1. Start from the landing page of your repository.
2. Click the `Code` button located in the middle of the page.
3. Click the `Codespaces` tab on the box that pops up.
4. Click the `Create codespaces on main` button.
**Wait about 2 minutes for the codespace to spin itself up. Note, its a VM spinning up in the background**
5. Verify your codespace is is running. The browser should contain a VS code web based editor a a terminal should be present such as the below:
![codespace1](https://user-images.githubusercontent.com/26442605/207355196-71aab43f-35a9-495b-bcfe-bf3773c2f1b3.png)

### :keyboard: Activity: Push code to your repository from the codespace

1. From inside the Codespace in the VS Code explorer window select the `index.html` file.
2. Add the following code inside of the `<html>` tag:
```
<h1>Hello from the codespace!</h1>
```
3. Save the file. Note: The file should autosave.
4. Commit the file changes. From the VS Code terminal enter:
```
git commit -a -m "Adding hello from the codespace!"
```
5. Push the changes back to your repository. From the VS Code terminal etner:
```
git push
```
6. Your code has been pushed to your repository!
7. Switch back to the homepage of your repository and view the `index.html` to verify the new code was pushed to your repository.
	
**Wait about 20 seconds then refresh this page for the next step**
</details>

<details id=2 open>
<summary><h2>Step 2: Add a custom image to your Codespace!</h2></summary>

_Nice work! :tada: You created your first Codespace and pushed codes using VS Code!_

You can configure the dev container for a repository so that codespaces created for that repository give you a tailored development environment, complete with all the tools and runtimes you need to work on a specific project

**What are Development containers?**: Development containers, or dev containers, are Docker containers that are specifically configured to provide a fully featured development environment. Whenever you work in a codespace, you are using a dev container on a virtual machine.

A dev container file is a JSON files that lets you customize the default image that runs your Codespace, VS code settings, run custom code, forward ports and much more!

Let's add a `devcontainer.json` file and add a custom image.
 
### :keyboard: Activity: Add a .devcontainer.json file to customize your Codespace

1. Start from the landing page of your repository.
2. Click `Add file`
3. Click `Create new file`
4. Type or paste the folling in the `Name you file...` prompt
```
.devcontainer/devcontainer.json
```
5. In the body of the `Edit new file` text box add:
```
{
    // Name this configuration
    "name": "Codespace for Skills!",
    //Use base codespace image then pull Valet on postCreateCommand,  
    "image": "mcr.microsoft.com/vscode/devcontainers/universal:latest",
    
    "remoteUser": "codespace",
    "overrideCommand": false
}
```
6. Click Commit changes directly to the main branch.
7. Create a new Codespace by navigating to the landing page of your repository.
8. Click the `Code` button located in the middle of the page.
9. Click the `Codespaces` tab on the box that pops up.
10. Click the `Create codespaces on main` button OR click the `+` sign on the tab. This will create a new Codespace on the main branch.
**Wait about 2 minutes for the codespace to spin itself up. Note, its a VM spinning up in the background**
11. Verify your codespace is is running as you did above.

Note the image being used is the default image provided for Codespaces. It includes runtimes and tools for Python, Node.js, Docker, and more. See the full list here: https://aka.ms/ghcs-default-image but any custom image can be used by your development team that has the required prerequisites installed on their image for more see: [Codespace image](https://aka.ms/configure-codespace) for more details. 
	
**Wait about 20 seconds then refresh this page for the next step**

</details>
<details id=3>
	
<summary><h2>Step 3: Customize your Codespace!</h2></summary>

_Nice work! :tada: You created a Codespace with a custom image!_

You can customize GitHub Codespaces by adding VS code extensions, adding features, setting host requirements, and much more when the Codespace is created.
	
Let's customize some setting in the .devcontainer.json file!

 ### :keyboard: Activity: Add customizations to the devcontainer file

1. Edit the `.devcontainer/devcontainer.json` file.
2. Add the following customizations to the body of the file before the last `}`. 
```
    ,    
    // Add the IDs of extensions you want installed when the container is created.
    "customizations": {
        "vscode": {
            "extensions": [
                "GitHub.copilot"
            ]
        },
        "codespaces": {
            "openFiles": [
                "codespace.md"
            ]
        }
    }
```
3. Click Commit changes directly to the main branch.
4. Create a new Codespace by navigating to the landing page of your repository.
5. Click the `Code` button located in the middle of the page.
6. Click the `Codespaces` tab on the box that pops up.
7. Click the `Create codespaces on main` button OR click the `+` sign on the tab. This will create a new Codespace on the main branch.
**Wait about 2 minutes for the codespace to spin itself up. Note, its a VM spinning up in the background**
8. Verify your codespace is is running as you did above.
9. The `codespace.md` file should show up in the VS code editor.
10. The `copilot` extension should show up in the VS code extension list.
	
This will add a VS code extension as well as open a file on start up of the codespace.

Next lets add some code to run on creation of the Codespace!

 ### :keyboard: Activity: Execute code on creation of the Codespace

1. Edit the `.devcontainer/devcontainer.json` file.
2. Add the following postCreateCommand to the body of the file before the last `}`. 
```
    ,
    "postCreateCommand": "echo '# Writing code on Codespace Creation!'  >> codespace.md"
```
3. Click Commit changes directly to the main branch.
4. Create a new Codespace by navigating to the landing page of your repository.
5. Click the `Code` button located in the middle of the page.
6. Click the `Codespaces` tab on the box that pops up.
7. Click the `Create codespaces on main` button OR click the `+` sign on the tab. This will create a new Codespace on the main branch.
**Wait about 2 minutes for the codespace to spin itself up. Note, its a VM spinning up in the background**
8. Verify your codespace is is running as you did above.
9. Verify the `codespace.md` file now has the text `Writing code on Codespace Creation!`.
	
**Wait about 20 seconds then refresh this page for the next step.**
 
</details>

<details id=4>
<summary><h2>Step 4: Personalize your Codespace!</h2></summary>

_Nicely done customizing your Codespace!_ :partying_face:

When using any development environment customizing the settings and tools to your preferences and workflows is an important step. GitHub Codespaces allows for two main ways of personalizing your codespaces which are `Settings Sync` with VS Code and `dot files`.
	
`Dot files` will be the focus of this activity.
	
**What are `dot files`?**: Dotfiles are files and folders on Unix-like systems starting with . that control the configuration of applications and shells on your system. You can store and manage your dotfiles in a repository on GitHub.

Let's see how this works!

### :keyboard: Activity: Enable a `dot file` for your Codespace

1. Start from the landing page of your repository.
2. In the upper-right corner of any page, click your profile photo, then click Settings
3. In the `Code, planning, and automation` section of the sidebar, click  Codespaces.
4. Under `Dotfiles`, select `Automatically install dotfiles` so that GitHub Codespaces automatically installs your dotfiles into every new codespace you create.
5. Choose YOUR current skills working repository as the repository install dotfiles from.

### :keyboard: Activity: Add a `dot file` to your reposiotry and run your Codespace
	
1. Start from the landing page of your repository.
2. Click the `Code` button located in the middle of the page.
3. Click the `Codespaces` tab on the box that pops up.
4. Click the `Create codespaces on main` button.
**Wait about 2 minutes for the codespace to spin itself up. Note, its a VM spinning up in the background**
5. Verify your codespace is is running. The browser should contain a VS code web based editor a a terminal should be present such as the below:
![codespace1](https://user-images.githubusercontent.com/26442605/207355196-71aab43f-35a9-495b-bcfe-bf3773c2f1b3.png)

1. From inside the Codespace in the VS Code explorer window create a new file `setup.sh`.
2. Add the following code inside of the file:
```
#!/bin/bash

sudo apt-get update
sudo apt-get install sl
```
	
3. Save the file. Note: The file should autosave.
4. Commit the file changes. From the VS Code terminal enter:
```
git add setup.sh --chmod=+x
git commit -m "Adding setup.sh from the codespace!"
```
5. Push the changes back to your repository. From the VS Code terminal etner:
```
git push
```
6. Switch back to the homepage of your repository and view the `setup.sh` to verify the new code was pushed to your repository.
7. Close the Codespace web browser tab.
8. Click the `Create codespaces on main` button OR click the `+` sign on the tab. This will create a new Codespace on the main branch.
**Wait about 2 minutes for the codespace to spin itself up. Note, its a VM spinning up in the background**
9. Verify your codespace is is running as you did above.
10. Verify the `setup.sh` file is present in your VS code editor.
11. From the VS Code terminal type or paste:
```
/usr/games/sl
```
11. Enjoy the show!

**Wait about 20 seconds then refresh this page for the next step.**
</details>

<details id=X>
<summary><h2>Finish</h2></summary>

_Congratulations friend, you've completed this course!_

<img src="https://octodex.github.com/images/welcometocat.png" alt=celebrate width=300 align=right>

Here's a recap of all the tasks you've accomplished in your repository:

* You've learned how to create a Codespace and push code to your repository from the Codespace.
* You've learned how to use custom images in your Codespace.
* You've learned how to customize your Codespace.
* You've learned how to persoalize your Codespace.

### Additional learning and resources

- [Developing in a codespace](https://docs.github.com/en/codespaces/developing-in-codespaces/developing-in-a-codespace). Learn how to delete, open an existing, connect to a private network, forward ports, and much more inside a Codespace
- [Set up your repository](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/introduction-to-dev-containers). Learn how to set minimum machine spces, add badges, set up a template repo, and much more inside a Codespace.
- [Personalize and Customize Codespaces](https://docs.github.com/en/codespaces/customizing-your-codespace/personalizing-github-codespaces-for-your-account). Learn how to use setting sync, dotfiles, set the default region, set the default editor, and much for your Codespace.
- [Prebuild your Codespace](https://docs.github.com/en/codespaces/prebuilding-your-codespaces/about-github-codespaces-prebuilds)
- [Manage your Codespace](https://docs.github.com/en/codespaces/managing-codespaces-for-your-organization/enabling-github-codespaces-for-your-organization)


### What's next?

- Learn more about securing your supply chain by reading: [GitHub Codespaces overview](https://docs.github.com/en/codespaces/overview).
- [We'd love to hear what you thought of this course](https://github.com/skills/.github/discussions).
- [Learn another GitHub skill](https://github.com/skills).
- [Read the Get started with GitHub docs](https://docs.github.com/en/get-started).
- To find projects to contribute to, check out [GitHub Explore](https://github.com/explore).

</details>

---

Get help: [Review the GitHub status page](https://www.githubstatus.com/)

&copy; 2022 TBD-copyright-holder &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [CC-BY-4.0 License](https://creativecommons.org/licenses/by/4.0/legalcode)
