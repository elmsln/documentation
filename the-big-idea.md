# The big idea

Innovation is in chasing the unknown. It's not doing what scales, it's doing what's right now so that we can later bring it to scale. ELMS:LN is based on the idea that many innovations in the education space follow a pattern. To this end, the platform sets in motion a pattern of design that helps produce sustainable innovation.

## What is sustainable innovation?

Let's look at an example. An instructor has a need for a twitter data mining application. It currently doesn't exist, and they need to mash up data going on in the course of instruction with data from other sources. So a project team assembles, they build a prototype, and then do a conference submission. People sit and watch and say "wow, that's so cool". The talk ends. The course ends. The innovation is shelved, and the next one is picked up.

End of story right?

This is the pattern that's been followed in educational innovations for decades in education. Meet cool needs in a classroom, present on it, rinse and repeat. But what if I wanted access to that innovation? What if you did? Perhaps it's open source and we can figure it out from there \(or not\). Perhaps it was hard coded just to get the job done \(we all have too much to do too quickly\). What if we were able to capture and deploy that innovation in a sustainable manner?

## Ways ELMS:LN makes innovation sustainable:

1. There is a common pattern to system type. Things are either authorities \(single point\) or services \(deployed per course\)

2. All innovations have the same guts: Consistent user interfaces, something called a "course", a "roster", profile pictures, accounts, all that jazz. So we routinize all that stuff. All the bricks that are needed to work on an innovation.

3. We follow a simple domain name based pattern. Meaning each new innovation of a specific scope will live at a new domain. bigidea2.elmsln.psu.edu kind of logic.

4. We will use web components to build reusable component architecture making front-end assets transportable

5. Drupal based innovations \(while not required\) have deployment automation built in a manner that can be captured and rolled out for others easily. This allows some course technologies to diverge from intention for a short period of time \(experimentation\) in order to roll back into the core platform and improve that experience for all users.

The networked nature of ELMS:LN ensures that if new innovations pulled into the platform follow the pattern of development then they will automatically get updates, rosters of users, and single sign on with any existing system. This ensures that any amazing innovation built by those in the network has an easy path toward being ingested by others. Improvements to one solution in ELMS:LN lead to direct improvements in other pieces.

## Will this always require Drupal?

No. In fact Web components are utilized far more then Drupal 7. We are all about the correct solution to a problem. Drupal provides unparalleled automation and deployment capabilities which uniquely position it for certain content management and database backed solutions. We will be adding Drupal 8 support in the future. There's also early support for GravCMS and experimental work toward integrating micro-service / docker architecture into the pattern based development methodology we employ.



