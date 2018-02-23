## Services vs Authorities {#services-vs-authorities}

There are two major system classifications in ELMSLN; authorities and services. Authority systems are those that only have a single deployment. The current authorities are online, inbox, media, and comply. The implication for these systems is that if you go to online.elmsln.local/sing100, you are still within the online.elmsln.local database. All course records on this system are nodes in effect.

In a Service, all course "folder" paths are actually different, sandboxed Drupal sites. For example, courses.elmsln.local/sing100 is a different Drupal site / database from courses.elmsln.local/stuff200. Some examples of services include courses, studio, interact, discuss, and blog.

This means that Services could \(theoretically\) be radically different from each other, which is by-design capability to allow for maximal flexibility in adopting the system to teaching styles. Authority systems are those who's functionality is considered core to the larger operation of the network. These are also largely more thought of as infrastructure and less spaces for innovation.

For example, we don't need an innovative email system, we just need something to store and bridge communications between systems. CIS / online is a giant routing / logistics system, it really _needs _to be rigid; whereas the place students experience material doesn't.

## What is a Service?

Services are systems that are replicated once per course. This provides additional flexibility in a space where it may make more sense to have customization per course. Services are effectively being created dynamically as part of a new course being setup.

For example: If a course network is to use the content outlining tools and a blog, these tools being selected will actually produce 2 new drupal sites and network them together.

These sites call home, can sync roster / access rights with each and most importantly, fork from the original intention. While they shouldn't fork far, they can allow for faculty to have customized learning environments and teach the way they want to and need to in order to better connect with learners.

For example: forking from the default configuration of the online studio environment can allow an instructor to have a video centric conversation rather then an image centric one. We could later capture this innovation and make it repurposable but it's more important that we allow fragmentation in the short-term in order to spur innovation, test it, and capture it can come later.

"Capture" on the pedagogy side is making an option to setup future studios this way. "Capture" on the developer side is making Drupal Features to package the configuration so that it can be used in other distributions / future installs.

## What is an Authority?

Authority systems are those that have a single source. These are systems in a network that really need to only exist in one place. For example, if there were multiple asset management systems, or per course asset management systems, it would become unmanagable.

Also, if there were multiple authorities of section data, it would become difficult to maintain integrity of sections across the rest of the network.

