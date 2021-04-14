# Welcome to BlackWall!

  
This project called BlackWall, was created to store a waiting list of customers. The application has two pages, wich are for registration and the other is a table with the costumers.
In the table it is possible to delete the users by clicking on the X.
The framework used in this was VueJs with preprocessor Sass and VueRouter. To persist data I used localStorage.
To check other dependecies please go to package.json



# How to run


**Clone**:
To clone the project please go to:
https://github.com/luisfop/BlackWall.git

On the terminal execute: 

    git clone: https://github.com/luisfop/BlackWall.git

Open the Stefanini folder:

    cd Stefanini/
    
Execute the command :

    npm install

   or

    yarn install

To run the application execute the command line:

    npm run serve
    or
    yarn run serve


# How to Use

Open the browser and go to url:
 https://localhost:8080

The land page is the registration form. To check the list of costumers whom is waiting, please go to "ver tabela" button on the bottom of the page.

# PS:

I chose not to use a form input validator library such as Vuelidate or Vuetify becuse I wanted to keep the code as native Javascript as I could.
