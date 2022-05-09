## Create Angular weatherApp - Part 1

Welcome to this series, hope you have installed angular & node -> [Prerequisites & Installation](https://shijoshaji.hashnode.dev/prerequisites)


## What are we building?
`Before we start, I like to show how the end product will look like.`

[GitHub Source Code](https://github.com/shijoshaji/weatherApp)

Fetched data based on geo location: 
> ![LowerTemp.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1651907689829/bDtNeNwcl.PNG align="left")


Fetched data based on City name specified: 
> ![MaxTemp.PNG](https://cdn.hashnode.com/res/hashnode/image/upload/v1651907706563/mkC284JCL.PNG align="left")

## Create a workspace and weatherApp application
Open gitbash/terminal and lets create a workspace.


- Run the CLI command ng new and provide the name my-app, as shown here:
```
ng new my-app
```


- Here **ng new** command is to create app, **my-app** is the name of the app you can give.

 I have created `weatherApp`
```
ng new weatherApp
``` 

2. The **ng new** command prompts you for information about features to include in the initial app. Accept the defaults by pressing the Enter or Return key.

3. The Angular CLI installs the necessary Angular npm packages and other dependencies. This can take a few minutes.

4. The CLI creates a new workspace and a simple Welcome app, ready to run.

## Run the application
The Angular CLI includes a server, for you to build and serve your app locally.
Navigate to the workspace folder, such as **weatherApp**.
Run the following command:
```
cd weatherApp
ng serve --open
```

The **ng serve** command launches the server, watches your files, and rebuilds the app as you make changes to those files.

The --open (or just -o) option automatically opens your browser to [http://localhost:4200/](http://localhost:4200/)

If your installation and setup was successful, you should see a page similar to the following.

![app-works.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1651906256289/X3qUnnYWG.png align="left")

> That's it😇 You did good

[NEXT ?](https://shijoshaji.hashnode.dev/create-angular-weatherapp-part-2)
