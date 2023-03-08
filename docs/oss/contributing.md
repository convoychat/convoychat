# ConvoyChat Contributor Guidelines

**Last updated: January 18, 2023**

**Notes:**

- The following is a set of guidelines for contributing to the ConvoyChat project. 

- Feel free to propose changes to this document in a pull request.

- Contributions to this project are released to the public under the project's open source license. See more [here](/LICENSE.md).

## Table of Contents

1. [Introduction](#introduction)
2. [Source Code Access](#access)
3. [Issue Reporting](#issue-reporting)
    - [Reporting Bugs](#bugs)
    - [Suggestions](#suggestions)
    - [Security Vulnerabilities](#vulnerabilities)
4. [Local Development](#development)
5. [Pull Request Process](#pr-process)
6. [Contributor Resources](#resources)
7. [Contributor Support](#support)

## <a id="introduction"></a> 👋 Introduction

ConvoyChat is a GraphQL realtime group messaging app based on React and Typescript.

ConvoyChat is and will always remain free and openly available under the **GNU General Public License Version 3** license. It can be
used and modified in any way by anyone.

The ConvoyChat project is maintained by the [C-EO](https://github.com/C-EO) and the [ConvoyChat Authors](https://github.com/c-eo/convoychat/graphs/contributors).

As the ConvoyChat Authors, we're committed to building a community that is welcoming and inclusive: an environment where people are encouraged to share ideas, treat each other with respect, and collaborate
towards the best solutions. To reinforce our commitment, we have adopted a slightly modified **[Code of Conduct](/docs/oss/code_of_conduct.md)** for the ConvoyChat project.

_**Please follow it in all your interactions with the project. Any violations of the Code of Conduct will result in serious consequences.**_

## <a id="access"></a> 🔐 Source Code Access

The source code to the ConvoyChat project can be accessed via a oublic-access repository on [GitHub](https://github.com/c-eo/convoychat).

This `main` branch of this repository contains the ongoing development of the ConvoyChat project.

All other releases of ConvoyChat can be found under their respective branches which may or may not follow a **[Semantic Versioning (Semver)](https://semver.org/spec/v2.0.0.html)** pattern; the source code for `v0.0.0-beta` of ConvoyChat can be found under the **v0.x-beta** branch.

If you wish to clone the repository, use the command below:

```bash
$ git clone https://github.com/c-eo/convoychat.git
```

**Requires Git to be installed on your local machine.**

## <a id="issue-reporting"></a> 📄 Issue Reporting

Like any other web application out there, ConvoyChat also encounters issues from time to time.

To be able to tackle those issues, we resorted to using [GitHub Issues](https://github.com/issues).

The ConvoyChat project issue tracker can be found [here](https://github.com/c-eo/convoychat/issues).

**The project's issue system is publicly readable --- however, you must have an account registered with GitHub to create a new issue.**

Before reporting any issue, please endeavor to check if a similar issue is already open. If there is one, please add a comment with additional information, react to it with a 👍, and subscribe to its notifications.

**Please note that due to other obligations, putting aside the ConvoyChat project, we are sometimes slow to respond to issues, especially if a bug is cosmetic, or a suggestion is vague or low in priority.**

### <a id="bugs"></a> 🐞 Reporting Bugs

Found a bug within ConvoyChat? All bugs can be reported using the `bug_report.yml` and `ui_bug_report.yml` templates of **[ConvoyChat's GitHub Issues](https://github.com/c-eo/convoychat/issues/new/choose)**.

The ConvoyChat project is very important to us as its developers, thus we take all bug reports very seriously.

If you find a bug, **DON'T** hesistate to report it to us immediately.

We will try our best to acknowledge legitimate bug reports within **14 days**.

### <a id="suggestions"></a> 🙋‍♂️ Suggestions

Most of our ideas come from the ConvoyChat community - our users and supporters.

We would love to here to each of your suggestions for ConvoyChat and see if its implementable.

All suggestions can be reported to us using [GitHub Issues](https://github.com/c-eo/convoychat/issues/new/choose) using the `suggestions.yml` template.

### <a id="vulnerabilities"></a> ❗ Security Vulnerabilites

In the world of technology today, security vulnerabilities are the biggest threat to everyone.

They can either lead to information being leaked or destruction of machines.

They cause more damage than a bug would, and ConvoyChat is no exception. In order to curb this threat, we have set up a **[Vulnerability Disclosure Policy](/docs/oss/security.md)** so that you can inform us of such threats.

Please **DON'T** and under no circumstances should you discuss undisclosed security vulnerabilities on any public mailing list.

We as the ConvoyChat Authors have a long history of handling reported vulnerabilities promptly and
effectively on many projects and we respect and acknowledge responsible reporters.

## <a id="development"></a> 💻 Local Development

Before we jump to the pull request process, you would have to set up your own instance to be able to make visible changes to the project.

To start off the development journey, you will need to sign up to the services listed below:

- **[Auth0](https://auth0.com)** - For user authentication
- **[Google Cloud Platform](https://cloud.google.com)** - For OAuth 2 support
- **[Cloudinary (Optional)](https://cloudinary.com)** - For image uploads
- **[MongoDB](https://mongodb.com)** - For database support

You could choose to sign up for **MongoDB Atlas** or you could download it and set it up locally.

Now that you're ready, you can start the development.

**Step 1 - Clone ConvoyChat**

The first step in deploying your own instance of ConvoyChat is to clone this repo:

```sh
git clone https://github.com/c-eo/convoychat.git
```

**Step 2 - Install Dependencies**

The next step is to install all required dependencies.

Install server side dependencies with this command:

```sh
cd convoychat
npm install
```

Then install the client side dependencies with this command:

```sh
cd client
npm install
```

**Step 3 - Environment Variables**

After installing all required dependencies, change the directory to the convoychat root folder with this command:

```sh
cd /path/to/convoychat
```

In the root folder you will find a file structure like the one below:

```txt
convoychat
|
|── .convoychat
|── .github
|── .vscode
|── client
|── docs
|── server
|── .dockerignore
|── .editorconfig
|── .env.example
|── .eslintignore
|── .eslintrc.json
|── .gitignore
|── .prettierignore
|── .prettierrc
|── .travis.yml
|── changelog.md
|── docker-compose.yml
|── Dockerfile
|── jest.config.js
|── LICENSE.md
|── package-lock.json
|── package.json
|── readme.md
|── tsconfig.json
```

In this next step, you will need to fill in the environment variables.

Follow the steps below:

- Create a new file named `.env` in the root folder.
- Open the [.env.example](/.env.example) file.
- Copy the contents of _.env.example_  and paste them in the _.env_ file.
- Replace all the dummy keys with your own valid ones.

**Step 3.1 - Setup Auth0 & Google OAuth 2**

You'll need Auth0 and Google OAuth 2 to handle user authentication.

Follow this guide for setting up Auth0 for NodeJS web applications.

> https://auth0.com/docs/quickstart/webapp/nodejs

It is **very important** that you setup all the callback URLs correctly in your Auth0 Dashboard.

To setup Google OAuth 2 follow the steps below:

- Create a Google account if you don't have one.

[![Organization Creation](/client/public/favicon.ico)](https://console.cloud.google.com)

- Visit **[Google Cloud Platform](https://cloud.google.com)** and log in.

[![Organization Creation](/client/public/favicon.ico)](https://console.cloud.google.com)

- After logging in, you'll be redirected to **[Google Cloud Console](https://console.cloud.google.com)**.

[![Organization Creation](/client/public/favicon.ico)](https://console.cloud.google.com)

- Create a an organization.

[![Organization Creation](/client/public/favicon.ico)](https://console.cloud.google.com)

- Create a new project under that organization.

[![Organization Creation](/client/public/favicon.ico)](https://console.cloud.google.com)

- Navigate to the `Credentials` page.

[![Organization Creation](/client/public/favicon.ico)](https://console.cloud.google.com)

- Navigate to the `OAuth 2 Consent Screen` page.

[![Organization Creation](/client/public/favicon.ico)](https://console.cloud.google.com)

- Follow the steps to create an OAuth 2 application.
- After creating the OAuth 2 application, copy the `Client id` and `Client secret`.
- Head back to your Auth0 dashboard, and replace the Google OAuth 2 Auth0 keys with your own.

And now you're done setting up Google OAuth 2.

**Need help?** You can open up an [issue](https://github.com/c-eo/convoychat/issues/new/choose) or contact us using our [email](mailto:convoychat@gmail.com).

**Step 3.2 - Setup Cloudinary (Optional)**

If you are working on a feature which includes image uploads, you'll also need to setup Cloudinary.

Follow this guide for setting up Cloudinary for NodeJS web applications.

> https://cloudinary.com/documentation/how_to_integrate_cloudinary

**Step 3.3 - Setup MongoDB**

As stated above, you could either sign up for MongoDB Atlas or download the MongoDB Community Edition.

Follow this guide for setting up MongoDB for NodeJS web applications.

> https://mongodb.com

**Step 4 - Starting ConvoyChat**

Finally to start the ConvoyChat server, execute this script in a new terminal:

```sh
npm run develop
```

**Alternatives**

**For Windows Users**: You can also set up ConvoyChat by executing the `_**kickstartConvoyChat.bat**_` file found in the `.convoychat` folder.

**For Linux Users**: You can also set up ConvoyChat by executing the below script:

```sh
bash /.convoychat/kickstartConvoyChat.sh
```

**All `package.json` scripts**

Below is a list of all scripts you'll find under the _scripts_ configuration of the `package.json` file in the root folder.

- **Main development scripts**
  - **dev:tsc** - Compiles Typescript code
  - **dev:server** - Runs and watches server for file changes
  - **dev:client** - Runs the client side
  - **develop** - Starts the app by running the above scripts concurrently
- **Tests**
  - **test:server** - Run all tests for server
  - **test:client** - Run all tests for client
- **Codegen & Infra**
  - **codegen** - Runs GraphQL Codegen for client
  - **lint** - Runs ESlint
  - **lint:fix** - Runs ESlint & Fixes,
  - **prettier** - Runs prettier

## <a id="pr-process"></a> 🟡 Pull Request Process

As stated above, all contributions to this project are licensed under the **[GNU General Public License Version 3](/LICENSE.md)**. 

**Working on your first pull request?** You can learn how from this *free* series:

**[How to Contribute to an Open Source Project on GitHub](https://egghead.io/courses/how-to-contribute-to-an-open-source-project-on-github)**

The ConvoyChat project uses **[GitHub's Pull Requests](https://github.com/pulls)** to handle pull requests.

**The project's pull request system is publicly readable --- however, you must have an account registered with GitHub to create a new pull request.**

If you are looking to contribute code to ConvoyChat, pull requests are a nice way to go about doing it. 

For your pull request to be merged faster, we recommend that you read and follow all the guidelines below:

- **Introduce yourself** - A great pull request has an introduction of yourself. It helps the developers know more about you.
- **State your reasons** - Pull requests to the ConvoyChat project must be as descriptive and detailed as possible.
- **Version your PR** - You must be able to provide us with the versions of the main prerequisites so as to be able to carry out testing.
- **Agree to the checkpoints** - No pull request will be allowed without agreeing to the checkpoints.
- **Conclude properly** -  Finally, before you create your pull request, you should write a nice conclusion.

You can create your pull request from the template we provide in the `pull_request_template.md` file or just copy the example below:

```md
## Introduction

Hey there @C-EO!

I'm @johndoe.

In an effort to improve ConvoyChat, I have submitted this pull request for you and the team to have a look at.

## Reasons for Pull Request

This pull request fixes #254 and improves user account security by adding 2fa.

## Status & Version Classification

**NodeJS version**: 12.22.10

**ConvoyChat version**: 1.0.0-beta

**Browser version**: Microsoft Edge - v107.0.1418.62 (Official build) (64-bit)

## Checkpoints

✅ I know how to update typings and have done so (or typings don't need updating).

✅ I agree to follow this project's **Code of Conduct** and **Contributing Guidlines**.


## Conclusion

I hope this pull request helps bring more enhancements to the ConvoyChat project.

Signed by John Doe <john@doe.com>
```

> **Notes**:
> 
> If you want to become one of the ConvoyChat Authors, you will need to have at least **5** accepted pull requests.
> 
> Every pull request you submit is reviewed by the ConvoyChat Authors following our code review process before it is merged.
> 
> It may take considerable time to review a pull request. 

**Documentation**

**Are you looking to improve our documentation?** That's great to hear.

All enhancements to the documentation should be done through a pull request following the above procedures.

## <a id="resources"></a> 📚 Contributor Resources

As a contributor, you'll need certain resources to help you on your journey.

Below is a list of resources that we as the ConvoyChat Authors use:

- [How to Contribute to Open Source](https://opensource.guide/how-to-contribute/)
- [Using Pull Requests](https://help.github.com/articles/about-pull-requests/)

If you have other resources in mind, feel free to open an issue with your suggestion.

## <a id="support"></a> ❓ Contributor Support

If you need any help or have problems with your contribution, please don't hesitate to contact us. You can find us on [GitHub](https://github.com/c-eo/convoychat/discussions) and [Discord](https://discord.gg/BmPNx9jJHD).

You may also reach us at our [email](mailto:convoychat@gmail.com).

**Please read our [support documentation](/docs/oss/support.md) for more info.**


Thank you for your interest in contributing to the ongoing development of the ConvoyChat project.

_**~ ConvoyChat Authors**_

<!-- 
Add tests section
Finish OAuth 2 docs
 -->