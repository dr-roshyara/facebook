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



