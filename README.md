# OctoBot - Repo Manifest
=============

Manage multiple repositories using
[Google Repo](http://code.google.com/p/git-repo/) (experimental).

This is the repository holding the manifest(s) describing repositories
to check out.

How to use
----------
1) Get [Google Repo](http://code.google.com/p/git-repo/), the following
assumes `repo` is in your path.

2) Create a directory for a local Repo install

3) Init/Install Repo by running `repo init -u https://github.com/Drakkar-Software/OctoBot-Repo-Manifest`

4) Syncronize the repositories by running `repo sync`.

5) Start master branches (so that each repository follows the github master
, need to understand this better...) on all repositories by running
`repo start master --all`




Manifests
---------
- `default.xml` : main manifest, used to manage personal github repos
