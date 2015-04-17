
__Goal__: Play back older posts in an RSS feed. (Why? Assume you like reading blogs in your RSS reader, but you'd like to read older blog posts as well.)

__Problem__: RSS feeds don't typically store their older posts. Google Reader used to archive old posts, but it no longer exists.

__Solution__: If a blog's RSS feed has been regularly archived on web.archive.org, we can read the archived RSS feeds to find older posts.

First, check to make sure that archives of the feed are available, using [this](http://archive.org/wayback/available).
Then, get a list of timestamps of archives using [cdx](https://github.com/internetarchive/wayback/tree/master/wayback-cdx-server).
