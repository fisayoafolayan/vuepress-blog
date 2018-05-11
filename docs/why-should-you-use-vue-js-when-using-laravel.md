---
title: Why should you use Vue.js when using Laravel
---
If you have used a recent Laravel version, you would notice it usually comes with Vue bundled in with other tools like bootstrap and jQuery. You would also notice in Laravel documentation that they gave a small introduction to using Vue components. Is this a sign that Laravel loves Vue?

In this guide, we are going to look at what Vue is, how it works with Laravel and why you should use it.


## Prerequisites
- Basic knowledge of PHP and Laravel
- Basic knowledge of JavaScript
- Have PHP setup on your local machine
- Have Composer installed on your local machine


## What is Vue.js?

Straight from the horse's mouth, “[Vue is a progressive framework for building user interfaces](https://vuejs.org/v2/guide/)”. Vue at its core is focused on the view layer only of an application, so integrating with other platforms or existing applications is really easy. You can also use Vue on its own to build sophisticated single page applications.


## How does Vue work?

If you have programmed for the web before the era of event-driven frontend JavaScript frameworks, you would understand there are considerable difficulties and inefficiencies that arise from trying to update the Document Object Model (DOM).

To update the DOM directly means you would have to take the page, make the change to a small part of it, then reload the entire DOM so the changes can take effect. If say you are watching a YouTube video and there is a new comment, the entire page would reload and your video would have to start afresh.

Vue tries to solve these challenges by utilizing a virtual DOM to manage the view a user sees. Vue essentially creates a copy of the DOM and stores it. When a change is made to any part of the DOM, it just updates only that section of the DOM without reloading the DOM. This means the comments would update without you even noticing it.

Vue provides reactive and composable view components. Vue responds to events and triggers changes on the DOM instantaneously. Its composable components can be selected and assembled in various combinations to satisfy whatever need arises. You can have components for everything and reuse them however you need.


## Why you should use Vue with Laravel

This is one question that you need to take your time to answer. It is important to understand what Vue has to offer and what that means for your work.

We are going to explore a few reasons why you should use Vue with Laravel.

**Everything happens on the frontend**

Applications on the internet today are event-driven. They are built to ensure users have a seamless experience, like they would if they used an application installed on their computer. 
Everything now happens on the frontend and users never have to reload a page again (thank you JavaScript).

**Reactive components makes for an excellent event driven app**

Vue lets you build a full-scale application that is event-driven and has all activity completely handle on the frontend. It also provides composable components that can be used however you wish. Given that it couples nicely with Laravel, you will only need to make a few trips to request data from your Laravel application and make UI changes by switching components without reloading the page.

You can trigger UI changes that are seamless with your Vue frontend, which in turn gives your users an amazing experience. It could be as simple as making a text on your page editable or swapping out an entire component to load up a video requested by a user without reloading the page.

Given Vue’s speed and performance, this happens very fast and smoothly without taking up so much of your computer resources.

**Building optimal complex frontend pages**

If you think of building an application with parts that need to update frequently, you have no other choice than to make the frontend run completely on JavaScript.

The challenge with vanilla JavaScript or jQuery or other JavaScript libraries that do not have a virtual DOM is that you quickly hit performance issues with the frequency of update increases or the volume of data to track for changes increases significantly. Changes to the DOM will gradually cease to be instantaneous and you begin to experience noticeable performance lags.

When you compose your application with Vue components, each component’s dependencies are automatically tracked during its render, so the system knows precisely which component actually needs to be updated when there is a change in data. This makes all updates to the DOM use minimal resources, thereby improving the overall application efficiency.

Vue is also compatible with state managers like Flux, Redux and Vuex which are excellent in managing data flow in complex applications. Vue’s utilization of a one-way data binding model also makes state management easier in complex applications.

**Single Page Application**

I would like to share a personal opinion - Single Page Applications are the greatest thing to happen to the internet in the last decade. It opens up applications to a wider audience of users than was possible before.

When you consider that many internet users outside of some parts of America and Europe have challenges getting on the internet, you begin to appreciate the role single page applications play in delivering a rich web experience to them.

Your entire application assets get loaded once (and most of it cached), all that your application does as the user engages with it is request data which typically requires low bandwidth to fulfill.

