
--------------------------------------------------------------------------
|                            nodejs express and ejs CRUD with maysql         |
------------- -------------------------------------------------------------


Firstable go Ampps open server then go to phpmyadmin create database then create table with 3 columns id auto_increment name 
description then follow bellow steps:


Step 1 : open new folder then install  npm init 
			 
		
Step 2 : Install Requred packages using NPM like this ===> 
			==> npm install  express mysql body-parser ejs --save
			
		
Step 3 : Add follwoing code in app.js
		
			const path = require('path');
			const express = require('express');
			const ejs = require('ejs');
			const bodyParser = require('body-parser');
			const mysql = require('mysql');
			const app = express();

			// Server Listening
			app.listen(3000, () => {
				console.log('Server is running at port 3000');
			});
			
		
		
Step 4 : Create Database Connection 
			const mysql=require('mysql');
			
			const connection=mysql.createConnection({
			  host:'localhost',
			  user:'root',
			  password:'put your massword',
			  database:'put name of your database)'
			});
			
			connection.connect(function(error){
			  if(!!error) console.log(error);
			  else console.log('Database Connected!');
			}); 

Setp 5 : Define view engin with ejs / public path / view files path / bodyParser/express static

			app.set('view engine', 'ejs');
                        app.set('views',path.join(__dirname,'views'));
			app.use(bodyParser.json());
			app.use(bodyParser.urlencoded({ extended: false }));
                        app.use(express.static(path.join(__dirname)));
                        app.use(express.static(path.join(__dirname, 'public')));
                        app.use(express.static(path.join(__dirname, 'public','css')));

Setp 6 : Define index path with '/' and ejs file
			
			//route for user index page
			app.get('/',(req, res) => {
				res.render('index', {
					title: 'ALL AUTHORS '
				});
			});

Setp 7 : Run a server and check with Browser
			node app

			http://localhost:3000/
			
Step 8 : Get value from database and show in ejs template