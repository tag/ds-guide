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
to be documented—and not just the text of the change, but also who proposed it.

This is even more important with computer code, when adding features to an
application may affect multiple files. Everyone needs to work from the most
current files to help prevent errors. In addition, there needs to be an easy way
of pushing the most current code to production, and _not_ pushing features that
are incomplete or broken.

Perhaps you can see why some automated system for handling versioning is
critical.

!!! note "Change Control Systems are Important"
    Organizations should also have an administrative process (with a supporting
    information system) called "change control", which helps keep track of what
    changes have been made in production systems. This is an important—but
    separate—topic, which we won't go in to here.

## Early version control systems
