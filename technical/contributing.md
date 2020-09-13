# Contributing

Code and documentation contributions are done with pull requests for the appropriate repositories (frontend, api, auth, admin, image). When implementing a feature you should consider if the implementation is generic in a sense that it's usable outside your customized application. If the implementation is generic it should be placed on the core-repositories. If you think no-one else might not benefit from the code as it's too application-specific it propably shouldn't be in the core-repositories. Remember you can always ask the community for opinions. Find us at slack: 

To submit code we follow the well known Git Flow, read more at the [Git flow page](technical/git-flow.md).

The frontend server use ApostropheCMS that allows for creating custom widgets that can be loaded per site, for custom widgets best is to create an own repository and allow other installation the ability to load it in with NPM. 



### Submit a pull request on GitHub

- Visit your GitHub repository page and issue the pull request.
- Core developers will Review the patch and may require changes or improvements to it prior to it being accepted.
- It will be up to the submitter to amend the pull request and keep it alive until it gets merged.
- Please be patient as pull requests are often reviewed in spare time so turn-around can be a little slow.
- Make sure your code works with the latest for the branch you are working on.



