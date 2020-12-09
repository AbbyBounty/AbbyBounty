<h1 align="center">Hi 👋, I'm Abhilash</h1>
<h3 align="center">Full Stack Developer | DevOps | MEAN Stack | Docker</h3>

<div class="codepen" data-height="265" data-theme-id="light" data-default-tab="result" data-user="abbybounty" data-slug-hash="vYXXJrj" data-prefill='{"title":"Knockout.js Typewriter Effect","description":"A cleanly composed Knockout.js custom binding to emulate a typewriter effect. Provided an array of strings, enables control of speed, pause and infinite looping.","tags":["javascript","typewriter","knockout-binding","typing","knockout"],"scripts":["https://cdnjs.cloudflare.com/ajax/libs/knockout/3.4.2/knockout-min.js"],"stylesheets":[]}'>
  <pre data-lang="html">&lt;div class="center">
  
  &lt;div class="content">
    
    &lt;h1 class="title" >Abhilash Kamble&lt;/h1>
    
    &lt;h2 class="title">&nbsp;
      &lt;span class="red-emph" data-bind="typewriter: { words: ['Full Stack Developer', 'problem solver.', 'MEAN Stack', 'Angular','Docker','AWS','Microservices','spring boot','java','javascript','NodeJS','MongoDB','Express'], speed: 30, iterations: 1, pause: 250 }">&lt;/span>      
    &lt;/h2>		
    
  &lt;/div>		
  
