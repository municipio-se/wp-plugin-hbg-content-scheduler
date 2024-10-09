# Content Scheduler

This plugin is an LTS version of the [Content Scheduler plugin v3.1.3](https://github.com/helsingborg-stad/content-scheduler/tree/3.1.3).

## Installation

1. Add the following to your `composer.json` file:
   ```json
   {
     "repositories": [
       {
         "type": "vcs",
         "url": "https://github.com/municipio-lts/wp-plugin-hbg-content-scheduler-2024.git",
         "only": [
           "municipio-lts/wp-plugin-hbg-content-scheduler-2024"
         ],
         "no-api": true
       },
     ]
   }
   ```
2. Install the package:
   ```bash
   composer require municipio-lts/wp-plugin-hbg-content-scheduler-2024:dev-main
   ```
3. Activate the plugin in WordPress.
