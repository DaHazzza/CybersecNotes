https://tryhackme.com/room/contentdiscovery

In this Section i learn to find hidden content on webpages, things like admin panels or any other hidden pages

Webservers will have a robots.txt, a file which lists the directorys not to show on public web browsers
going into this page on our target device we see this

User-agent: *
Allow: /
Disallow: /staff-portal

showing that staff-portal is a hidden dir




Favicon

many frameworks for building websites install a default icon on the top of the tab, if this isnt changed we can see which framework the website is running and potentialy exploit it
https://wiki.owasp.org/index.php/OWASP_favicon_database - a list of favicons (md5 hash) to frameworks
now doing a curl command on thhe provided site can retrive the favico and then md5 hash it and search through the list
curl https://static-labs.tryhackme.cloud/sites/favicon/images/favicon.ico | md5sum 

we then find they are using cgiirc (0.5.9)



Sitemap.xml

Unlike the robots.txt file, which restricts what search engine crawlers can look at, the sitemap.xml file gives a list of every file the website owner wishes to be listed on a search engine. 
These can sometimes contain areas of the website that are a bit more difficult to navigate to or even list some old webpages that the current site no longer uses but are still working behind 
the scenes.

this is what it looks like

<urlset>
<url>
<loc>http://10.10.75.123/</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>1.00</priority>
</url>
<url>
<loc>http://10.10.75.123/news</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
<url>
<loc>http://10.10.75.123/news/article?id=1</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
<url>
<loc>http://10.10.75.123/news/article?id=2</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
<url>
<loc>http://10.10.75.123/news/article?id=3</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
<url>
<loc>http://10.10.75.123/contact</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
<url>
<loc>http://10.10.75.123/customers/login</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
<url>
<loc>http://10.10.75.123/s3cr3t-area</loc>
<lastmod>2021-07-19T13:07:32+00:00</lastmod>
<priority>0.80</priority>
</url>
</urlset>





Http headers
using curl and the -v we can see the headers of http and see some info on versions and frame works
curl -v {url}



framework exploitation
once we know the framework the best thing to do is then lookup that framewroks documentation ad see if there is a default portal or login
