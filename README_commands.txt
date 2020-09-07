#Git Commands 

	-touch README.mD 
	-echo "# facebook" >> README.md
	-git init
	-git add README.md
	-git commit -m "first commit"
	-git remote add origin https://github.com/user_name/git-test.git
	-git push -u origin master
#These commands has connected local repository to the remote repository in Github and made a first commit 
#Download the laravel package in your directory using command

	-laravel new facebook 
#Go to mysql and create a database by using mysql command 
	 mysql -u root -p 
	 give the passport root 
	#use the comamnd 
	create database facebook 
#Set up the database connection . 
	#Go to .env file  
	#Change the mysql settings 
	database name :facebook 
	username: root 
	passport :root
#Download the passport package 
	composer require laravel/passport 
	#Migrate the passport  built in table 
	php artisan migrate 
	#Use the command passport:install 
	php artisan passport:install 
#	#it gives the following information then 
		#ncryption keys generated successfully.
		#Personal access client created successfully.
		#Client ID: 1
		#Client secret: GcYTVnuHywXzKDwPnjAH42P3iogG5LEUY4J0USOv
		#Password grant client created successfully.
		#Client ID: 2
		#Client secret: Bf8l5rnZBG0hIAprYQun0gGb8GRMQMVUYcDqD5Li
#		#Go To the User.php model and add the trait : HasApitokens
		#Add this line to the App\User.php 
		use Laravel\Passport\HasApiTokens;
		class User extends Authenticatable
		{  
    		use Notifiable, HasApiTokens;
		// here goes the model further 
		...	
#		#Go to the App\Providers\AuthServiceProdiders.php 
		#add at the top where use commands are given  
		use Laravel\Passport\Passport;
		#add in the booth method route methods 
		Passport::routes();
#		#Next You set up the laravel authnication driver 
		#Go to config/auth.php file 
		edit the guards as following 
		'api' => [
            // 'driver' => 'token',
            'driver' => 'passport',
            'provider' => 'users',
            'hash' => false,
        ],
#		#Next You go to the Http Kernel file and add the middle ware . Without adding it , you cant use 		#the middle ware. 
		# Here add the last line of code 
		 protected $middlewareGroups = [
        'web' => [
            \App\Http\Middleware\EncryptCookies::class,
            \Illuminate\Cookie\Middleware\AddQueuedCookiesToResponse::class,
            \Illuminate\Session\Middleware\StartSession::class,
            // \Illuminate\Session\Middleware\AuthenticateSession::class,
            \Illuminate\View\Middleware\ShareErrorsFromSession::class,
            \App\Http\Middleware\VerifyCsrfToken::class,
            \Illuminate\Routing\Middleware\SubstituteBindings::class,
            \Laravel\Passport\Http\Middleware\CreateFreshApiToken::class,		
		#see the last line of code 
#		# Check all the active routes in laravel 		
		 php artisan route:list

#Add the Laravel ui package so that you can use the buit in ui 
		#install ui 
		composer require laravel/ui
		# add vue as ui frontend 
		php artisan ui vue --auth 

#install the dependencies packages 
		npm install 
		#compile them 
		npm run dev 
		#If there is success on compiling. You have started the basic settings of vuejs. 

#Set up a controller 
#Now lets start creating the app.First you create the frontend Compiler 
	php artisan make:controller AppController 
	#Create an index function on it as following 
	 //
    public function index(){
       
        return view('home');
    }

#	#change the route file web.php as following 
	#remove the welcome route and welcome.blade.php 
	// Route::get('/', function () {
		//     return view('welcome');
		// });

		Auth::routes();
	#remove the home route 
		// Route::get('/home', 'HomeController@index')->name('home');
	#Add the following route 
	Route::get('{any}', 'AppController@index')
			->where('any', '.*') // This means any route which can start with . or any 
			->middleware('auth') // here we use auth as middleware 
			->name('home');     // here we call the route as home 

#Set up for Vue.js 
#	#Edit the home.blade.php file 
	#Write the following lines 
	@extends('layouts.app')
	@section('content')
	<App></App>
	@endsection

#	#Edit the app.js file as following 
	Edit the resources/js/app.js file and write only the following lines 
	/**
	* First we will load all of this project's JavaScript dependencies which
	* includes Vue and other libraries. It is a great starting point when
	* building robust, powerful web applications using Vue and Laravel.
	*/
#	#app.js 
	import Vue from 'vue';
	import router from './router';
	import App from './components/App';	

	require('./bootstrap');	
	const app = new Vue({
		el: '#app',
	
		components: {
			App
		},
	
		router,
	});
#	#install vue router 
	npm install vue-router  --save-dev 
	npm run dev 

#	#create a router.js file: resources/router.js and add the following lines of code 
	#This is the vue-router file and we write here the routes. 
	:router.js
		import Vue from 'vue';
		import VueRouter from 'vue-router';
		import Start from './views/Start';
		
		Vue.use(VueRouter);
		
		export default new VueRouter({
		mode: 'history',
		
		routes: [
			{
			path: '/', 
			name: 'home', 
			component: Start,
			}
		]
		});
#	# The component start does exits yet . It should be the start component . So we crete it now . 
	#Create a vie directory inside js and then a Start.vue file inside it . 
#	# js/views/Start.vue 
		<template>
		<div>asdf</div>
		</template>
		
		<script>
			export default {
				name: "Start"
			}
		</script>
		
		<style scoped>
		
		</style>	
#	# Finally create a  App.vue component . this is the main componet 
	#components/App.vue 
	<template>
		<div>Start
		<router-view/></router-view>
		</div>
	</template>
	
	<script>
		export default {
			name: "App"
		}
	</script>
	
	<style scoped>
	
	</style>
	..
#change the redirect to home as '/'
	# I searched all
	protected $redirectTo = RouteServiceProvider::HOME;
    and changed it to 
	 protected $redirectTo = '/';
#Setting of Tailwind 
	#install tailwind 
	npm install tailwindcss
#	#Go to the resources/sass/app.scss file and add the follwoing lines fo code 
	#resources/sass/app.scss
	@import "tailwindcss/base";

	@import "tailwindcss/components";

	@import "tailwindcss/utilities";
#	# execute the following command to generate tailwind.config.js 
	npx tailwindcss init 
#	# Edit the webpack.mix.js 
	# Edit it as folllwoing 
	const mix = require('laravel-mix');
	const tailwindcss = require('tailwindcss');

	mix.js('resources/js/app.js', 'public/js')
		.sass('resources/sass/app.scss', 'public/css')
		.options({
			processCssUrls: false,
			postCss: [tailwindcss('./tailwind.config.js')],
		});
#	# npm run dev 
	#This command will compile the tailwind utilities
#	# check if tailwind is working 
	#for example go to views/layout/app.blade.php 
	<body class="bg-gray-400"> 
	#I found it working congratulation 
	




