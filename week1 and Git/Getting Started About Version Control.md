
**Version Control** is a system that records changes to a file or set of files over time so that you can recall specific versions later.

- VCS allows users to revert back to a previous state. and allows to compare changes made overtime.

- So we can figure out who has caused the issue and when and more.

- Using VCS it makes files easily recoverable.

**Local Version Control Systems** Many people's version control method will be to create new folder for every version and copy files in this new folder and change them. But this method is incredibly error prone. It is easy to forget which directory you're in and accidentally write to the wrong file or copy over the files you don't mean to.

To deal with this issue, To deal with this issue programmer have developed VCSs that had a simple database that kept all the changes to the files under revision control.

![Local version control diagram](https://git-scm.com/book/en/v2/images/local.png)
###### Figure 1 Local version control diagram

One of the most popular VCS tools was a system called RCS, which is still distributed with many computers today. RCS works by keeping patch sets in special format on the disk; it can then recreate any file looked like at any point by adding patches.

**Centralized Versions Control System**

The next major issue that people encounter is that they may need to collaborate with developers on other systems. To deal with this problem, Centralized Version control were developed. These systems have single server that contains all the versioned files and number of clients that check out fuels from that central place.

![Centralized version control diagram](https://git-scm.com/book/en/v2/images/centralized.png)
###### Figure 2 Centralized version control diagram.

**Advantages:**
- Know what other people are doing on the project.
- Grants control over who can do what part of the project.

**Disadvantages:**
- Single point of failure

**Distributed Version Control Systems**
Example are Git, Mercurial or Darcs.

Clients don't just check out the latest snapshot of the files; rather, they fully mirror the repository, including its full history.
Thus, if any server dies, and these systems were collaborating via that server, any of the client repositories can be copied back up to the server to restore it. Every clone is really a full backup of all the data.


![Distributed version control diagram](https://git-scm.com/book/en/v2/images/distributed.png)Many of these systems deal pretty well with having several remote repositories they can work with, so you can collaborate with different groups of people in different ways simultaneously within the same project. This allows you to set up several types of workflows that aren’t possible in centralized systems, such as hierarchical models.