**Easy to learn and use**

Vue is easy to get into. It provides very few options for you as the developer and has a lot abstracted away. You feel like you are writing plain JavaScript when you use Vue and you can make a simple application with plain JavaScript and it remains valid in Vue.

Another great thing about Vue is that your valid HTML is also a valid Vue template. You can keep your CSS external or you can process it with JavaScript depending on your application needs. You can also take advantage of scoped styling, to apply style changes to a single component on the fly without the change affecting other components.

If you are familiar with JavaScript, you can build a non-trivial application with Vue after just one day of reading the [documentation](https://vuejs.org/v2/guide/).


## Basic Vue usage with Laravel

Vue integrates nicely with Laravel. You can create Vue components and use them like you would use regular HTML tags inside your blade file. You can pass props to the component from the output generated when your blade file renders.

To try it out, create a new Laravel installation using the Laravel installer:

    > $ laravel new vueapp

If you do not have the Laravel installer, run the following command to get it:

    > $ composer global require "laravel/installer"

When this is done, change your working directory into your new Laravel installation:

    $ cd vueapp

Install Vue and other JavaScript libraries your application needs to run:

    $ npm install

Setup your application to reload when you make changes to your `js` assets:

    $ npm run watch


> If you like seeing your changes as you make them, especially since you are learning, then you should definitely `run watch` to watch the applications.

Now, open another terminal instance and start the Laravel application server:

    $ php artisan serve


## Creating your first Vue Component

Making a Vue component is easy. If you open the `resources/assets/js/app.js` file, you would see that Vue has already been imported and a sample Vue component created.

You can create your Vue components in many ways. For this guide, we are going to create each component in a separate file in `resources/assets/js/components` directory to keep things neater. All Vue template files end in `.vue` extension, so name everyone you create correctly.

Now, create a new file `Welcome.vue` inside the components directory, and add the following to it:

    <template>
        <div class="flex-center position-ref full-height">
            <div class="content">
                <div class="title m-b-md">
                    Welcome to Vue.js on Laravel
                </div>
                <div class="links">
                    <a href="https://laravel.com/docs">View Laravel Docs</a>
                    <a href="https://vuejs.org/v2/guide/">View Vue Docs</a>
                    <a href="https://laracasts.com">Watch Videos</a>
                </div>
            </div>
        </div>
    </template>
    <script>
        export default {}
    </script>
    <style scoped>
        html, body {
            background-color: #fff;
            color: #636b6f;
            font-family: 'Raleway', sans-serif;
            font-weight: 100;
            height: 100vh;
            margin: 0;
        }
    
        .full-height {
            height: 100vh;
        }
    
        .flex-center {
            align-items: center;
            display: flex;
            justify-content: center;
        }
    
        .position-ref {
            position: relative;
        }
    
        .top-right {
            position: absolute;
            right: 10px;
            top: 18px;
        }
    
        .content {
            text-align: center;
        }
    
        .title {
            font-size: 84px;
        }
    
        .links > a {
            color: #636b6f;
            padding: 0 25px;
            font-size: 12px;
            font-weight: 600;
            letter-spacing: .1rem;
            text-decoration: none;
            text-transform: uppercase;
        }
    
        .m-b-md {
            margin-bottom: 30px;
        }
    </style>
    


<template> holds the HTML template for the page we are making. If we do not enclose our HTML in the template tag, we would have to specify what the template is, either by linking to an external file or by assigning the entire template content as a variable to Vue.

If we have an external file called `MyTemplate.vue`, we would need to grab more JavaScript libraries to help us parse and use the external template. This is enough reason not to use external templates.

If you look at the contents enclosed by the `<template>` tag, you would see that it is just plain HTML markup. The most important part is that this is valid Vue template as well. You would not need to learn new tricks to get started.

We have the `script` section on the page where we define the entire logic that controls the page. We do not need to define or declare anything to use Vue templates, so we leave it empty.
The last part is the `style` section. We added a parameter to it - `scoped` simply to tell Vue “Apply these styles to this component alone. Do not make it available to any other component”. 

This means that the changes we made to existing styles and the new styles we added will not be visible outside of this component.


## Using the component in your blade file

We have made our first Vue component (I know, it is that easy). To use it in the `welcome.blade.php` file, we would need to make Vue aware that it exist and give it a name Vue would label it with.

Open the `resources/assets/js/app.js` file and edit it to the following:

    require('./bootstrap');
    
    window.Vue = require('vue');
    
    Vue.component('welcome', require('./components/Welcome.vue'));
    
    const app = new Vue({
        el: '#app'
    });

Next, use the Vue component inside of your `resources/views/welcome.blade.php` file:


    [...]
            <meta name="viewport" content="width=device-width, initial-scale=1">
            <meta name="csrf-token" content="{{ csrf_token() }}">
    
            <title>Laravel</title>
    
    [...]
        <body>
            <div id="app">
                <welcome></welcome>
            </div>
            <script type="text/javascript" src="js/app.js"></script>
        </body>
    [...]


> Make sure to edit the file accordingly and include the script tag in it so that your Vue component can be visible on the page

If you set your application to watch for changes to your `js` assets, then you should see that it already built the entire application and would output `compiled successfully in XXXms`.
Now, visit `http://localhost:8000` on your browser to see your application.

![It should look like this](https://d2mxuefqeaa7sj.cloudfront.net/s_F0ECF1C019FD9A0954C5AE0DB595AD2F48B99F1D437215268682415602B03970_1523709620925_Screen+Shot+2018-04-14+at+1.39.54+PM.png)

## Passing data to the component

Let us assume we want to output the details of the developer of the application, and we cannot know it because only the application can give that detail. We can easily pass the details to the component and have it display it when it renders.

Next, we will pass a title to the component and see what it looks like. Open the welcome blade file located at  `resources/views/welcome.blade.php` and add the following:


    [...]
    <div id="app">
       <welcome :title="'This cool app'"></welcome>
    </div>
    [...]

We just passed data into the component by binding the data to a variable we would receive in the component as a property (prop).

Then, open the `Welcome.vue` file located at `resources/assets/js/components/Welcome.vue` and add the following to it:


    <template>
                [...]
                <div class="title m-b-md">
                    {{title}}
                </div>
    
                [...]
    </template>
    
    <script>
        export default {
            props : ['title']
        }
    </script>

From the above code, you will see we replaced the `Welcome to Vue.js on Laravel` with `{{title}}`. This is the way to output the content of a variable in your Vue template, just like with Laravel blade template.

In the script section, we received a prop using `props : ['title']` and the prop we received is what we displayed.

![Your app should look like this now](https://d2mxuefqeaa7sj.cloudfront.net/s_F0ECF1C019FD9A0954C5AE0DB595AD2F48B99F1D437215268682415602B03970_1523710528693_Screen+Shot+2018-04-14+at+1.55.13+PM.png)


Next, we will pass the title from our application server. Open the `routes/web.php` file and edit as follows:


    [...]
    Route::get('/', function () {
        return view('welcome',
            [
                'title' => "An even cooler way to do the title"
            ]
        );
    });

Then, edit the `welcome.blade.php` file as follows:


    [...]
    <div id="app">
       <welcome :title="'{{$title}}'"></welcome>
    </div>
    [...]

We just output the content `title` from the server and pass it directly to the component.

![It should look like this now](https://d2mxuefqeaa7sj.cloudfront.net/s_F0ECF1C019FD9A0954C5AE0DB595AD2F48B99F1D437215268682415602B03970_1523710893288_Screen+Shot+2018-04-14+at+2.01.16+PM.png)


Next, we will add a second page to our application and make a second component. Create a new file `resources/assets/js/components/Page.vue` and add the following to it:


    <template>
        <div class="flex-center position-ref full-height">
            <div class="content">
                <div class="title m-b-md">
                    {{title}}
                </div>
    
                <div class="links">
                    <span class="subtitle">Name : {{author.name}}</span><br/>
                    <span class="subtitle">Role : {{author.role}}</span><br/>
                    <span class="subtitle">Code : {{author.code}}</span><br/>
                </div>
            </div>
        </div>
    </template>
    
    <script>
        export default {
            props : ['title', 'author']
        }
    </script>
    <style scoped>
        html, body {
            background-color: #fff;
            color: #939b9f;
            font-family: 'Raleway', sans-serif;
            font-weight: 100;
            height: 100vh;
            margin: 0;
        }
        .title {
            font-size: 60px;
        }
        .subtitle {
            font-size: 20px;
        }
        .full-height {
            height: 100vh;
        }
    
        .flex-center {
            align-items: center;
            display: flex;
            justify-content: center;
        }
        .position-ref {
            position: relative;
        }
    
        .top-right {
            position: absolute;
            right: 10px;
            top: 18px;
        }
        .content {
            text-align: center;
        }
        .m-b-md {
            margin-bottom: 30px;
        }
    </style>

Like the first page, we received a second prop that is a `json object` that contains author information. We have rendered the page with the Author information

Let us make Vue aware of the new component we just created. Open `resources/assets/js/app.js` file and add the following:


    [...]
    
    Vue.component('welcome', require('./components/Welcome.vue'));
    Vue.component('page', require('./components/Page.vue'));
    
    [...]

Now, create a new file `resources/views/page.blade.php` and add the following to it:


    <!doctype html>
    <html lang="{{ app()->getLocale() }}">
        <head>
            <meta charset="utf-8">
            <meta http-equiv="X-UA-Compatible" content="IE=edge">
            <meta name="viewport" content="width=device-width, initial-scale=1">
            <meta name="csrf-token" content="{{ csrf_token() }}">
    
            <title>Page</title>
    
            <link href="https://fonts.googleapis.com/css?family=Raleway:100,600" rel="stylesheet" type="text/css">
        </head>
        <body>
            <div id="app">
                <page :title="'{{$title}}'" :author="{{$author}}"></page>
            </div>
            <script type="text/javascript" src="js/app.js"></script>
        </body>
    </html>

Finally, open `routes/web.php` and add a route for loading the page at the end of the file:


    [...]
    
    Route::get('/page', function () {
        return view('page',
            [
                'title' => "Page 2 - A little about the Author",
                'author' => json_encode([
                        "name" => "Fisayo Afolayan",
                        "role" => "Software Enginner",
                        "code" => "Always keeping it clean"
                ])
            ]
        );
    });

To view our new route, visit http://127.0.0.1:8000/page on your browser.

![This is how it should look.](https://d2mxuefqeaa7sj.cloudfront.net/s_D1E5B54363DC37D40F0D7B04CF1A4A14F4DA6E7298C2EB5E1C1986D32E08D9FF_1524387039955_page2.png)

## Building the entire frontend in Vue

So far, we have looked at one way to use Vue and Laravel. When we started this article, we talked about everything running on the frontend and users not having to reload anything. We are going to see how to build a Single Page App (SPA) a user would only have to load once and fetch everything by making API calls.


## Installing vue router

Vue router is the Vue tool for building navigation on the frontend application. It would allow you navigate an SPA like you would a regular application. To install vue router, run the following command on your terminal:


    $ npm install vue-router


> Exit the `watch` process we initiated earlier using `ctrl + c`. We would start watching for changes again after vue router is installed.


## Setting up the routes

Now that vue router is installed, we need to define the routes of the application. This will be the guide for switching between the components we have made.

Create a new file `resources/assets/js/vueapp.js` and edit it as follows:


    import Vue from 'vue'
    import VueRouter from 'vue-router'
    
    Vue.use(VueRouter)
    
    import App from './components/App'
    import Welcome from './components/Welcome'
    import Page from './components/Page'
    
    const router = new VueRouter({
        mode: 'history',
        routes: [
            {
                path: '/home',
                name: 'welcome',
                component: Welcome,
                props: { title: "This is the SPA home" }
            },
            {
                path: '/spa-page',
                name: 'page',
                component: Page,
                props: { 
                    title: "This is the SPA Second Page",
                    author : {
                        name : "Fisayo Afolayan",
                        role : "Software Engineer",
                        code : "Always keep it clean"
                    }
                }
            },    
        ],
    })
    const app = new Vue({
        el: '#app',
        components: { App },
        router,
    });
## What sorcery was that?

You are already familiar with what `import` does in JavaScript and how to do it. In the above code, we have imported everything we want to use for our SPA.

`Vue.use(VueRouter)` - telling vue to use the router package, so it can access all the functionalities of the router and interpret the route we are about to create

`const router = new VueRouter` - defines the routes our application is going to have. Through the application, the routes definitions will not be changed, so we have to make them constant.

`mode` - this is the mode we want the router to use in managing the navigation of the application. The default mode is `hash mode` which uses the URL hash to simulate a full URL so that the page won't be reloaded when the URL changes. The other is `history mode`, which leverages the `history.pushState` API to achieve URL navigation without a page reload.

`routes` - the routes we would like our application to have.
`path` - the url to access this route
`name` - the name we would like to give this route (useful when navigating in-component)
`component` - the component we want loaded when this route is visited.
`props` - we are passing props to the component as we mount them

    


The last part creates the Vue application and defines the parent component the router will use as it’s entry point. In our case, we used the `App` component as the parent component.


## Setting up the parent container

We need to create the `App` component in `resources/assets/js/components` directory. Add the following to it:

    <template>
        <div>
                <nav class="navbar navbar-expand-md navbar-light navbar-laravel">
                <div class="container">
                    <ul class="navbar-nav">
                        <router-link :to="{ name: 'welcome' }" class="nav-link">Home</router-link>
                        <router-link :to="{ name: 'page' }" class="nav-link" >Spa-Page</router-link>
                    </ul>
                </div>
            </nav>
            <main>
                <router-view></router-view>
            </main>
        </div>
    </template>
    <script>
        export default {}
    </script>
                resources/assets/js/components/App.vue
                

Vue will use `<router-view>` as the outlet for any component we visit as its URL. The `<router-link>` is responsible for navigating between components. If you notice, we are assigning the name we gave the routes to the `to` attribute of the route.


## Mounting our components

We need to do a few things before we can use our SPA. We need to first set the `vueapp.js` file to be built. We need to also define the blade file our SPA will use as it’s entry point. Finally, we need to define the route that w enable us access the SPA.

To set `vueapp.js` to be built, edit the `webpack.mix.js` file as follows:


    [...]
    
    mix.js('resources/assets/js/app.js', 'public/js')
       .js('resources/assets/js/vueapp.js', 'public/js')
       .sass('resources/assets/sass/app.scss', 'public/css');

Now, create the file `vueapp.blade.php` inside the `resources/views` directory. Edit it as follows:


    <!doctype html>
    <html lang="{{ app()->getLocale() }}">
        <head>
            <meta charset="utf-8">
            <meta http-equiv="X-UA-Compatible" content="IE=edge">
            <meta name="viewport" content="width=device-width, initial-scale=1">
            <meta name="csrf-token" content="{{ csrf_token() }}">
    
            <title>Outlet for SPA</title>
    
            <link href="https://fonts.googleapis.com/css?family=Raleway:100,600" rel="stylesheet" type="text/css">
            <link rel="stylesheet" type="text/css" href="css/app.css">
        </head>
        <body>
            <div id="app">
                <app></app>
            </div>
            <script type="text/javascript" src="js/vueapp.js"></script>
        </body>
    </html>

Then define the route in `routes/web.php` file as follows:


    [...]
    Route::get('/{any}', function(){
            return view('vueapp');
    })->where('any', '.*');

Now, build the application by running the following command:


    $ npm run prod

Visit the application on `http://127.0.0.1:8000/home`


![](https://d2mxuefqeaa7sj.cloudfront.net/s_D1E5B54363DC37D40F0D7B04CF1A4A14F4DA6E7298C2EB5E1C1986D32E08D9FF_1524388697310_full_task.gif)

## Conclusion

In this guide we have looked at what Vue.js can do and how it can work with Laravel. We explored some reasons why you should consider using Vue with Laravel. We also looked at how to use Vue with Laravel, including making a single page application that will run on Laravel.

There is a whole lot you can build with Vue and Laravel. Only the surface was scratched in this article to give you an idea of what is obtainable. Vue is very easy to use and works well with Laravel. You should read the [documentation](https://vuejs.org/v2/guide/) to learn of the cool thing you can build with it.

The source code to the application in this article is available on [GitHub](https://github.com/fisayoafolayan/laravel-vue).

