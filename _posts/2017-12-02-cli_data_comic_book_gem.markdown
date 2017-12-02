---
layout: post
title:      "CLI DATA COMIC BOOK GEM "
date:       2017-12-02 23:15:23 +0000
permalink:  cli_data_comic_book_gem
---

I am a big fan of comic books, especially heroes like Spiderman, Batman, X-men.
I could read all of them:) so I decided to scrape a site that offers weekly releases of
all comic books that I would be interested in. I decided that the best course of action
would be to first present the user with a list of release weeks that can be further explored
by comic book title. Site is called leagueofcomicgeeks.com and allows a user to browse comic releases 
by weeks; current, 2 in advance and 2 prior to the current week. So my first task was to scrape 
the links of weeks get the url and navigate to it to capture all comics released for that week.
From a list of comics for a specific week the user can choose to select a specific comic book title
and get information about the authors and a full description. There were a lot of comics listed
so I used a gem called command_line_reporter that formats the data in a more user-friendly way.
The scraping part was challenging, but the site was well structured so I was able to drill down
to the data I wanted without to much acrobatics involved. I also learned a lot about what Ruby 
gems are how to build them and I sure did a lot of searching on the web about managing the 
gemspec file:). All in all a challenging project but you got to challenge yourself to get better. 
