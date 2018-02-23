# Custom Tools {#custom-tools}

There are several ways using developer hooks to get custom tools to show up in the network flyout / system wide. The easiest way is to add your own custom topology files. A topology file tells elmsln about your custom thing you made or external system you want to provide links to.

create a topology file in`/var/www/elmsln/config/shared/drupal-7.x/tools/{name}/{name}.topology`. Here's an example topology file:

```
default_title=
"Custom Tool"
type=
"custom"
subdomain=
"custom"
group=
"Network"
icon_library=
"elmsln"
show_in_network=
"1"
weight=
"11"
icon=
"dino"
color=
"light-blue"
color_dark=
"darken-3"
color_light=
"lighten-3"
color_text=
"accessible-light-blue-text"
color_outline=
"light-blue-outline"
color_code=
"#03a9f4"
custom=
"1"
address=
"http://legacylms.edu"
```

You can create any number of topology files and have them lazy loaded into the elmsln keychain registry. This visually shows up in the Network flyout but also allows you to utilize elmsln's ability to simplify call structures to other systems \(see`_cis_connector_request()`\).

Common developer questions are being added here as a catch all currently. If you have any[please check the issue queue](https://github.com/btopro/elmsln/issues)or[create a new issue](https://github.com/btopro/elmsln/issues/new)and the community will get back to you asap.

## From the issue queue {#from-the-issue-queue}

* [Adding new modules](https://github.com/btopro/elmsln/issues/49)
* [Unable to access added services](https://github.com/btopro/elmsln/issues/48)
* [What is a course?](https://github.com/btopro/elmsln/wiki/Information-Architecture)
* [What am I looking at after a new installation of ELMSLN?](https://github.com/btopro/elmsln/issues/46)
* [CIS - where is the campus list being pulled from?](https://github.com/btopro/elmsln/issues/64)

## From emails {#from-emails}

### How can I get the current 'section\_id' of a user in code? {#how-can-i-get-the-current-section_id-of-a-user-in-code}

There's a function called`_cis_connector_section_context()`which acts similar to the og\_context to provide an ID associated with the user based on what they are currently viewing. This lets you know a user is in section "ABC-123" as opposed to another one. This information can be used to act on showing different data based on section in a course or pulling additional details from CIS / other systems that is relevant to that group.

### We're moving hosting from where we started building, what urls need updated {#were-moving-hosting-from-where-we-started-building-what-urls-need-updated}

There's 3 places addresses get hard-coded into ELMSLN to keep the web services transactions happy. The first is at time of deployment when the registry keychain is created. This can be found in`/var/www/elmsln/config/shared/drupal-7.x/modules/_elmsln_scripted`'s .module file and has links to all the services in the network.

After that, you'll want to issue`drush @online cis-sync-reg`which will sync the database with some of these values that it stores locally for caching purposes. Lastly, any services that were created \(like courses.elmsln.dev/sing100\) will need to have their settings.php files modified to reflect the new domain. This is stored in the`$base_url`variable. Another strategy is to edit the file in`/var/www/elmsln/config/shared/drupal-7.x/settings/shared_settings.php`to do an overwrite of the different urls if you are passing them around a lot.

### When I look at the System Setup, it looks like you can't change the method of access once it's been created. Is that correct? {#when-i-look-at-the-system-setup-it-looks-like-you-cant-change-the-method-of-access-once-its-been-created-is-that-correct}

If you go into the course in question you can change the permissions to match what you're looking for. These routines are for when the systems are stamped out initially, it's in the roadmap to have jobs retroactively update the systems to keep in sync with the level of access set in CIS. This is a known issue and is marked in https://github.com/btopro/elmsln/issues/71

## Should I upgrade modules?

Anything that’s included in the enclosed core directory should not be updated outside of the schedule of updating versions of the code from the github repository \(unless you know what you are doing\). There are a few projects patched so the best way to get projects upgraded to the latest version is to test it in a vagrant instance, report on it in an issue queue, and then let the ELMSLN community vet the module / theme upgrade. Once this has happened then it will be rolled into the final package.

This is to ensure that all sites function properly after upgrades. This package will be updated on versions once they are tested, any modules that you install in your config directory is on you to manage. The general rule in Drupal is don’t hack core and the same is true with ELMSLN, don’t hack ELMSLN core; apply all your changes you want inside the config directory.

There is a drush edl function that can be used to place modules, drush plugins, themes, profiles, and copies of core in the correct location in the elmsln setup. If you are doing this though you probably are an active developer in the community \(so that's awesome\).

## Where can I add custom Drupal modules / code?

All changes should be made inside the config directory in a location that aligns with its counterpart in the core directory. For example, to add a new module for use in all sites, you’ll want to place it in elmsln/config/shared/drupal-7.x/modules. This is the same area for themes and libraries.

There’s also a settings/shared\_settings.php file that has settings you want applied to all sites by default. This is where your environmental staging overrides can go, or you can switch the cache bins used by default. The version that ships with this has APC and file cache support automatically setup and tuned \(but disabled\).

Also make sure you never place an upgraded module in a different location from its default \(such as updating views module by placing it in your config directory\). This will effectively WSOD / brick your site until you run drush rr against the sites that bricked. If you've run the elmsln-install.sh script included in this package, you'll have drush rr. You can repair this relationship then with drush @courses.bricked rr --y \(for example\).

## Where should I point these domains you gave me?

The domains directory is structured in the optimal way for managing sites. The domains directory is ignored below the initial directories inside of it, meaning that your sites that get written here automatically won’t be pushed through git or updated. If you remove directories or change the way sites are managed in anyway inside this location, you’ll need to add that area to your .gitignore \(or stop using the github version\).

You can use this as a starting point and self manage from there but sticking as closely as possible to the structure of ELMSLN will help ensure upgrades down the road take correctly.

