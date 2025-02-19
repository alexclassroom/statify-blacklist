[![Build Status](https://github.com/stklcode/statify-blacklist/actions/workflows/test.yml/badge.svg?branch=stable)](https://github.com/stklcode/statify-blacklist/actions/workflows/test.yml?query=branch%3Astable)
[![Quality Gate Status](https://sonarcloud.io/api/project_badges/measure?project=stklcode%3Astatify-blacklist&metric=alert_status)](https://sonarcloud.io/dashboard?id=stklcode%3Astatify-blacklist)
[![Packagist Version](https://img.shields.io/packagist/v/stklcode/statify-blacklist.svg)](https://packagist.org/packages/stklcode/statify-blacklist)
[![License](https://img.shields.io/badge/license-GPL%20v2-blue.svg)](https://github.com/stklcode/statify-blacklist/blob/stable/LICENSE.md)

# Statify Filter #
* Contributors:      stklcode
* Requires at least: 4.7
* Tested up to:      6.5
* Requires PHP:      5.5
* Stable tag:        1.7.2
* License:           GPLv2 or later
* License URI:       https://www.gnu.org/licenses/gpl-2.0.html

## Description ##
A filter extension for the famous [Statify](https://wordpress.org/plugins/statify/) WordPress plugin.

This plugin adds customizable filters to Statify to allow blocking of referer spam or internal interactions.

### Features ##

#### Referer Filter ####
Add a list of domains (for simplicity only second-level, e.g. _example.com_ which blocks _everything.example.com_).

#### Target Filter ####
Add a list of target pages (e.g. _/test/page/_, _/?page_id=123_) that will be excluded from tracking.

#### IP Filter ####
Add a list of IP addresses or subnets (e.g. _192.0.2.123_, _198.51.100.0/24_, _2001:db8:a0b:12f0::/64_).

#### User Agent Filter ####
Add a list of (partial) user agent strings to exclude (e.g. _curl_, _my/bot_, _Firefox_).

#### CleanUp Database ####
Filters can be applied to data stored in database after modifying filter rules or for one-time clean-up.

#### Compatibility ####
This plugin requires Statify to be installed. The extension has been tested with Statify up to version 1.8
The plugin is capable of handling multisite installations.

### Support & Contributions ###
* If you experience any issues, use the [support forums](https://wordpress.org/support/plugin/statify-blacklist).
* Latest sources and development are handled on [GitHub](https://github.com/stklcode/statify-blacklist). You might contribute there or file an issue for code related bugs.
* If you want to translate this plugin you can do this on [WordPress Translate](https://translate.wordpress.org/projects/wp-plugins/statify-blacklist).

### Credits ###
* Author: Stefan Kalscheuer
* Special Thanks to [pluginkollektiv](https://pluginkollektiv.org/) for maintaining _Statify_

## Installation ##
* If you don’t know how to install a plugin for WordPress, [here’s how](https://wordpress.org/support/article/managing-plugins/#installing-plugins).
* Make sure _Statify_ plugin is installed and active
* Goto _Settings_ -> _Statify Filter_ to configure the plugin

### Requirements ###
* PHP 5.5 or above
* WordPress 4.7 or above
* _Statify_ plugin installed and activated (1.5 or above)

## Frequently Asked Questions ##

### What is blocked by default? ###
Nothing. By default, all filters are empty and disabled. They can and have to be filled by the blog administrator.

A default filter is not provided, as the plugin itself is totally neutral. If you want to filter out referer spam,
visitors from search engines, just "false" referrers from 301 redirects or you own IP address used for testing only depends on you.

### Does the filter effect user experience? ###
No. It only prevents _Statify_ from tracking, nothing more or less.

### Does live filtering impact performance? ###
Yes, but probably not noticeable. Checking a single referer string against a (usually small) list should be negligible compared to the total loading procedure.
If this still is an issue for you, consider deactivating the filter and only run the one-time-cleanup or activate the cron job.

### Is any personal data collected? ###
No. The privacy policy of _Statify_ is untouched. Data is only processed, not stored or exposed to anyone.

### Are regular expression filters possible? ###
Yes, it is. Just select regular expressions (case-sensitive or insensitive) as matching method instead of exact or keyword match.

### Why is IP and User Agent filtering only available as live filter? ###
As you might know, _Statify_ does not store any personal information, including IP addresses in the database.
Because of this, these filters can only be applied while processing the request and not afterwards.

### Can whole IP subnet be blocked? ###
Yes. The plugin features subnet filters using CIDR notation.
For example _198.51.100.0/24_ filters all sources from _198.51.100.1_ to _198.51.100.254_.
Same for IPv6 prefixes like _2001:db8:a0b:12f0::/64_.


## Screenshots ##
1. Statify Filter settings page

## Upgrade Notice ##

### 1.7.2 ###
This is a bugfix release to restore the manual cleanup function that was broken since 1.7.0.

### 1.7.1 ###
This is a service release with minor corrections. Recommended for all users. Tested up to 6.5.

### 1.7.0 ###
This is a service release with primarily internal rework. Tested up to 6.4 and PHP 8.3.


## Changelog

### 1.7.2 / 06.06.2024 ###
* Restore manual database cleanup functionality

### 1.7.1 / 24.03.2024 ###
* Fix HTML syntax for checkboxes on settings page
* Simplify some internal control structures
* Add plugin dependency to Statify
* Declared compatibility with WordPress 6.5

### 1.7.0 / 11.03.2024 ###
* Internal rework of plugin settings
* Make the IP filter list unique
* Fix options upgrade routine
* Declared compatibility with WordPress 6.4

### 1.6.3 / 14.08.2023 ###
* Minor internal code cleanup
* Declared compatibility with WordPress 6.3

### 1.6.2 / 25.02.2023 ###
* Always process IPv6 addresses lowercase
* Optimize internally used regular expression
* Minor adjustments to prevent warnings during user agent filtering with PHP 8.2

### 1.6.1 / 28.05.2021 ###
* Fix storage of user agent filter list (#28, props @BananaSquishee)

### 1.6.0 / 09.12.2020 ###

Plugin renamed to _Statify Filter_.

* Minor accessibility fixes on settings page
* Introduced new user agent filter (#20)
* Declared compatibility with WordPress 5.6

### 1.5.2 / 03.09.2020 ###
* Minor translation updates
* Declared compatibility with WordPress 5.5

### 1.5.1 / 20.05.2020 ###
* Fix initialization on AJAX calls for _Statify_ 1.7 compatibility (#22)

### 1.5.0 / 13.05.2020 ###
* Minimum required WordPress version is 4.7
* Removed `load_plugin_textdomain()` and `Domain Path` header
* Added automatic compatibility check for WP and PHP version (#17)
* Added keyword filter mode for referer blacklist (#15)
* Layout adjustments on settings page
* Regular expression filters are validated before saving (#13)

### 1.4.4 / 19.05.2018 ###
* Fix live filter chain when regular expressions are active (#12)

### 1.4.3 / 09.01.2018 ###
* Fix issues with multisite installation (#11)

### 1.4.2 / 12.11.2017 ###
* Minor code fixes

### 1.4.1 / 16.07.2017 ###
* Relicensed to GPLv2 or later
* Fix filter hook if referer is disabled (#9)
* Fix problem with faulty IPv6 netmask in IP blacklist
* Minor changes for WP Coding Standard
* Minimum required WordPress version is 4.4 (#10)

### 1.4.0 / 10.06.2017 ###
* IP blacklist implemented (#7)
* Target page blacklist implemented (#8)
* Internal configuration restructured (upgrade on plugin activation)
* Statify hook name changed to `statify__skip_tracking` (as of Statify 1.5.0)

### 1.3.1 / 09.12.2016 ###
* Continue filtering if no filter applies (#6)

### 1.3.0 / 17.10.2016 ###
* Regular expressions filtering implemented

### 1.2.1 / 10.10.2016 ###
* Fix live filter configuration check

### 1.2.0 / 29.08.2016 ###
* Switched from `in_array()` to faster `isset()` for referer checking
* Optional cron execution implemented

### 1.1.2 / 17.08.2016 ###
* Prepared for localization

### 1.1.1 / 16.08.2016 ###
* Some security fixes

### 1.1.0 / 15.08.2016 ###
* One-time execution on database

### 1.0.0 / 14.08.2016 ###
* First release
