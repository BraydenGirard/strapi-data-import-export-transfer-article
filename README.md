# Importing, Exporting, and Transferring Data with the Strapi CLI

> Learning how to use the import, export, and data transfer options in the Strapi CLI to migrate data.

As a developer working with Strapi in the past, there have been many scenerios where I wished I could have easily taken a backup of my data. To be able to export my data from one Strapi instance and then been able to import it back to another Strapi instance when needed was a frequent chore. Thanks to the Strapi CLI this is now a trivial task. In this article we will show how you can export your data from one instance and then import it again to another instance with a couple simple commands.

While importing and exporting data is useful, sometimes you just want to push or pull data you already have in a local Strapi instance to a remote Staging instance. You also may want to pull production data down to a local Strapi instance for testing. This is where the data transfer commands come in handy. We will also demonstrate how to use these commands in the Strapi CLI as well.

Read on to learn how to use the import, export, and data transfer options in the CLI.

## Prerequisites

Before you can jump into this content, you need to have a basic understanding of the following.

1. Basic knowledge of JavaScript
2. A Node.js ready environment
3. Basic understanding of Strapi - get started here

## What is Strapi

Strapi is an open-source headless CMS based on Node.js that is used to develop and manage content using a Restful API and/or GraphQL.

With Strapi, we can scaffold our API faster and consume the content via APIs using any HTTP client or GraphQL enabled frontend.

## Scaffolding a Strapi project

To scaffold a new Strapi project is very simple and works precisely as installing a new frontend framework.

We are going to start by running the following commands and testing them out in our default browser.

```javascript
npx create-strapi-app strapi-api --quickstart
# OR
yarn create strapi-app strapi-api --quick start
```

The command above will scaffold a new strapi project in the directory you specified.

Next, run yarn build to build your app and yarn develop to run the new project if it doesn't start automatically.

The last command will open a new tab with a page to register your new admin of the system. Go ahead and fill out the form and click on the submit button to create a new Admin.

## Using the Strapi CLI Export then Import

In this example we are going to be using the Strapi blog template as a starter. We have one project that is populated with the starter data and then another project with **the same schema** but no data. 

It is important to note that your schemas have to match in order for the Strapi data import / export CLI commands to succeed. Another important thing to note is that Strapi will not copy over admin users, API tokens, or third party content,  strictly files and content within the Strapi instance. 

In our start blog you can see our two projects below, first our project which has content and second our other project that currently does not have any content.

[Image of Strapi project with content]

[Image of Strapi project without content]

The first thing we have to do is export the content from our populated instance. There are many options that can be applied to this CLI command but we will just stick to the basics in this example. You can see a full list of CLI commands in [the documentation](https://docs.strapi.io/dev-docs/data-management/export).

[Image of export command]

Now that we have exported our data and encrypred the export, we can now move over to our empty project. In the console for our empty project we will import this data by running the following commands from the CLI. Again, further options can be found in [the documentation](https://docs.strapi.io/dev-docs/data-management/import).

[Image of import]

And just like that we now have our content form our local environment replicated in our remote staging environment. Below is a screenshot again of first our local environment and second our remote staging environment except this time after using the Strapi CLI export and then import features.

[Image of project with Strapi content]

[Image of other project with Strapi content]

## Pushing Data to a Remote with Strapi Transfer

Next, we will use the same Strapi blog template project to demonstrate how we can push our local content to a remote project (our staging environment). In order to do this, we first have to get an authorization token from our remote project. This token will be a push token which will allow us to push data into the remote instance. You can create this token in the Strapi admin as shown below.

[Image of push token]

Now that we have our push token, we can run the Strapi transfer CLI command. Again, before this is run you must make sure that the schema of your local project and the schema of your remote project match. In this case they do as both projects are the Strapi Blog Template except our remote is missing the start content. Below you can see us run the transfer command. For all the options of the transfer command you can [read the docs](https://docs.strapi.io/dev-docs/data-management/transfer).

[Image of data transfer in CLI]

And just like that, we have our data from our local environment pushed into our remote! It's really that easy. Below is a screenshot of first our local environment and second our remote.

[Local content]

[Remote content]


## Wrap Up

From our examplese above you can see that both the import and export CLI features as well as the data transfer CLI features are welcoming additions to the Strapi CLI. When you need to create a backup for an archive or simply to import to another project, the Import and Export features of the Strapi CLI should be your go to. Likewise, if you want to push or pull data to or from a remote instance, the Strapi CLI Transfer feature should be your go to. I hope you enjoyed this article, thanks for reading. 
