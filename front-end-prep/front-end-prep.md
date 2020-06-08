# UI Dev:

    Angularjs = MVC
    React = Component Based Architecture
    Angular = 

    TypeScript vs Javascript = 

        JavaScript is a scripting language which helps you create interactive web pages.

        Typescript is a modern age Javascript development language. It is a statically compiled language to write clear and simple Javascript code. It can be run on Node js or any browser which supports ECMAScript 3 or newer versions.

    Component Based Architecture = Has reusability of components. A component is a software object, intended to interact with other components, encapsulating certain functionality or a set of functionalities.

    MVC = User uses controller which modifies models and updates the view
          Advantage of separating MVC is cleaner, more maintanable and sustainable code

          User uses Controller, which manipulates the Model, which updates the View, that the user sees

    What is the DOM? 

    Document Object Model is an interface to web pages. It is essentially an API to the page, allowing programs to read and manipulate the page’s content, structure, and styles.

    MVVM =  Model-View-ViewModel is a structural design pattern. 

            Model holds application data. 
            View display to user. 
            ViewModel transform model data into values that can be displayed to View

    Electron = a popular framework that makes it easy to build desktop apps for macOS, Linux or Windows using familiar web technologies (HTML, JavaScript and CSS).

    Nodejs = The runtime environment for javascript. Equivalent to JRE to java. It has everything required to run a javascript program.

    npm = Default package manager for nodejs

    Server side 
        The “server” is a web application server at a remote location. A server side or back-end language runs its scripts before the HTML is loaded, not after. PHP is one of the most popular, as well as Ruby on Rails, ASP.NET and many others. They are called server side languages because their scripts are run not on your computer, but on the server which hosts the website and sends down the HTML code.

    Client side 
        The “client” is a web browser. Client side development is done almost exclusively in JavaScript. This is, of course, in addition to basic HTML and CSS code. The reason JavaScript is called a client side language is because it runs scripts on your computer after you’ve loaded a web page.

# Web Applications stacks:
    LAMP
        Linux               (OS)
        Apache              (Webserver)
        MySQL               (Data persistence)
        PHP                 (Programming language)

        Pros: Lots of documentation. Years being used, very stable. Easy to learn.

        Variations:
            LAMP (with Perl or Python instead of PHP)
            LAMP (with MongoDB instead of MySQL)
            WAMP (Windows as OS)
            MAMP (Mac OS X as OS)
            XAMPP (Any OS + Perl or PHP + FTP Server)
            LAPP (PostgreSQL as database)

    MEAN
        MongoDB             (Data persistence)
        Express.js          (server-side application framework) Back-end web application framework running on top of Node.js
        Angular.js          (client-side application framework)
        Node.js             (server-side environment)

        Pros: Pure javascript. Ability to easily build mobile or desktop apps, for example with Ionic.

        Variations:
            MERN (React instead of Angular)
            MEEN (Ember.js instead of Angular)

    Other Stacks:

        WISA            Windows Server / IIS / Microsoft SQL Server / ASP.net
        Ruby Stack      Ruby/Ruby on Rails/RVM (Ruby Virtual Machine) / SQLite
        Java+Spring     Preferred by large enterprises and shied by indie developers for its complexity, 
                        Spring offers an entire full-stack framework written in Java.
        Django Stack    Python / Django / Apache / MySQL


Internet 
    end to end principle

    TCP/UDP

    SSL

    HTTP 

    NAT

Sprinboot
    HTTP verbs
        200 successful
        401 unathorized
        404 not found
    CRUD
    REST 
        GET
        PUT 
        PATCH 
        POST
        DELETE
    SOAP

    Spring MVC vs Springboot

Jenkins
    L
    Unit testing:
    Integration testing:
    System testing:
    Acceptance testing:

Database:
    Sql
        Has schemas
        MySQL
    Nosql: 

        MongoDB: schemaless data persistence and is faster than MySQL if you have a lot of read requests

    Schema: Design or list of attributes and instructions that tells the database how the data is organized and how the components are related.

        Example:
            Name-Last   Name-Middle Name-First  Name-Nick   Phone-AreaCD    Phone-Number
            Aden        K.          Samson      (Sam)       (555)           234-1221
            Joe         Brown                               (555)           234-1233

        Physical Schema − This schema pertains to the actual storage of data and its form of storage like files, indices, etc. It defines how the data will be stored in a secondary storage.

        Logical Schema − This schema defines all the logical constraints that need to be applied on the data stored. It defines tables, views, and integrity constraints.



This sections is usually ask for senior positions(10+ years)
#################################################### DESIGN ####################################################

Questions explaining design of systems/apps 
If you were to build a social networking website from scratch, how would you design the system?

https://www.hiredintech.com/classrooms/system-design/lesson/52
https://www.youtube.com/playlist?list=PLA8lYuzFlBqAy6dkZHj5VxUAaqr4vwrka
https://www.geeksforgeeks.org/design-scalable-system-like-instagram/
https://hackernoon.com/how-not-to-design-netflix-in-your-45-minute-system-design-interview-64953391a054
https://gist.github.com/vasanthk/485d1bottom5737e8e72759f
https://github.com/donnemartin/system-design-primer

System Design Basics
Key Characteristics of Distributed Systems
Load Balancing
Caching
Data Partitioning
Indexes
Proxies
Redundancy and Replication
SQL vs. NoSQL
CAP Theorem
Consistent Hashing
Long-Polling vs WebSockets vs Server-Sent Events

Design a URL Shortening service like TinyURL
Design Pastebin
Design Instagram
Design Dropbox or Google Drive
Design Facebook Messenger
Design Twitter
Design Youtube or Netflix
Design Typeahead Suggestion
Design an API Rate Limiter
Design Twitter Search
Design a Web Crawler or Type-Ahead (search engine related services)
Design Facebook’s Newsfeed
Design Quora, Reddit or Hackernews
Design Yelp or Nearby Friends
Design Uber backend
Design Ticketmaster 
playstore app
instagram
web browser
countdown app
swiggy rider app
Booking.com booking listings screen

