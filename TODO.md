## Flask's blueprint system is pretty vital.

When working with larger projects, having dozens of routes in one file gets... well, uh, hellish.
That's why to kick things off we're going to focus on working with blueprints.

### Packages v. Blueprints

So, you may have noticed that I've used a few different terms: packages and blueprints. So, are they the
same thing? Not quite.

#### What's the difference?

Packages are one way of beginning to separate your code. Packages are decent for mid-size projects, where
you need to work with multiple modules containing classes, utility functions, etc., but you don't have
so many routes that those need to be broken up too much. Packages are simple. They involve splitting your file tree into something that looks like this:

```
Online_Store
│   README.md
│   requirements.txt
|   app.py    
│
└───online_store
│   │   
│   │   
│   │
│   └───static
│   |   │   styles.css
│   |   │____assets
│   |          somepicture.jpeg
|   |___templates
│         index.html   

```

In packages, you would break your code up into modules, leaving basic things in the project's root folder. Within the "big"
package folder (in this example, online_store), you would keep your __init__, config, and python module files, with subfolders
for static files like assets and styles, and a subfolder for templates (if you're directly serving HTML).

Blueprints separate your routes into multiple files. This is the key difference between packages and blueprints. In a larger
project, it's helpful to NOT have all of your routes in the same file. Thousands of lines of code in any given file is not good
practice, it gets difficult to maintain, and it's frustrating to scroll up and down that many times just to find that ONE route you need to make a change to.

For example, blueprints would encapsulate "main" routes: your home page, about page, and maybe contact page, separately from your "admin" routes, and keep those separate from your "user authentication" routes.

If you haven't already, check out the resources in the main Varsity repository. We've linked great resources for blueprints there. Once you feel ready, get back here and complete the following TODOs:

1. Set up your file structure. You'll need an app.py file, and a main project folder to start (I like to name mine either server/API if I'm building an API, or the project name if I'm just serving HTML). For the sake of consistency throughout the instructions, let's call this folder "week_one_blueprints"

2. It's good practice to keep app.py in your project's root directory. Obviously, it can work if you move it (if you need to see it in your server folder, for example), but it can cause problems. For now, since we aren't building an API, let's keep it in our project's root.

3. This project is going to stay relatively general, and we'll be creating lots of dummy routes to start. Once you're done, feel free to go refactor a previous project to use blueprints, or add more to this as a stretch challenge. For now, create an __init__.py file in your week_one_blueprints folder. Then, add a config.py file.

4. Initialize your Flask application in __init__.py. Also, make sure you place from flask import Blueprint at the top of the file. We'll need that in a minute.

5. In your project's root directory, create a .env file, and add a SECRET_KEY. We don't really need this in this application, but I want you to get practice with the whole setup.

6. In config.py, create class Config. See your resources for proper setup. This class doesn't have an __init__ method, it just has attributes. Inside your class should look something like this for now:

    SECRET_KEY = os.getenv('SECRET_KEY')

7. In __init__.py, create your app. Set app.config.from_object(Config) so that your application can use the environmental variables you just configured. Now, the rest is going to be pretty independent, but this is what we need:

      1. Create a "main" folder. This folder has to have an __init__.py file in it, but it's okay to leave that file empty. Also in this folder, create a routes.py folder. At the top of routes.py, add from flask import Blueprint, and initialize your "main" blueprints. Add any three routes serving any basic HTML files in this file.
      2. Create a "party" folder. Follow the above instructions to initialize, and make sure you have at least two routes in this one. Don't forget to create your templates to go along with these!
      3. In your main __init__.py in your project root, make sure you're registering your blueprints so your app knows what it's looking for. And, don't forget to test!

8. If you run into problems with things running, check these few things:

      1. Make sure that in each folder, you're starting your routes with "/<blueprintname>/<routename>" - OR that you're adding URL prefixes when you register your blueprints (this is a stretch challenge, if you don't know what this means or how to do this, don't worry! (or Google))
      2. Check your file structure, the locations of your templates, and your resources. They're there for a reason! We trust that you guys mostly know what you're doing, you got this!
      3. If all else fails, we'll be hosting office hours each week to help debug and check things out. You can Slack us anytime with questions and we'll get back to you as soon as we can.
