This page contains answers to frequently asked questions (some of which have been asked in person).

**Why make users add books manually? This is tedious. Why not use something like an ISBN API so that users don't have to fill in lots of details for all of the books they want to store?**

This was considered before starting the project. However, at present, a sufficiently good API for books has not been found. The search results aren't that good. 

Besides, adding manual input is only the first part of the process. Platforms like Goodreads have this, too: if no such book exists in the catalogue, users can add their own books. 

We are currently working on curating our own library catalogue of books that users can search from: the [Books API](https://github.com/Project-Books/books-api). 
We want to have users be able to search for books from a large catalogue as well as add their own books.

**It’s been done before, and Goodreads does a fair job at it. Why reinvent the wheel?**

We're not reinventing something. We're not making a carbon-copy clone of Goodreads or some other platform. What we are doing is creating something that addresses some of the popular concerns about Goodreads (see next question). In short, while we do think Goodreads is a good platform, we think it could be so much better. 

**So how is the Book Project different to Goodreads?**

- Open source: it's a collaborative effort. Alone, a single developer may not be able to compete with Goodreads. Together, we can. What this hopefully means for the end-user is that we're focused on building something incredible purely because we want to make something amazing (and we're not driven by profit). We hope this translates into developing features at a much quicker rate than closed-source software like Goodreads.

- Clean design: the Goodreads UI is outdated. Many have been asking for a design refresh for some time. By clean design, we mean a) it looks good and b) it's simple.

- Community first: we want to listen to our users and build the features they're asking for. In the case of Goodreads, in addition to a better design, users have been asking for features such as half stars (which we trump by having a more granular ten-point scale). We're also looking into some other flaws of Goodreads such as having to use HTML for reviews (not very user-friendly) and spammy reviews. And these are just some examples of the many, many requested features that have been lingering in the ether for years.

- Quick: the Goodreads website is OK, but the mobile apps are slow.

- Privacy first: Amazon doesn't have the best reputation when it comes to privacy and, unfortunately, Amazon owns Goodreads. From something as seemingly innocuous as the books someone likes, a lot can be extrapolated (see the [BBC 'Secrets of Silicon Valley' documentary clip](https://www.bbc.co.uk/programmes/p05bw5jg)). We aim to collect as little data as possible, we're going to be very transparent about what we do collect and we won't do anything nefarious with your data.

**When will the Book Project be deployed to real users?**

Soon, we hope! We don't want to rush into publishing something that we don't believe is production-quality. This means that we need to fix any bugs, add a lot more unit tests to help us catch bugs and generally improve the quality of our code.