&lt;/div></pre>
  <pre data-lang="css">.center{
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

.title {			
  font-weight: 200;
  text-align: center;
}

h1.title {
  font-size: 4.5em;
}

h2.title {
  font-size: 2em;
}

.red-emph {
  border-bottom: 2px solid #ce3635;
  padding-bottom: .125em;
}

.content {
  box-sizing: border-box;
  padding: 4rem;
  width: 100%;
}

/* hydrogen.css (https://github.com/pimbrouwers/HydrogenCSS) */
html{-ms-text-size-adjust:100%;-webkit-text-size-adjust:100%;font-family:sans-serif}body{margin:0;font:16px/1 -apple-system,system-ui,BlinkMacSystemFont,"Segoe UI",Roboto,"Helvetica Neue",sans-serif;-moz-osx-font-smoothing:grayscale;-webkit-font-smoothing:antialiased}blockquote,figure,h1,h2,h3,h4,h5,h6,ol,p,ul{margin:0;padding:0;line-height:1.5}li,main{display:block}strong{font-weight:700}a,button{color:inherit;transition:background .3s}a{text-decoration:none}button{overflow:visible;border:0;font:inherit;-webkit-font-smoothing:inherit;letter-spacing:inherit;background:0 0;cursor:pointer}::-moz-focus-inner{padding:0;border:0}:focus{outline:0}img{max-width:100%;height:auto;border:0}.h-c{margin:0 auto;max-width:76.5em;padding:0 1.5em}.h-c>.h-g{margin:0 -1.5em}.h-c .h-g .h-g{margin:0 -1.5em}.h-c .h-u{padding:0 1.5em}.h-g{display:-webkit-box;display:-webkit-flex;display:-ms-flexbox;display:flex;-webkit-flex-flow:row wrap;-ms-flex-flow:row wrap;flex-flow:row wrap;-webkit-align-content:flex-start;-ms-flex-line-pack:start;align-content:flex-start}.h-g:after{content:"";clear:both;display:table}@media only screen{.h-u{float:left;width:100%;box-sizing:border-box}}.h-btn{background:#ddd;display:inline-block;padding:.75em 1.5em}.h-btn:hover{background:#c4c4c4}.h-btn[disabled]{opacity:.4;cursor:not-allowed}.h-btn[disabled]:hover{background:#ddd}.h-form fieldset{border:0;margin:0;padding:0}.h-form legend{border-bottom:1px solid #ddd;display:block;margin:.75em 0;padding:.75em 0;width:100%}.h-form input,.h-form select,.h-form textarea{border:1px solid #ddd;font:inherit;margin:0 0 .75em;padding:.75em}.h-form input:focus,.h-form select:focus,.h-form textarea:focus{border-color:#c4c4c4}.h-form input[required]:focus,.h-form select[required]:focus,.h-form textarea[required]:focus{border-color:red}.h-form input[disabled],.h-form select[disabled],.h-form textarea[disabled]{background:#efefef;cursor:not-allowed}.h-form input[type=checkbox]{margin:3px 3px 3px 4px}.h-form.h-form-stack input,.h-form.h-form-stack label,.h-form.h-form-stack select,.h-form.h-form-stack textarea{display:block}.h-form.h-form-stack input[type=checkbox]{display:inline-block}.h-list li{display:list-item;margin-left:1.5em}.h-menu li>a,.h-menu li>span{display:inline-block;margin:0;padding:.75em 1.5em}.h-menu li>span{font-weight:700}.h-menu li:first-child>span{padding-left:0}.h-menu.h-menu-inline li{display:inline-block}.h-tbl{border-collapse:collapse;width:100%;max-width:100%}.h-tbl td,.h-tbl th{padding:.75em}.h-tbl th{border-bottom:2px solid #ddd;text-align:left}.h-tbl td{border-top:1px solid #eaeaea}</pre>
  <pre data-lang="js">function Typewriter(element)
{
	this.element = element;
	this.iterations = 1; //-1 for infinite
	this.pause = 250;
	this.speed = 100;
	this.words = [];
	
	//internal counters
	this.charCounter = 0;
	this.iterationCounter = 0;
	this.wordIndex = 0;

	return this;
};

Typewriter.prototype.run = function(){			
	console.log(this);
	setTimeout(this.type.bind(this), this.pause);
};

Typewriter.prototype.speedPlusRandom = function(speed){
	return Math.floor((Math.random() * 50) + 1) + speed;
};

Typewriter.prototype.type = function(){
	if(this.charCounter &lt; this.words[this.wordIndex].length)
	{
		//typing
		this.element.innerHTML += this.words[this.wordIndex].charAt(this.charCounter);
		this.charCounter++;
		setTimeout(this.type.bind(this), this.speedPlusRandom(this.speed));
	}
	else if(this.wordIndex + 1 &lt; this.words.length || this.iterationCounter + 1 &lt; this.iterations || this.iterations === -1)
	{
		//start untyping if we're not on the last word						
		setTimeout(this.untype.bind(this), this.pause);
	}
};

Typewriter.prototype.untype = function(){
	if(this.charCounter > 0)
	{			
		//untyping			
		this.element.innerHTML = this.words[this.wordIndex].substring(0, this.charCounter - 1);
		this.charCounter--;
		setTimeout(this.untype.bind(this), this.speedPlusRandom(this.speed));
	}
	else if(this.wordIndex + 1 &lt; this.words.length){
		this.wordIndex++;						

		//start typing with next word (if exists)
		setTimeout(this.type.bind(this), this.pause);
	}
	else if(this.iterationCounter + 1 &lt; this.iterations || this.iterations === -1)
	{
		this.wordIndex = 0;
		
		//start typing with first word (if exists)
		setTimeout(this.type.bind(this), this.pause);
	}
};

Typewriter.prototype.withIterations = function(iterations){
	if(iterations) this.iterations = iterations;
	return this;
};

Typewriter.prototype.withPause = function(pause){
	if(pause) this.pause = pause;
	return this;
};

Typewriter.prototype.withSpeed = function(speed){
	if(speed) this.speed = speed;
	return this;
};

Typewriter.prototype.withWords = function(words){
	if(words) this.words = words;
	return this;
};

ko.bindingHandlers.typewriter = {
	init: function(element, valueAccessor){
		var options = ko.unwrap(valueAccessor());

		var typewriter = new Typewriter(element)
													.withIterations(options.iterations)
													.withPause(options.pause)
													.withSpeed(options.speed)
													.withWords(options.words);

		typewriter.run();
	}
};


window.onload = function(){
  ko.applyBindings({});
};</pre></div>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>


<img src="https://github-readme-stats.vercel.app/api/?username=AbbyBounty&show_icons=true&title_color=fff&icon_color=79ff97&text_color=9f9f9f&bg_color=151515" alt="Stats" align="right">

<p align="left"> <img src="https://komarev.com/ghpvc/?username=abbybounty&label=Profile%20views&color=0e75b6&style=flat" alt="abbybounty" /> </p>

<p align="left"> <a href="https://twitter.com/abby_bounty" target="blank"><img src="https://img.shields.io/twitter/follow/abby_bounty?logo=twitter&style=for-the-badge" alt="abby_bounty" /></a> </p>

- 🔭 I’m currently working on **CDAC Project**

- 🌱 I’m currently learning **React**

- 💬 Ask me about **Angular , Spring boot**

- 📫 How to reach me **abhilash.kamble376@gmail.com**

- 📄 Know about my experiences [https://abbybounty.github.io/website/](https://abbybounty.github.io/website/)

<h3 align="left">Connect with me:</h3>
<p align="left">
<a href="https://codepen.io/abhilash kamble" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/codepen.svg" alt="abhilash kamble" height="30" width="40" /></a>
<a href="https://twitter.com/abby_bounty" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/twitter.svg" alt="abby_bounty" height="30" width="40" /></a>
<a href="https://linkedin.com/in/abhilashkamble" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/linkedin.svg" alt="abhilashkamble" height="30" width="40" /></a>
<a href="https://fb.com/abhilash.kamble33" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/facebook.svg" alt="abhilash.kamble33" height="30" width="40" /></a>
<a href="https://instagram.com/abby_bounty" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/instagram.svg" alt="abby_bounty" height="30" width="40" /></a>
<a href="https://www.codechef.com/users/abby_bounty" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.1.0/icons/codechef.svg" alt="abby_bounty" height="30" width="40" /></a>
<a href="https://www.hackerrank.com/abby_bounty" target="blank"><img align="center" src="https://cdn.jsdelivr.net/npm/simple-icons@3.0.1/icons/hackerrank.svg" alt="abby_bounty" height="30" width="40" /></a>
</p>

<h3 align="left">Languages and Tools:</h3>
<p align="left"> <a href="https://developer.android.com" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/android/android-original-wordmark.svg" alt="android" width="40" height="40"/> </a> <a href="https://angular.io" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/angularjs/angularjs-original.svg" alt="angularjs" width="40" height="40"/> </a> <a href="https://www.arduino.cc/" target="_blank"> <img src="https://cdn.worldvectorlogo.com/logos/arduino-1.svg" alt="arduino" width="40" height="40"/> </a> <a href="https://aws.amazon.com" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/amazonwebservices/amazonwebservices-original-wordmark.svg" alt="aws" width="40" height="40"/> </a> <a href="https://azure.microsoft.com/en-in/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/microsoft_azure/microsoft_azure-icon.svg" alt="azure" width="40" height="40"/> </a> <a href="https://www.gnu.org/software/bash/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/gnu_bash/gnu_bash-icon.svg" alt="bash" width="40" height="40"/> </a> <a href="https://getbootstrap.com" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/bootstrap/bootstrap-plain.svg" alt="bootstrap" width="40" height="40"/> </a> <a href="https://www.cprogramming.com/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/c/c-original.svg" alt="c" width="40" height="40"/> </a> <a href="https://circleci.com" target="_blank"> <img src="https://www.vectorlogo.zone/logos/circleci/circleci-icon.svg" alt="circleci" width="40" height="40"/> </a> <a href="https://www.w3schools.com/cpp/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/cplusplus/cplusplus-original.svg" alt="cplusplus" width="40" height="40"/> </a> <a href="https://www.w3schools.com/cs/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/csharp/csharp-original.svg" alt="csharp" width="40" height="40"/> </a> <a href="https://www.cypress.io" target="_blank"> <img src="https://raw.githubusercontent.com/simple-icons/simple-icons/6e46ec1fc23b60c8fd0d2f2ff46db82e16dbd75f/icons/cypress.svg" alt="cypress" width="40" height="40"/> </a> <a href="https://www.djangoproject.com/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/django/django-original.svg" alt="django" width="40" height="40"/> </a> <a href="https://www.docker.com/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/docker/docker-original-wordmark.svg" alt="docker" width="40" height="40"/> </a> <a href="https://dotnet.microsoft.com/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/dot-net/dot-net-original-wordmark.svg" alt="dotnet" width="40" height="40"/> </a> <a href="https://expressjs.com" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/express/express-original-wordmark.svg" alt="express" width="40" height="40"/> </a> <a href="https://firebase.google.com/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/firebase/firebase-icon.svg" alt="firebase" width="40" height="40"/> </a> <a href="https://flask.palletsprojects.com/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/pocoo_flask/pocoo_flask-icon.svg" alt="flask" width="40" height="40"/> </a> <a href="https://cloud.google.com" target="_blank"> <img src="https://www.vectorlogo.zone/logos/google_cloud/google_cloud-icon.svg" alt="gcp" width="40" height="40"/> </a> <a href="https://git-scm.com/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/git-scm/git-scm-icon.svg" alt="git" width="40" height="40"/> </a> <a href="https://heroku.com" target="_blank"> <img src="https://www.vectorlogo.zone/logos/heroku/heroku-icon.svg" alt="heroku" width="40" height="40"/> </a> <a href="https://www.w3.org/html/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/html5/html5-original-wordmark.svg" alt="html5" width="40" height="40"/> </a> <a href="https://jasmine.github.io/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/jasmine/jasmine-icon.svg" alt="jasmine" width="40" height="40"/> </a> <a href="https://www.java.com" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/java/java-original-wordmark.svg" alt="java" width="40" height="40"/> </a> <a href="https://developer.mozilla.org/en-US/docs/Web/JavaScript" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/javascript/javascript-original.svg" alt="javascript" width="40" height="40"/> </a> <a href="https://jekyllrb.com/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/jekyllrb/jekyllrb-icon.svg" alt="jekyll" width="40" height="40"/> </a> <a href="https://www.jenkins.io" target="_blank"> <img src="https://www.vectorlogo.zone/logos/jenkins/jenkins-icon.svg" alt="jenkins" width="40" height="40"/> </a> <a href="https://kafka.apache.org/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/apache_kafka/apache_kafka-icon.svg" alt="kafka" width="40" height="40"/> </a> <a href="https://karma-runner.github.io/latest/index.html" target="_blank"> <img src="https://raw.githubusercontent.com/detain/svg-logos/780f25886640cef088af994181646db2f6b1a3f8/svg/karma.svg" alt="karma" width="40" height="40"/> </a> <a href="https://kubernetes.io" target="_blank"> <img src="https://www.vectorlogo.zone/logos/kubernetes/kubernetes-icon.svg" alt="kubernetes" width="40" height="40"/> </a> <a href="https://laravel.com/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/laravel/laravel-plain-wordmark.svg" alt="laravel" width="40" height="40"/> </a> <a href="https://www.linux.org/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/linux/linux-original.svg" alt="linux" width="40" height="40"/> </a> <a href="https://mariadb.org/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/mariadb/mariadb-icon.svg" alt="mariadb" width="40" height="40"/> </a> <a href="https://mochajs.org" target="_blank"> <img src="https://www.vectorlogo.zone/logos/mochajs/mochajs-icon.svg" alt="mocha" width="40" height="40"/> </a> <a href="https://www.mongodb.com/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/mongodb/mongodb-original-wordmark.svg" alt="mongodb" width="40" height="40"/> </a> <a href="https://www.microsoft.com/en-us/sql-server" target="_blank"> <img src="https://cdn.worldvectorlogo.com/logos/microsoft-sql-server.svg" alt="mssql" width="40" height="40"/> </a> <a href="https://www.mysql.com/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/mysql/mysql-original-wordmark.svg" alt="mysql" width="40" height="40"/> </a> <a href="https://nativescript.org/" target="_blank"> <img src="https://raw.githubusercontent.com/detain/svg-logos/780f25886640cef088af994181646db2f6b1a3f8/svg/nativescript.svg" alt="nativescript" width="40" height="40"/> </a> <a href="https://www.nginx.com" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/nginx/nginx-original.svg" alt="nginx" width="40" height="40"/> </a> <a href="https://nodejs.org" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/nodejs/nodejs-original-wordmark.svg" alt="nodejs" width="40" height="40"/> </a> <a href="https://www.oracle.com/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/oracle/oracle-original.svg" alt="oracle" width="40" height="40"/> </a> <a href="https://www.php.net" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/php/php-original.svg" alt="php" width="40" height="40"/> </a> <a href="https://www.postgresql.org" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/postgresql/postgresql-original-wordmark.svg" alt="postgresql" width="40" height="40"/> </a> <a href="https://postman.com" target="_blank"> <img src="https://www.vectorlogo.zone/logos/getpostman/getpostman-icon.svg" alt="postman" width="40" height="40"/> </a> <a href="https://www.python.org" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/python/python-original.svg" alt="python" width="40" height="40"/> </a> <a href="https://reactjs.org/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/react/react-original-wordmark.svg" alt="react" width="40" height="40"/> </a> <a href="https://reactnative.dev/" target="_blank"> <img src="https://reactnative.dev/img/header_logo.svg" alt="reactnative" width="40" height="40"/> </a> <a href="https://redis.io" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/redis/redis-original-wordmark.svg" alt="redis" width="40" height="40"/> </a> <a href="https://www.selenium.dev" target="_blank"> <img src="https://raw.githubusercontent.com/detain/svg-logos/780f25886640cef088af994181646db2f6b1a3f8/svg/selenium-logo.svg" alt="selenium" width="40" height="40"/> </a> <a href="https://spring.io/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/springio/springio-icon.svg" alt="spring" width="40" height="40"/> </a> <a href="https://travis-ci.org" target="_blank"> <img src="https://www.vectorlogo.zone/logos/travis-ci/travis-ci-icon.svg" alt="travisci" width="40" height="40"/> </a> <a href="https://www.typescriptlang.org/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/typescript/typescript-original.svg" alt="typescript" width="40" height="40"/> </a> <a href="https://unity.com/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/unity3d/unity3d-icon.svg" alt="unity" width="40" height="40"/> </a> <a href="https://www.vagrantup.com/" target="_blank"> <img src="https://www.vectorlogo.zone/logos/vagrantup/vagrantup-icon.svg" alt="vagrant" width="40" height="40"/> </a> <a href="https://vuejs.org/" target="_blank"> <img src="https://devicons.github.io/devicon/devicon.git/icons/vuejs/vuejs-original-wordmark.svg" alt="vuejs" width="40" height="40"/> </a> </p>
