# Visual Studio Code Wordpress Development Base
Containerized development in Visual Studio Code for Wordpress. Includes support for PhpUnit and XDebug.

## What's Inside
- Free (though Intellephense kinds asks for your support) VS Code Php extensions to make your life easier
- Docker / Dev Container configuration for Wordpress development
- XDebug automatic installation and configuration
- An example workspace with settings to ensure PHP Code Sniffer and Intellephense respect wordpress / xdebug library calls

## Setting Up
If you are developing Wordpress plugins, the only "real" configuration you need to do is replace {YOUR_PLUGIN_NAME_HERE} in devcontainer.json and docker-compose.yml.

If you are developing Wordpress themes, you will want to alter the volume in devcontainer.json and docker-compose.yml so that your theme directory syncs to the proper theme directory in your containerized wordpress (use the plugin example provided as a guide).

Remember to perform the five minute install before running any tests! (See "Visit Your Containerized Wordpress Website")

## Visit Your Containerized Wordpress Website
Simple use 0.0.0.0:8000/wp-admin to access your site. The IP will auto-route to the address of your docker container.

Perform the five-minute install as you typically would on any Wordpress website. 

If you are using PhpUnit to test your code, this is a pre-requisite since requests against Wordpress core are killed silently (die()) when the website is not installed.

## PhpUnit and XDebug
The included extensions will make PhpUnit testing rather simple if you are familiar. If you are not, the documentation and community offer many great resources to get started.

Using XDebug is as simple as:
1. Include a call to xdebug_connect_to_client() at the top of your PhpUnit bootstrap file. This will ensure every PhpUnit run attempts to connect to XDebug if XDebug is listening.
2. In your run configuration, choose "Listen for XDebug" - now XDebug is listening!
3. With the debug session active, set a breakpoint and run any PhpUnit test. Voila! Wordpress + PhpUnit + XDebug testing made simple.

## License for Use
This project is MIT licensed, which means you may use it in any free or proprietary works.
