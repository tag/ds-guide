# Version Control Systems

Have you ever needed to keep multiple versions of a file? Maybe you're president
of the knitting club, and need to keep a list of active members, but you don't
want to lose the historical list of who was active last year. Do you recreate
the list every year, and keep old copies?

Have you ever worked on a document, either by yourself or with a partner, and
had different file names after each revision? Maybe you used name such as
"Report", "Report-updated", "Report-updated-final", and maybe even
"Report-updated-final-USE-ME". This method of versioning gets confusing quickly,
especially when "final" doesn't really mean "final".

Or consider a legislative body that proposes, debates, and amends laws. The law
that's eventually passed (or defeated) may have little resemblance to the law
that was originally proposed. Other legislators may propose amendments in
committee, or on the floor of the legislature. Every change needs to be
documented. Actually, every _proposed_ change, whether it passes or not, needs
to be documented—and not just the text of the change, but also metadata such as
who proposed the change and when.

This is even more important with computer code, when adding features to an
application may affect multiple files. Everyone needs to work from the most
current files to help prevent errors. In addition, there needs to be an easy way
of pushing the most current code to production, and _not_ pushing features that
are incomplete or broken.

Perhaps you can see why some automated system for handling versioning is
critical. Such a system is called a _**version control system (VCS)**_.

!!! note "Change Control Systems are Important Too"
    Organizations should also have an administrative process (with a supporting
    information system) called "change control", which helps keep track of what
    changes have been made in production systems. This is an important---but
    separate---topic, which we won't go in to here.

Other names for version control include "revision control" and "source control".
Although VCSs can be used for any type of versioned file, they are most often
used for _source code management (SCM)_.

*[VCS]: Version Control System
*[VCSs]: Version Control Systems
*[DVCS]: Distributed Version Control System
*[DVCSs]: Distributed Version Control Systems
*[SCM]: Source Code Management

## Early version control systems

There were a handful of early attempts at building a VCS. For many years, one of
the most common was a program called CVS, which stood for "Concurrent Versioning
Sytem". CVS was free and open source, which was one of the reasons it was
adopted so freely.

CVS used a client–server model. The server held the "single source of truth" in
a database called a _**repository**_. Developers could _**check out**_ copies from the
repository to their local client machine. The local copy was called the _**working
copy**_, or sometimes sandbox or workspace. After making changes, developers would
_**commit**_ their changes to the remote repository.

One major advantage of version control systems is _**branches**_. For example, the
code for Windows 7 and Windows 10 are necessarily different, even though they
have many of the same features. The same with Windows 10 Home and Windows 10
Pro. The code is similar, but different in specific ways. When Microsoft
releases a patch for a security flaw in Windows, in sometimes has to fix the
security hole in each of those versions, or branches. It's common to create a
branch for each released version of a product. Modernly, each feature might have
its own branch as its being developed, with the feature being merged into the
next version when it's ready. Additionally, each developer might have their own
branch, to help limit unintended interactions from the work of others.

If you attempted to commit your changes to a branch, and other developers had
committed changes to the same branch since your checkout, it was necessary to
_**update**_ (sometimes called _**merge**_) the new commits back from the
repository to your local copy before the your new commit would be permitted. As
you might suspect, as a development team grew in size, the amount of time it
spent merging each others' commits also grew. Modernly, the term merge is used
to describe copying updates in one branch into another branch.

Over time, some of the warts in CVS became clear. Commits to CVS were not,
_atomic_[^atomic], meaning if a commit was interrupted the repository could
become corrupted. In addition there was some odd behavior around how it handled
merging files renamed in separate branches. Several commercial VCSs sprung up,
including Visual SourceSafe, which was bought by Microsoft in 1995.
To add necessary features, and take advantage of the many things developers had
learned about version control systems, in 2000, a new project called Subversion
(often abbreviated as SVN) was started by some of the developers of CVS.
Subversion 1.0 was officially released in 2004.

[^atomic]: You might remember _atomic_ as one of the necessary parts of ACID
properties of databases. The term ACID---which stands for Atomicity,
Consistency, Isolation, and Durability---was coined by Andreas Reuter and Theo
Härder in 1983.

## Distributed version control systems

Until about 2005, the dominant model for VCS was client–server. Most systems,
including CVS and Subversion, used this model. One of the downsides of the
client--server model should be obvious: if the server failed, the repository
history was lost, and developers were left with only their working copies. This
was partly a conscious design decision in early systems. Hard drive space was
expensive and network speeds were slow, so transferring large files was not
optimal.

Our systems have changed. Networks are faster and hard drive size is no longer
constraints for most applications. More people are connected, which also makes
peer-to-peer architectures more viable.

