# myGit

## 1. Initialize a Repository (git init)
Create a directory (e.g., .mygit/) that will store everything related to version control. Inside it, create:

- A folder to store objects (compressed file data). :white_check_mark:
- A folder for refs (branches and tags). :white_check_mark:
- A HEAD file to keep track of the current branch. 

## 2. Store File Contents as Blobs
In Git, each version of a file is stored as a compressed "blob". What to do:

- Read the file contents.
- Compute a SHA-1 hash of the contents.
- Store the compressed file using part of the hash as its filename.
- Avoid storing duplicate files (since identical content will have the same hash).

## 3. Track File Changes (Index/Staging Area)
When a user runs git add <file>:

- Store a record of the file’s latest blob hash in an index (a file that lists tracked files and their hashes).
- The index acts as the staging area—it holds file versions before they are committed.

## 4. Create Commits (git commit)
A commit should store:

- A tree (snapshot of all files in the repository).
- A reference to the previous commit (parent commit).
- Metadata like author, timestamp, and commit message.
- The commit object itself should be hashed and stored in the object database.

## 5. Implement Branching (git branch)
Branches are just pointers to commits. What to do:

- Store branch names inside .mygit/refs/heads/.
- Update the HEAD file to point to the current branch.
- Allow creating new branches by copying commit references.

## 6. Implement Checkout (git checkout)
Switching branches or commits requires:

- Looking up the commit/tree structure.
- Extracting files from the object store.
- Overwriting the working directory with the checked-out files.

## 7. Implement Merging (git merge)
To merge two branches, you need to:

- Find the common ancestor (using commit history).
- Compare file differences.
- If conflicts exist, prompt the user to resolve them manually.

## 8. Handle Diffs (git diff)
To compare file versions, you should:

- Retrieve file blobs from the object store.
- Perform line-by-line comparison.
- Display changes in a readable format.

## 9. Implement Remote Repositories (git push/git pull)
If you want a distributed system:

- Allow storing repository data in a remote server.
- Implement a way to send and fetch commits over a network.
- Use compression to transfer only necessary changes.



