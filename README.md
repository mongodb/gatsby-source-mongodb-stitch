## MongoDB Stitch Source Plugin for Gatsby

## Description

This source plugin serves as a simple wrapper for MongoDB Stitch access within Gatsby. Specifically, the plugin calls a number of supplied `functions` at build-time to gather nodes.

This plugin expects the result type from stitch to be an array of objects, where each object will be a node in Gatsby.

TODO: Support authentication-required applications.

### Learning Resources (optional)

For help setting up a serverless architecture in MongoDB Stitch, feel free to [consult the docs](https://docs.mongodb.com/stitch/).

## How to install

Install via your selected package manager, i.e.:

`npm install gatsby-source-mongodb-stitch` or `yarn add gatsby-source-mongodb-stitch`.

## Available options

| option      | required? | description                                                                                                                |
| ----------- | --------- | -------------------------------------------------------------------------------------------------------------------------- |
| `stitchId`  | Yes       | The ID of your MongoDB Stitch Application                                                                                  |
| `functions` | Yes       | An array of function calls to execute via Stitch. Each element of `functions` is to be an object with the below properties |
|             |           |                                                                                                                            |

### Functions

Each supplied function should have the following properties:

| option        | required? | description                                                         |
| ------------- | --------- | ------------------------------------------------------------------- |
| `name`        | Yes       | The name of the function to call                                    |
| `args`        | No        | An array of arguments to invoke the function `name` with            |
| `resultType`  | Yes       | The type to use for resulting nodes                                 |
| `getResultId` | No        | A function to get the `id` for a result document (default is `_id`) |

## Examples of usage

Once installed, register the plugin by adding to `plugins` in `gatsby-config`:

```javascript
{
    resolve: 'gatsby-source-mongodb-stitch',
    options: {
        stitchId: /* stitch-app-id */,
        functions: [
            {
                name: /* function-name */,
                args: [/* some-function-args */],
                resultType: /* result-node-type*/,
                getResultId: /* document => document._id (or some unique ID) */,
            },
        ],
    },
},
```

## How to query for data (source plugins only)

You will be able to query for the type specified as the `resultType` for that function after the `sourceNodes` step is complete.

## How to develop locally

1. Clone this repository
2. Develop on a feature branch
3. Open a pull request with your feature branch against `master`

## How to contribute

Feel free to leave issues or pull requests for this plugin!
