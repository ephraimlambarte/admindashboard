## Admin Panel Template
    This is a template using vuespa with laravel file structure

## Requirements
    -vue/cli
    -composer
    -npm
    -laravel 5.5 and above

## Setup
    -create laravel project using composer
    -cd to the project created
    -run "npm install"
    -run "npm install vue-router"
    -run "npm install bootstrap popper.js jquery --save-dev"
    -copy this code to resources/assets/js/app.js
    ```
        import Vue from 'vue'
        import VueRouter from 'vue-router'

        Vue.use(VueRouter)

        import App from './views/App'
        <!-- import components here -->

        const router = new VueRouter({
            mode: 'history',
            routes: [
                
                <!-- 
                include components for views here
                ex:
                {
                    path: '/',
                    name: 'home',
                    component: Home
                }, -->
            ],
        });

        const app = new Vue({
            el: '#app',
            components: { App },
            router,
        });
    ```
    -create App.vue file on resources/assets/js/views/
    <!-- Note: this directory is not required, you can have your own directory structure -->
    -copy and paste this template to App.vue
    ```
        <template>
            <div>
                <h1>Vue Router Demo App</h1>

                <p>
                    <!-- include router names here. ex: -->
                    <router-link :to="{ name: 'home' }">Home</router-link>
                </p>

                <div class="container">
                    <router-view></router-view>
                </div>
            </div>
        </template>
        <script>
            export default {}
        </script>
    ```
    -replace the code in routes/web.php
    ```
        Route::get('/{any}', 'SpaController@index')->where('any', '.*');
    ```
    -create a controller for the route made:
        -run this command "php artisan make:controller SpaController"
    -open SpaController under app/Http/Controllers/SpaController.php
    copy and paste this function to SpaController.php: 
    ```
 
        public function index()
        {
            return view('spa');
        }

    ```
    -lastly create resources/views/spa.blade.php and paste this code
    ```
    
    <html lang="en">
        <head>
            <meta charset="UTF-8">
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <meta http-equiv="X-UA-Compatible" content="ie=edge">
            <title>Vue SPA Demo</title>
        </head>
        <body>
            <div id="app">
                <app></app>
            </div>

            <script src="{{ mix('js/app.js') }}"></script>
        </body>
    </html>
    ```

## Running the application 
    - npm run watch
    - php artisan serve

## CREDITS
    All of the designs here are copied and integrated from this free template: https://bootstrapious.com/p/admin-template