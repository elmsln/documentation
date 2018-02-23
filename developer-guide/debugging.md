# Debugging ELMSLN {#debugging-elmsln}

## Some modules for debugging: {#some-modules-for-debugging}

* devel - Drupal developer module, useful for digging into objects / code development
* cis\_devel - Disables caching on all webservice calls as well as prints them to the screen so you can see what the response was. Useful when setting up new systems / complex calls.

## A buid failed / seems broken {#a-buid-failed-seems-broken}

Sometimes when working through integration issues or point release issues you could experience a drupal site in the network not being built correctly when requested. Here's steps to rebuild / give meaningful feedback to the development team / debug it yourself. Our test here will be called courses\_tt\_stuff as a new item in the courses stack called stuff - Go into the database for courses\_tt\_stuff and delete all tables - Go to ~/elmsln/config/stacks/courses/sites/courses/tt/stuff/settings.php and comment out the shared\_settings requirement at the bottom - go to http://courses.elmsln.local/stuff/install.php and run through the installer and see if it builds successfully / what the issue is \(usually seen during install\) - If there was no issue there, look for the job file`~/elmsln/config/jobs/courses.stuff.processed`and copy the drush commands in this file. - Append \(in another text editor like sublime\) @courses.stuff in after the drush command. Also place --y at the end of each command \(this is effectively what the job runner is doing\) - run these and see if there are any errors in the output

## Reversing commits

Working with Git can be a large challenge in almost every project. When submitting a Pull-Request \(PR\) it is best practice to try and submit the PR as one commit to be pushed. This way it is easier to see exactly what was worked on within the code. Sometimes an individual may make a mistake in pushing a commit that was incorrect. Through these steps you can reverse the commit and push in order to make your PR only have one accurrate commit.

WARNING: THIS PROCESS IS POTENTIALLY DESTRUCTIVE

```
Step 1: Get the ID of the 
commit
 you want 
to
reset
to
and
 run the following command...
git 
reset
 [ID]
Step 
2
: 
Commit
 changes
git 
commit
 -m 
'these are my changes'
 
Step 
3
: 
Force
 Push 
to
 origin 
master
 (i.e. your forked repository) 
git push 
--force origin master
```

These steps will allow you to smoosh multiple commits into one and make corrections to pushes in a PR that contained incorrect commits.

