
<img src="https://i.imgur.com/CYJCaua.png" alt="website">

### Code Institute Milestone Project 3

# **Chocolatier** 


An all-chocolate website where users can contribute recipes and get recommendations for essential baking tools. 

<img src="https://i.imgur.com/b9sdn9o.jpg" alt="banner">

## UX 

### User stories

As a user, I would like to:

- find chocolate recipes in one website so I do bake recipes myself.
- submit my own recipes and other users can submit their own too.
- update my own recipes and other people's recipes.
- delete my own recipes and other people's recipes.
- easily view the website while I am baking and easily shift from mobile to desktop and vice versa.
- manouver through the website with ease.
- to buy baking tools recommended by the recipes.


As a seller, I would like to: 

- showcase my baking products alongside with chocolate recipes.
- recommend products for every recipe in the website.
- sell baking tools to a target audience.

### Mockup

Since the main goal of this project is to create, read, edit and delete records from the Mongodb database, I did a basic design so the user can easily manouver around the website and to manipulate the data. I did as much as possible gave each route a separate page and a confirmation message that a deletion of an entry will be made.

[Mobile wireframes](https://i.imgur.com/un7WiC3.png)

[Desktop wireframes](https://i.imgur.com/ew0vM1t.png)

## Features 

### Existing Features
- Sidenavbar - For mobile view, users can navigate the website through the sidenavbar or the links in the footer.
- Uniform cards - Users will have great ease scanning for reipes because of the uniformity of the layout of the recipe cards.
- Page updates - Users are redirected to updated pages upon submission, revision or deletion of a recipe. 
- Form validation - Users will not be allowed to submit a form if a field is left blank or if the required input type is not met.
- Modals - Modals are used to confirm a deletion of a recipe. During deletions, users can choose to either confirm and will be directed back to the updated All Recipes page or to cancel.
- Randomized product recommendation - A random product will be recommended upon opening a whole recipe. I made this by using 
- Product links to Amazon - Since I did not include a product page, I linked the products to Amazon instead. 
    ```products=mongo.db.products.aggregate([{'$sample': {'size': 3}}])```

    to randomly get 3 products from the collection. Then use Jinja for and if loop to pick one from the 3 products. Otherwise, Jinja will throw a "TypeError: object of type 'Cursor' has no len()".

    ````
        {% for product in products %}
        {% if loop.index < 2 %}
        {% endif %}
        {% endfor %}
    ````
### Future Features
- User login - This project did not require a user login that is why I did not include it. Although, it would be optimal for websites like this to have a user login so not anyone can edit and delete data. This project is mainly for CRUD operations.
- Search option - I did not include a search option because my website is already narrowed down to one subject, CHOCOLATE, and the products I included were baking products mostly used with chocolates. A search option right now would be unnecessary.
- Product page - I did not include a product page because I want to focus on the CRUD operations for the recipes. 
- Pagination - I will add pagination if the recipes begin to increase in number.

## Technologies Used ##

Here are the list of programming languages, technologies, libraries, frameworks and plugin used for this website:

- HTML
- CSS
- [Bootstrap](https://getbootstrap.com/) - used for navbars, grid, parallax, buttons, forms and card styling
- [MaterializeCSS](https://materializecss.com/) - used for additional styling and components like textarea and Modals
- [Google Fonts](https://fonts.google.com/) - used for font-styles [Playfair](https://fonts.google.com/specimen/Playfair+Display?query=playfair), [Merriweather](https://fonts.google.com/specimen/Merriweather?query=merriweather), [Roboto](https://fonts.google.com/specimen/Roboto?query=roboto)
- [Font Awesome](https://fontawesome.com/) - used for icons
- [jQUery](https://jquery.com/) - used for eventhandling and animation 
- [Python 3.8.2](https://www.python.org/) - used for building a connection between Mongodb database and Flask app
- [Flask](https://pypi.org/project/Flask/) - used as the project's framework, Flask uses dependencies and store them in ````requirements.txt```` to build environments.
- [Jinja](https://jinja.palletsprojects.com/en/2.11.x/) - used for handling templates
- [MongoDb Atlas](https://www.mongodb.com/cloud/atlas) - MongoDB cloud service used for making document database that stores JSON-like documents
- [Heroku](https://www.heroku.com/home) - used for hosting this project. Github cannot host Python project. Requires ``requirements.txt``  and  ````Procfile````.


## Testing

### A. Manual Testing

I used Google Developer tools to test different components

1. Website pages
    - Pages are responsive on different screen breakpoints.
    - There are no weirdly positioned elements.
    - Pages are mobile adaptable.

2. Form validation
    - Users are not allowed to submit a form without filling required input.
    - Throws an error message.
    - Placeholders guides the user to write the right input.

3. Modal 
    - Appears everytime to confirm an action was made either by submission or deletion of recipe.
    - Redirects to the updated page.

4. Submit button
    - Disabled until form is completed.
    - does not allow submission of incomplete form

5. Product links
    - opens in a new tab

### B. Code Validator testing

- [HTML Validator](https://validator.w3.org/) Passed tests except for one document

    1. on  ``whole-recipe`` file, 
    ````
    Element div not allowed as child of element ul in this context.
    ````

- [CSS Validator](https://jigsaw.w3.org/) 
    
    Passed tests, no errors found

- [JSHint](https://jshint.com/)

    found one issue 
    ````	
    'Trailing comma in arguments lists' is only available in ES8 (use 'esversion: 8').
    ````

- [PEP8](http://pep8online.com/) 

    Passed test, no errors found

### C. Browser Testing

####    No issues found 

-   Google Chrome
-   Mozilla Firefox
-   Microsoft Edge

### D. Mobile Testing

#### No issues found

-   Samsung Galaxy Note 10 plus
-   Iphone 4
-   Iphone 8 plus
-   Samsung Note 9

-   Samsung Galaxy tab has some issue with parallax layout

### E. Desktop and laptop Testing

#### No issues found


## Deployment 

I use Gitpod IDE extension to clone Github repositories quickly. But you can do this too locally or on your chosen IDE.

1. Clone or download the Zip from Github

2. Make a new directory: 

    ````
    $ mkdir directory
    ````

    or  change directory to where you want to clone the repository:
   
    ````
    $ cd directory
    ````

3. Paste the clone link

    ````
    $ git clone https://github.com/loulunds/3rd_Milestone_Project.git
    ````

4. Update the ``requirements.txt`` file if you need to used additional dependencies. Procfile is already included in the repo. These two are Heroku's requirement to build the app.

    ````
    pip3 freeze --local > requirements.txt
    ````

In this project you need to set up environment variables so you can keep your sensitive information safe like passwords. You can do this by:

1. Update the ``env.py`` and ``.gitignore`` file on root directory. ``env.py`` should be typed in your ``.gitignore`` file.

2. In ``env.py`` there should be:

    ````
    import os
    os.environ["variable name"] = "value of variable"
    ````
    -   In this project, I used Mongodb Atlas database so you need to make an account there then use ``"MONGO_URI"`` as variable and your MongoDB connection by going to ``Overview`` of your Cluster and click connect and choose option ``Connect your application`` and copy the link
    
    -   Paste the link in your "value of variable"

3. Add this to your ``app.py`` file

    ````
    from os import path
    if path.exists("env.py") :
        import env

    ````
4. Now you can add this to app.py and your sensitive information is safe

    ````
    app.config["MONGO_URI"] = os.environ.get('MONGO_URI', 'mongodb://localhost')
    ````
This project is hosted in Heroku, to do that:

1. Create an app in Heroku

2. In your terminal, login to Heroku

    ````
    heroku login -i
    ````
3. Go to ``deploy`` and find the clone link:

    ````
    $ heroku git:clone -a <app-name>
    ````

4. Before pushing, add variables to ``Config Variables`` option in Heroku.
    
    ````
    <key>            <value>
    MONGO_URI     <your Mongo_URI link>
    IP            0.0.0.0
    PORT          5000
    SECRET_KEY    <SECRETKEY> if you have

5. if you have everything above

    ````
    $ git push heroku master
    ````

## Credits


### Images 

- [Pixabay](https://pixabay.com/) - for free images

- [Imgur](https://imgur.com/) - for hosting my images

### Recipes
- [Google](https://www.google.com/) - for yummy chocolate recipes

### Codes
- [Stack Overflow](https://stackoverflow.com/)

- [Bootstrap](https://getbootstrap.com/)

- [MaterializeCSS](https://materializecss.com/)

- [Jinja](https://jinja.palletsprojects.com/)

## Acknowledgements

Thanks to my mentor, Dick Vlaanderen and to the tutor and student care support personnels of Code Institute.
Also, to the thousands of contributor in Slack and Slack Overflow.

## Disclaimer

This project is for educational purposes only. 

[Back to top](#)