In 2005, following a brief controversy with the VCS used by Linux, two new
systems, Git and Mercurial, were released to the public as open source software.
Both are _distributed_ version control systems (DVCS), which allow developers to
push commits to _any_ remote system. With modern DVCSs, there may be a single
centralized repository, or many. Developers can even push code commits directly
to each other, bypassing the central system. Each developer keeps a full history
of their work, so it's significantly easier to recover a projects history if a
central server fails.

Git was written by Linus Torvalds, the creator of Linux. Mercurial was written
by Matt Mackall, at about the same time, and for much the same reason. Somewhat
unsurprisingly, the Linux project adopted Git. Git was perhaps made famous by
the creation of GitHub, which promised free cloud hosting for open source
projects. I was dabbling with an open source project at the time, and it seemed
there was a mass exodus to GitHub, as it was so very much better than other open
source hosting at the time. (Google Code was better than SourceForge, but still
had its challenges.) As of 2019, Mercurial is used by several major
organizations, including Facebook[^MM], W3C, and Mozilla.

[^MM]: As of 2019, Matt Mackall, author of Mercurial, works at Facebook.

One of the major differences between DVCS and VCS is the local copy of the
repository. Thus, systems like Git have a _**two-phase commit**_. Changes are
first committed to the local repository, then when they are ready, the developer
will _**push**_ all of the commits in a branch to a remote repository.

## Using version control systems

Modern version control systems have several common characteristics:

1. Annotation and blame. The ability to provide a full history of each line in a
   code file, including who wrote, deleted, or changed it, when each revision
   was committed, and notes regarding the purpose of each commit. It's
   considered good practice to briefly describe each commit. A report showing
   who wrote each line (and when) is often called a "blame" file.

2. Branching and merging. Although workflows differ between organizations, it's
  common to create a branch for each feature under development. As a feature is
  completed, those branches are typically merged into release branches. In more
  complicated setups, each developer might have their own branch for each
  feature. The ability to merge a change to multiple branches---for example,
  making a security fix to multiple versions---is much easier in modern systems.

3. Traceability. Annotations allow VCSs to connect to requirements systems and
  issue tracking systems. In some industries, such as defense and aerospace,
  it's critical to be able to identify why each change was made, and who
  requested it. Traceability and requirements systems are often separate from
  VCSs, but can integrate with them.

## Git hosting providers

It's important not to confuse Git with the hosting provider. Atlassian has a Git
hosting service called [BitBucket]. GitHub---which was acquired by Microsoft in
2018 for $7.5 billion---has their eponymous hosting service. Like Bitbucket,
GitHub is merely a web interface over the top of a cloud-hosted Git server.

Modernly, there are many quality Git hosting providers, including [GitLab],
which also provides an opensource interface if you wish to run your own hosting
server and repository manager.

[BitBucket]: https://bitbucket.org/product/
[GitHub]: https://github.com
[GitLab]: https://about.gitlab.com

## Additional reading

* _[Pro Git]_, by Scott Chacon and Ben Straub, APress. This book available
    online in HTML, PDF, and e-book formats for free under a Creative Commons
    Attribution Non-Commercial Share-Alike 3.0 license. It's worth reading the
    first few chapters.
* _[Version Control with Subversion]_, by Ben Collins-Sussman, Brian W.
  Fitzpatrick, & C. Michael Pilato, O'Reilly. This book is available online in
  HTML Released under a Creative Commons 2.0 Attribution license. The section on
  [Subversion's history](http://svnbook.red-bean.com/en/1.7/svn.intro.whatis.html#svn.intro.history)
  is brief and interesting.
* Perhaps the best introductions to Git come from [Atlassian](https://www.atlassian.com/git/tutorials/what-is-version-control)
  and from [GitHub](https://try.github.io)
* GitHub has a [great tutorial](https://guides.github.com/activities/hello-world/)
  for their repository hosting product. GitHub is free for public/open source
  projects.
* [Git-it] is a desktop (Mac, Windows and Linux) app that teaches you how to use
Git and GitHub on the command line.
* _Wikipedia_ has a good article on ["Version Control"](https://en.wikipedia.org/wiki/Version_control)

[Pro Git]: https://git-scm.com/book/en/v2
[Version Control with Subversion]: http://svnbook.red-bean.com
[Git-it]: https://github.com/jlord/git-it-electron#what-to-install

## Footnotes
///Footnotes Go Here///

## Review

1. What is a "Version Control System" used for?
2. Describe the difference between distributed version control systems and
   centralized version control systems.
3. Explain the phrase "two-phase commit".
3. Explain the terms "commit", "push", "merge".
4. Explain the difference between "merge" and "update" in modern Git.

## Exercises

1. Create a repository in Git, using the command line. Add a file, and commit
the change. Make a change to the file, and commit with a useful commit message.

2. Create a repository with a hosting service like GitHub. Perform a checkout,
and make changes. Push your commits back to the hosted repository.
