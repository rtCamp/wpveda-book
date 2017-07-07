# Git Flow
GitFlow is a branching model for Git. It has attracted a lot of attention because it is very well suited to collaboration and scaling the development team.

# Key Benefits
- Parallel Development
- Collaboration
- Release Staging Area
- Support For Emergency Fixes


## How to use git flow with your existing git repo:

1.  You need to install **Git Flow** into you local machine.

    Git flow install into linux using

    >> command: sudo apt-get install git-flow

    For Other operating system visit: [nvie/gitflow](https://github.com/nvie/gitflow/wiki/Installation)

2.  Clone your existing git repo

    Once clone completed and Before initialize gitflow into your repo you need to create two branch into your repo.

    1. **Master**: This is default branch.
    2. **Develop**: This is development branch or next release branch.

    reference link : [wpveda/git/git-clone](http://wpveda.com/git/basic.html#5-1-2-git-clone)

3.  Run "git flow init" into your git repo folder

    >> command: git flow init

    After executing above command it will ask for configure stable branch [ production release ]

    ```
    Which branch should be used for bringing forth production releases?
          - develop
          - master
       Branch name for production releases: [master]:
    ```
    and develop branch [ Next release ].

    ```
    Which branch should be used for integration of the "next release"?
       - develop
    Branch name for "next release" development: [develop]:
    ```

    once branch configure you need to configure prefix for other branch and release tag

    ```
    How to name your supporting branch prefixes?
    Feature branches? [feature/]
    Release branches? [release/]
    Hotfix branches? [hotfix/]
    Support branches? [support/]

    Version tag prefix? []
    ```

    After configure this your repository configuration is done to use *Git flow**.


## Git Flow feature

Feature branch are use to develop new feature for the upcoming or distant feature release.

>> command: git flow feature [start | finish | publish | pull ] <feature_name>

- If two person ( andey and Rachel ) working on same project but in different feature like featureX and featureY.

- featureX will be released in a week by Andey and FeatureY will be released after month by Rachel. Can you handle above situation using git? if you can then it will be very complex to handle.

- Using gitflow it will handlw easly.

- simply Andey should start **featureX** and Rachel should start feature **featureY** using fllowing commnand of gitflow.

    >> command: git flow feature start featureX
    >> command: git flow feature start featureY

Using Above command git flow create two feature branch "featureX" & "featureY" from develop branch.

After a week, featureX is completed by Andey so Andey Finished that feature using

    >> command: git flow feature finish

Git flow merge featureX branch with develop branch and delete feature branch.

if Andey want to contribute in "featureY" in between development of "featureX" or after finishing it then it will be easy using gitflow.

1. Need to publish "featureY" on remote so andey can pull the code and contribute into in.

    >> command: git flow feature publish featureY


2. After publish code on remote by Rachel, Need to execute bellow command to pull Rachel code on Andey's machine.

    >> command: git flow feature pull featureY


## Git Flow release

When all next release features completed.you can start preparation of a new production release using **Git Flow release**.

>> command: git flow release [start | finish | publish | pull ] <release_tag> [BASE]

** [BASE] : commit sha-1 hash to start the release from.

In our example andey prepare realse "v1.1.0" with feature "featureX" using

    >> command: git flow release start v1.1.0

It's wise to publish the release branch after creating it to allow release commits by other developers.

    >> command: git flow release publish v1.1.0

after all set need to Finishing a release using

    >> command: git flow release finish v1.1.0

Git will merges the release branch back into production releases branch [master], Tags the release with its name and Back-merges the release into next release branch [develop].

After above task completed release brahch deleted.

** Don't forget to push your tags with **

    >> command: git push --tags


## Git Flow hotfix
In between delepment of next release, if any critical bug into earlier release then you can use ** git flow hotfix ** and git flow create new brach as hotfix branch from production releases [master] branch.

>> command: git flow hotfix [start | finish | publish | pull ] <hotfix_name> [BASENAME]

** [BASENAME] : version argument hereby marks the new hotfix release name.

Before release v1.1.0, if Andey find some critical bug like "login_issue" into previous releas.

At this time Andey make hotfix release using

    >> command: git flow hotfix start login_issue

By finishing hotfix it gets merged back into next release branch [develop] and production releases branch [master].

Additionally the master merge is tagged with the hotfix version.

    >> command: git flow hotfix finish login_issue

For more information Visit : [git-flow-cheatsheet](http://danielkummer.github.io/git-flow-cheatsheet/)
