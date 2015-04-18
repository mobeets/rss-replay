
__Goal__: Play back older posts in an RSS feed. (Why? Assume you like reading blogs in your RSS reader, but you'd like to read older blog posts as well.)

__Problem__: RSS feeds don't typically store their older posts. Google Reader used to archive old posts, but it no longer exists.

__Solution__: If a blog's RSS feed has been regularly archived on web.archive.org, we can read the archived RSS feeds to find older posts.

First, check to make sure that archives of the feed are available, using [this](http://archive.org/wayback/available).
Then, get a list of timestamps of archives using [cdx](https://github.com/internetarchive/wayback/tree/master/wayback-cdx-server).

### Usage

__Inputs__

Form

* pick feed; start date, end date of posts
* pick frequency of posting

__Outputs__

* check to make sure rss path exists on web.archive.org
* add entry to database, if duplicate does not already exist
* if new entry was added, create empty rss at new feed url (i.e., set up routing to serve this url)
* show user new feed url

__Task database__

* input feed url, output feed url, start date, end date, post frequency, date of last post, last web.archive timestamp posted, last post id posted

__Feed database__

* output feed url, rss content

__Processing__

* should run once a day, and go through every item in database
* for each item in Task database:
    - if "date of last post" is empty, create post; otherwise, check "date of last post" and "post frequency" to see if new post is needed
    - fetch posts using "last web.archive timestamp posted", and try to find next post id after "last post id posted"; if not, fetch the next web.archive timestamp and repeat
    - create new post by updating Feed database
