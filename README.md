# PersonalMediaVault website

This is a product and documentation website made for [PersonalMediaVault](https://github.com/AgustinSRG/PersonalMediaVault).

Powered by [Hugo](https://gohugo.io/) and [Docsy](https://www.docsy.dev/).

## Requirements

 - [Golang](https://go.dev/), latest stable version
 - [NodeJS](https://nodejs.org/en), latest stable version

## Installation

In order to install dependencies, type:

```sh
npm install
```

## Running development server

In order to run a development server, run the following command:

```sh
npm run serve
```

## Changing content

The content is placed into the [content folder](./content/), each language inside its own sub-folder.

Read the [Docsy documentation](https://www.docsy.dev/docs/) for more information on how the content is interpreted to make the website.

## Building website

In order to build the website, run the following command:

```sh
npm run build
```

The website will be placed in the `public` folder.

