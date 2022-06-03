# Descartes Underwriting

## Context

We wish to create a backup tool that will save only the last modified files of a storage unit.

In our example, the storage unit is **not a bucket**.

The storage unit is the `DD-MM-YYYY-test` branch of the current `descartes-underwriting/devops-technical-test-data` git repository.

## Property

The `descartes-underwriting/devops-technical-test-data` repository is not frozen and will have new commits.

Commits will be added to the `DD-MM-YYYY-test` branch multiple times every day.

The `DD-MM-YYYY-test` branch name will be adapted using standard datetime convention eg: `01-01-2022-test` for the 1st of January 2022.

## Task

Develop a backup tool to save the modified files at each commit.

### Submission

Script and data should be saved on a private `candidate/descartes-backup-project` repository on your github account.

Access should be granted to all members of the `descartes-underwriting` group:

<https://github.com/orgs/descartes-underwriting/people>

Especially:

* <https://github.com/alexandreCameron>
* <https://github.com/Mareak>
* <https://github.com/jrdescartes>

### Script

Create a script to automate the backup process using open source software.

The script should track the changes fo the branch `DD-MM-YYYY-test` of the `descartes-underwriting/devops-technical-test-data` repository.

The execution of the script should be carried out with a github-action / gitlab-pipeline or any other tool automating git workflow on your git project.

It is highly recommended to use a scheduling tool to execute the back up process.

### Data

The backup should store files in separate folders.

The backup file structure should be based on the sha1 of the `descartes-underwriting/devops-technical-test-data`.

Starting from the initial commit [282180fe7e5d9cbf297f2f0ef813cffe60ce2328](https://github.com/descartes-underwriting/devops-technical-test-data/commit/282180fe7e5d9cbf297f2f0ef813cffe60ce2328), all the history should be backup.

## File structure example

For the following commits on the `descartes-underwriting/devops-technical-test-data`:

| SHA | OPERATION |
|-----|-----------|
| Commit_N | create readme.md |
| Commit_N+1 | create doc.txt |
| Commit_N+2 | create data/test/test.txt |
| Commit_N+3 | append text to ./doc.txt |
| Commit_N+4 | create test/project/project1.txt |

The `candidate/descartes-backup-project` repository should have

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
