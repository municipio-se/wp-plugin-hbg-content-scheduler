# HBG Content Scheduler

This plugin is a [Municipio LTS](https://github.com/municipio-se/municipio-lts)
version of Helsingborg stad's
[Content Scheduler plugin](https://github.com/helsingborg-stad/content-scheduler).

## Fork Base

This LTS fork is based on upstream tag
[`3.1.3`](https://github.com/helsingborg-stad/content-scheduler/tree/3.1.3),
commit
[`2b12bf4`](https://github.com/helsingborg-stad/content-scheduler/commit/2b12bf43e00487e5fe0ae432e8d7156f71bd4e2b).

## Changes in this Fork

This LTS version fixes several critical issues that affected core functionality. Most importantly, it resolves a fatal error that occurred when creating posts, ensuring the plugin works reliably with post creation workflows.

Scheduling functionality has been corrected with proper timezone handling and the use of Unix timestamps instead of incorrect timestamp formats. A significant bug where posts were always being trashed instead of properly scheduled has been fixed. The plugin now properly manages scheduled tasks by ensuring old unpublish cron jobs are removed when no longer needed.

Additional improvements include fixes to CSS styling, vendor autoload configuration, and updated package dependencies for better long-term stability.

## Installation

1. Install the package:
   ```bash
   composer require municipio/wp-plugin-hbg-content-scheduler
   ```
2. Activate the plugin in WordPress.
