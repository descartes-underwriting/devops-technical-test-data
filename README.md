# Descartes Underwriting

## Context

We wish to create a backup tool that will save only the last modified files of a storage unit.

In our example, the storage unit is **not a bucket**.

The storage unit is a git repository called `devops-technical-test-data`.

The repository `devops-technical-test-data` is not frozen and will have new commits.

Commits will be added to the `datestamp-test` branch on the `devops-technical-test-data` repository.

## Task

Develop a backup tool to save the modified files at each commit.

### Submission

Script and data should be saved on a private `descartes-backup-project` repository on your github account.

Access should be granted to all members of the `descartes-underwriting` group:

<https://github.com/orgs/descartes-underwriting/people>

### Script

Create a script to automate the backup process using open source software.

The script should track the branch `datestamp-test` of the repository.

The execution of the script should be carried with a github-action / gitlab-pipeline or any other git automated workflow.

### Data

The backup should store files in separate folders.

The backup file structure should be based on the sha1 of the `devops-technical-test-data`.

## File structure example

For the following commits on the `devops-technical-test-data`:

| SHA | OPERATION |
|-----|-----------|
| Commit_N | create readme.md |
| Commit_N+1 | create doc.txt |
| Commit_N+2 | create data/test/test.txt |
| Commit_N+3 | append text to ./doc.txt |
| Commit_N+4 | create test/project/project1.txt |

The `candidate_backup_repository` should have

```bash
$ tree .
.
├── .gitworkflow
│   └── workflows
│       └── my-lovely-workflow.yml
├── data
│   ├── N
│   │   └── readme.md
│   ├── N+1
│   │   └── doc.txt
│   ├── N+2
│   │   └── data
│   │       └── test
│   │           └── test.txt
│   ├── N+3
│   │   └── doc.txt
│   └── N+4
│       └── test
│           └── project
│               └── project1.txt
└── script
    └── my-beautiful-script.best-language
```
