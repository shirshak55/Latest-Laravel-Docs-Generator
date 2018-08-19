# Directory Structure {#structure}

- [Introduction](#structure-introduction)
- [The Root Directory](#structure-the-root-directory)
    - [The `app` Directory](#structure-the-root-app-directory)
    - [The `bootstrap` Directory](#structure-the-bootstrap-directory)
    - [The `config` Directory](#structure-the-config-directory)
    - [The `database` Directory](#structure-the-database-directory)
    - [The `public` Directory](#structure-the-public-directory)
    - [The `resources` Directory](#structure-the-resources-directory)
    - [The `routes` Directory](#structure-the-routes-directory)
    - [The `storage` Directory](#structure-the-storage-directory)
    - [The `tests` Directory](#structure-the-tests-directory)
    - [The `vendor` Directory](#structure-the-vendor-directory)
- [The App Directory](#structure-the-app-directory)
    - [The `Broadcasting` Directory](#structure-the-broadcasting-directory)
    - [The `Console` Directory](#structure-the-console-directory)
    - [The `Events` Directory](#structure-the-events-directory)
    - [The `Exceptions` Directory](#structure-the-exceptions-directory)
    - [The `Http` Directory](#structure-the-http-directory)
    - [The `Jobs` Directory](#structure-the-jobs-directory)
    - [The `Listeners` Directory](#structure-the-listeners-directory)
    - [The `Mail` Directory](#structure-the-mail-directory)
    - [The `Notifications` Directory](#structure-the-notifications-directory)
    - [The `Policies` Directory](#structure-the-policies-directory)
    - [The `Providers` Directory](#structure-the-providers-directory)
    - [The `Rules` Directory](#structure-the-rules-directory)

## Introduction {#structure-introduction}

The default Laravel application structure is intended to provide a great starting point for both large and small applications. Of course, you are free to organize your application however you like. Laravel imposes almost no restrictions on where any given class is located - as long as Composer can autoload the class.

#### Where Is The Models Directory?

When getting started with Laravel, many developers are confused by the lack of a `models` directory. However, the lack of such a directory is intentional. We find the word "models" ambiguous since it means many different things to many different people. Some developers refer to an application's "model" as the totality of all of its business logic, while others refer to "models" as classes that interact with a relational database.

For this reason, we choose to place Eloquent models in the `app` directory by default, and allow the developer to place them somewhere else if they choose.

## The Root Directory {#structure-the-root-directory}

#### The App Directory {#structure-the-root-app-directory}

The `app` directory, as you might expect, contains the core code of your application. We'll explore this directory in more detail soon; however, almost all of the classes in your application will be in this directory.

#### The Bootstrap Directory {#structure-the-bootstrap-directory}

The `bootstrap` directory contains the `app.php` file which bootstraps the framework. This directory also houses a `cache` directory which contains framework generated files for performance optimization such as the route and services cache files.

#### The Config Directory {#structure-the-config-directory}

The `config` directory, as the name implies, contains all of your application's configuration files. It's a great idea to read through all of these files and familiarize yourself with all of the options available to you.

#### The Database Directory {#structure-the-database-directory}

The `database` directory contains your database migrations, model factories, and seeds. If you wish, you may also use this directory to hold an SQLite database.

#### The Public Directory {#structure-the-public-directory}

The `public` directory contains the `index.php` file, which is the entry point for all requests entering your application and configures autoloading. This directory also houses your assets such as images, JavaScript, and CSS.

#### The Resources Directory {#structure-the-resources-directory}

The `resources` directory contains your views as well as your raw, un-compiled assets such as LESS, SASS, or JavaScript. This directory also houses all of your language files.

#### The Routes Directory {#structure-the-routes-directory}

The `routes` directory contains all of the route definitions for your application. By default, several route files are included with Laravel: `web.php`, `api.php`, `console.php` and `channels.php`.

The `web.php` file contains routes that the `RouteServiceProvider` places in the `web` middleware group, which provides session state, CSRF protection, and cookie encryption. If your application does not offer a stateless, RESTful API, all of your routes will most likely be defined in the `web.php` file.

The `api.php` file contains routes that the `RouteServiceProvider` places in the `api` middleware group, which provides rate limiting. These routes are intended to be stateless, so requests entering the application through these routes are intended to be authenticated via tokens and will not have access to session state.

The `console.php` file is where you may define all of your Closure based console commands. Each Closure is bound to a command instance allowing a simple approach to interacting with each command's IO methods. Even though this file does not define HTTP routes, it defines console based entry points (routes) into your application.

The `channels.php` file is where you may register all of the event broadcasting channels that your application supports.

#### The Storage Directory {#structure-the-storage-directory}

The `storage` directory contains your compiled Blade templates, file based sessions, file caches, and other files generated by the framework. This directory is segregated into `app`, `framework`, and `logs` directories. The `app` directory may be used to store any files generated by your application. The `framework` directory is used to store framework generated files and caches. Finally, the `logs` directory contains your application's log files.

The `storage/app/public` directory may be used to store user-generated files, such as profile avatars, that should be publicly accessible. You should create a symbolic link at `public/storage` which points to this directory. You may create the link using the `php artisan storage:link` command.

#### The Tests Directory {#structure-the-tests-directory}

The `tests` directory contains your automated tests. An example [PHPUnit](https://phpunit.de/) is provided out of the box. Each test class should be suffixed with the word `Test`. You may run your tests using the `phpunit` or `php vendor/bin/phpunit` commands.

#### The Vendor Directory {#structure-the-vendor-directory}

The `vendor` directory contains your [Composer](https://getcomposer.org) dependencies.

## The App Directory {#structure-the-app-directory}

The majority of your application is housed in the `app` directory. By default, this directory is namespaced under `App` and is autoloaded by Composer using the [PSR-4 autoloading standard](http://www.php-fig.org/psr/psr-4/).

The `app` directory contains a variety of additional directories such as `Console`, `Http`, and `Providers`. Think of the `Console` and `Http` directories as providing an API into the core of your application. The HTTP protocol and CLI are both mechanisms to interact with your application, but do not actually contain application logic. In other words, they are two ways of issuing commands to your application. The `Console` directory contains all of your Artisan commands, while the `Http` directory contains your controllers, middleware, and requests.

A variety of other directories will be generated inside the `app` directory as you use the `make` Artisan commands to generate classes. So, for example, the `app/Jobs` directory will not exist until you execute the `make:job` Artisan command to generate a job class.

> {tip} Many of the classes in the `app` directory can be generated by Artisan via commands. To review the available commands, run the `php artisan list make` command in your terminal.

#### The Broadcasting Directory {#structure-the-broadcasting-directory}

The `Broadcasting` directory contains all of the broadcast channel classes for your application. These classes are generated using the `make:channel` command. This directory does not exist by default, but will be created for you when you create your first channel. To learn more about channels, check out the documentation on [event broadcasting](#{{version}}/broadcasting).

#### The Console Directory {#structure-the-console-directory}

The `Console` directory contains all of the custom Artisan commands for your application. These commands may be generated using the `make:command` command. This directory also houses your console kernel, which is where your custom Artisan commands are registered and your [scheduled tasks](#{{version}}/scheduling) are defined.

#### The Events Directory {#structure-the-events-directory}

This directory does not exist by default, but will be created for you by the `event:generate` and `make:event` Artisan commands. The `Events` directory, as you might expect, houses [event classes](#{{version}}/events). Events may be used to alert other parts of your application that a given action has occurred, providing a great deal of flexibility and decoupling.

#### The Exceptions Directory {#structure-the-exceptions-directory}

The `Exceptions` directory contains your application's exception handler and is also a good place to place any exceptions thrown by your application. If you would like to customize how your exceptions are logged or rendered, you should modify the `Handler` class in this directory.

#### The Http Directory {#structure-the-http-directory}

The `Http` directory contains your controllers, middleware, and form requests. Almost all of the logic to handle requests entering your application will be placed in this directory.

#### The Jobs Directory {#structure-the-jobs-directory}

This directory does not exist by default, but will be created for you if you execute the `make:job` Artisan command. The `Jobs` directory houses the [queueable jobs](#{{version}}/queues) for your application. Jobs may be queued by your application or run synchronously within the current request lifecycle. Jobs that run synchronously during the current request are sometimes referred to as "commands" since they are an implementation of the [command pattern](https://en.wikipedia.org/wiki/Command_pattern).

#### The Listeners Directory {#structure-the-listeners-directory}

This directory does not exist by default, but will be created for you if you execute the `event:generate` or `make:listener` Artisan commands. The `Listeners` directory contains the classes that handle your [events](#{{version}}/events). Event listeners receive an event instance and perform logic in response to the event being fired. For example, a `UserRegistered` event might be handled by a `SendWelcomeEmail` listener.

#### The Mail Directory {#structure-the-mail-directory}

This directory does not exist by default, but will be created for you if you execute the `make:mail` Artisan command. The `Mail` directory contains all of your classes that represent emails sent by your application. Mail objects allow you to encapsulate all of the logic of building an email in a single, simple class that may be sent using the `Mail::send` method.

#### The Notifications Directory {#structure-the-notifications-directory}

This directory does not exist by default, but will be created for you if you execute the `make:notification` Artisan command. The `Notifications` directory contains all of the "transactional" notifications that are sent by your application, such as simple notifications about events that happen within your application. Laravel's notification features abstracts sending notifications over a variety of drivers such as email, Slack, SMS, or stored in a database.

#### The Policies Directory {#structure-the-policies-directory}

This directory does not exist by default, but will be created for you if you execute the `make:policy` Artisan command. The `Policies` directory contains the authorization policy classes for your application. Policies are used to determine if a user can perform a given action against a resource. For more information, check out the [authorization documentation](#{{version}}/authorization).

#### The Providers Directory {#structure-the-providers-directory}

The `Providers` directory contains all of the [service providers](#{{version}}/providers) for your application. Service providers bootstrap your application by binding services in the service container, registering events, or performing any other tasks to prepare your application for incoming requests.

In a fresh Laravel application, this directory will already contain several providers. You are free to add your own providers to this directory as needed.

#### The Rules Directory {#structure-the-rules-directory}

This directory does not exist by default, but will be created for you if you execute the `make:rule` Artisan command. The `Rules` directory contains the custom validation rule objects for your application. Rules are used to encapsulate complicated validation logic in a simple object. For more information, check out the [validation documentation](#{{version}}/validation).