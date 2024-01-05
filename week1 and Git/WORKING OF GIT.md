Git is a persistent Map.
Git reuses objects/blobs
Git might store just the diff of the files. 
Annotated Tags comes with a message.
Git is similar to file system.

---

| hash function | `git hash-object <input>` |
| ---- | ---- |
| cat-file | `git cat-file <hash> <MODE>` -p for read or -t for type |
| cat-file for tag | `git cat-file <tag-name> <MODE>` |
|  |  |

---
# Desmystifying Branch

- A branch is a reference to commit.
- Master is just a small file that contains reference.
- Head file contains reference to the head
- Head is pointer to a pointer
- Merge creates to parents.
- Git just looks at the objects not the path.
- Git will remove detached head after some time
- In detached head head moves as  the reference.

# Rebasing
- Rebase changes the base.
- detaches and moves to the top.
- detaches and makes it the parent.

Tradeoffs 
- Merge provides history exactly how it happened
- Merge preserves project history
	-
- Rebases refactors the history.

Tags are references.
Tags don't move.

# Distributed version control
- remote branch is just a reference to a commit
- We fetch then merge and then push for synchronization `git pull` is fetch followed by merge
- Never rebase shared commits
- Fork is kind of like clone but create  a remote repository to connect with original repo we need to use `upstream`
- pull request is used to synchronize changes in remote repo with forked repo.
- 