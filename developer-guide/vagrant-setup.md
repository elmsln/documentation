<h1 id="elmsln-vagrant-instructions-elmsln-vagrant-instructions-">ELMSLN Vagrant Instructions {#elmsln-vagrant-instructions}</h1>
<p><a href="https://www.youtube.com/watch?v=ZeuDKzs6sj0&amp;list=PLJQupiji7J5fygec37Wd-gAbpMj8c5A_C">Watch how to use this!</a></p>
<h3 id="what-is-this-what-is-this-">What is this {#what-is-this}</h3>
<p>This is a Vagrant profile for installing a fully functioning<a href="https://github.com/elmsln/elmsln">ELMS Learning Network</a>in a single command! This instance is for development purposes but you can follow the<a href="https://elmsln.readthedocs.io/en/latest/INSTALL">installation instructions</a>to install this on any real server!</p>
<h3 id="how-to-use-this-to-bring-up-elmsln-how-to-use-this-to-bring-up-elmsln-">How to use this to bring up ELMSLN {#how-to-use-this-to-bring-up-elmsln}</h3>
<ol>
<li>Install
<a href="https://www.virtualbox.org/wiki/Downloads">VirtualBox</a>
(5.1.14+)</li>
<li>Install
<a href="http://www.vagrantup.com/downloads.html">Vagrant</a>
(1.9.1+)</li>
<li>Install
<a href="http://git-scm.com/downloads">git</a></li>
<li>Open Terminal(OSX/Linux) or PowerShell (Windows) and navigate to the folder you want elmsln in. Now clone the repository using the command (
<code>git clone https://github.com/elmsln/elmsln.git</code>
)
<img src="https://cloud.githubusercontent.com/assets/16597608/13260179/60875b1e-da28-11e5-865f-89e6586f370a.PNG" alt="" title="clone elmsln"></li>
</ol>
<h3 id="spin-up-the-development-instance-osx-linux-spin-up-the-development-instance-osx-linux-">Spin up the development instance (OSX / Linux) {#spin-up-the-development-instance-osx-linux}</h3>
<pre><code>cd
 elmsln

sh
 developer
</code></pre>
<h3 id="spin-up-the-development-instance-windows-spin-up-the-development-instance-windows-">Spin up the development instance (Windows) {#spin-up-the-development-instance-windows}</h3>
<p>Find Powershell, right click, select run as Administrator. Navigate to elmsln directory</p>
<pre><code>cd elmsln
vagrant plugin 
install
 vagrant-vbguest
vagrant 
plugin
install
 vagrant-hostsupdater
vagrant 
plugin
install
 vagrant-cachier
vagrant up
</code></pre>
<p>If you have issues downloading the box try running<code>vagrant box add --insecure -c elmsln/ubuntu16 --force</code>ahead of time which will download just the box in question. This will take a long time the first time you do it as it has to download a server image. After the first build, future builds from scratch should take about 10-12 minutes.</p>
<h3 id="after-installation-completes-after-installation-completes-">After installation completes {#after-installation-completes}</h3>
<p>Now you'll be able to jump into any of the domains that ELMSLN starts to establish for use! Go to <a href="http://online.elmsln.local/">http://online.elmsln.local/</a> after installation completes. If it all worked you should see a new Drupal site running the Course Information System (CIS) distribution.<em>If this address doesn't resolve, you may need to do this extra step at the bottom in Legacy - host file management</em></p>
<p>You can log into this with<code>user: admin | password: admin</code></p>
<p><img src="https://cloud.githubusercontent.com/assets/329735/22887464/ca97877e-f1c7-11e6-98df-2207a421204d.png" alt="" title="log in"></p>
<p>To connect to the console of your instance:<code>vagrant ssh</code>Here you'll have access to command line elms called<code>leafy</code>. Type<code>leafy</code>to see developer options for selection. This also comes installed with a fully primed copy of<code>drush</code>so you can type<code>drush sa</code>to see a list of possible drupal sites to run commands against.<code>drush @elmsln</code>is a target that will run the command against every site it finds in the elmsln instance.</p>
<h3 id="create-a-new-course-create-a-new-course-">Create a new course {#create-a-new-course}</h3>
<ol>
<li>Click Add, then select New Course</li>
<li>Create the name of the course. Ex: Art100</li>
<li>Choose which services to access under course network</li>
<li>Finish by clicking Create course</li>
<li>Wait while the services are installed</li>
<li>Once it says service is available, you can click Access service</li>
</ol>
<h3 id="why-use-this-why-use-this-">Why use this {#why-use-this}</h3>
<p>It has been optimized and heavily tested for use with ELMS:LN and it is what we use in daily testing and development and is the easiest way to get up and running. The alternative is to deploy the system on a live server environment and hook up real IPs to DNS entries. This is great / realistic but a lot of times people just want to play with things before jumping in fully. Vagrant provides this and does so with minimal barriers to entry.</p>
<h3 id="legacy-host-file-management-legacy-host-file-management-">Legacy - host file management {#legacy-host-file-management}</h3>
<p>This step is now only required if you don't follow the above directions about how to get our development environment up and running. Add this code to your /etc/hosts (or<a href="http://www.howtogeek.com/howto/27350/beginner-geek-how-to-edit-your-hosts-file/">windows equivalent</a>) so you can access it "over the web".</p>
<pre><code>###ELMSLN development
# front facing addresses
10.0
.18
.55
      courses.elmsln.
local
10.0
.18
.55
      media.elmsln.
local
10.0
.18
.55
      online.elmsln.
local
10.0
.18
.55
      analytics.elmsln.
local
10.0
.18
.55
      studio.elmsln.
local
10.0
.18
.55
      interact.elmsln.
local
10.0
.18
.55
      blog.elmsln.
local
10.0
.18
.55
      comply.elmsln.
local
10.0
.18
.55
      discuss.elmsln.
local
10.0
.18
.55
      inbox.elmsln.
local
10.0
.18
.55
      people.elmsln.
local
10.0
.18
.55
      innovate.elmsln.
local
10.0
.18
.55
      grades.elmsln.
local
10.0
.18
.55
      hub.elmsln.
local
10.0
.18
.55
      lq.elmsln.
local
10.0
.18
.55
      cdn1.elmsln.
local
10.0
.18
.55
      cdn2.elmsln.
local
10.0
.18
.55
      cdn3.elmsln.
local
# backend webservices addresses
10.0
.18
.55
      data-courses.elmsln.
local
10.0
.18
.55
      data-media.elmsln.
local
10.0
.18
.55
      data-online.elmsln.
local
10.0
.18
.55
      data-studio.elmsln.
local
10.0
.18
.55
      data-interact.elmsln.
local
10.0
.18
.55
      data-blog.elmsln.
local
10.0
.18
.55
      data-comply.elmsln.
local
10.0
.18
.55
      data-discuss.elmsln.
local
10.0
.18
.55
      data-inbox.elmsln.
local
10.0
.18
.55
      data-people.elmsln.
local
10.0
.18
.55
      data-innovate.elmsln.
local
10.0
.18
.55
      data-grades.elmsln.
local
10.0
.18
.55
      data-hub.elmsln.
local
10.0
.18
.55
      data-lq.elmsln.
local
</code></pre>
<h3 id="spin-up-the-vagrant-instance-spin-up-the-vagrant-instance-">Spin up the vagrant instance** {#spin-up-the-vagrant-instance}</h3>
<pre><code>cd
 elmsln

sh
 developer
</code></pre>
<p>Now you'll be able to jump into any of the domains that ELMSLN starts to establish for use! Go to <a href="http://online.elmsln.local/">http://online.elmsln.local/</a> after installation completes (grab a coffee, it takes awhile the first time to finish). If it all worked you should see a new Drupal site running the Course Information System (CIS) distribution.</p>
<p>You can log into this with<code>user: admin | password: admin</code></p>
<p><img src="https://cloud.githubusercontent.com/assets/16597608/13260446/767d8ae6-da29-11e5-8346-393a09c54cf6.PNG" alt="" title="log in"></p>
<p>To connect to the console of your instance:<code>vagrant ssh</code></p>
<h3 id="create-a-new-course-create-a-new-course_1-">Create a new course {#create-a-new-course_1}</h3>
<ol>
<li>Click Add, then select New Course</li>
<li>Create the name of the course. Ex: Art100</li>
<li>Choose which services to access under course network</li>
<li>Finish by clicking Create course</li>
<li>Wait while the services are installed</li>
<li>Once it says service is available, you can click Access service</li>
</ol>
<h3 id="why-use-this-why-use-this_1-">Why use this {#why-use-this_1}</h3>
<p>It has been optimized and heavily tested for use with ELMS:LN and it is what we use in daily testing and development and is the easiest way to get up and running. The alternative is to deploy the system on a live server environment and hook up real IPs to DNS entries. This is great / realistic but a lot of times people just want to play with things before jumping in fully. Vagrant provides this and does so with minimal barriers to entry.</p>
<p>**Note: If you are experiencing an APDQC Error (<a href="https://github.com/elmsln/elmsln/issues/1843\">https://github.com/elmsln/elmsln/issues/1843\</a>) when running<code>sh developer</code>after the first time please run the following commands to fix:</p>
<ul>
<li><code>vagrant ssh (within the elmsln folder where you usually do sh developer)</code></li>
<li><code>sudo service mysql restart</code></li>
<li><code>logout</code></li>
</ul>
<p>This should fix your install and allow you to continue developing smoothly :)</p>
<magazine-cover header="Research Technology" subheader="Marshall Space Flight Center" text="Marshall Space Flight Center’s" image="https://images-assets.nasa.gov/image/0000362/0000362~thumb.jpg" action="Touch to learn more" icon="check" link="#" class=" magazine-cover-0">
</magazine-cover>
