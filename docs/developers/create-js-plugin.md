---
id: create-js-plugin
title: Create a JavaScript Plugin
---

- JS Plugin
- - Description: ...
- - Steps:
- - - Setup (w3 create)
- - - Define schema
- - - Import & List Web3API imports
- - - Implement schema's functions
- - - - Wrap an existing SDK
- - - Build Plugin Package
- - - Test With Web3ApiClient

In this guide, we'll walk you through a JavaScript plugin that you can build into your Web3API.

> Note: Plugins do not retain all of Web3API's benefits. We recommend re-writing your existing SDKs as WebAssembly-based Web3APIs.

## **Getting started**

To get started, use the following command to spin up a project folder for your plugin.

```
npx w3 create plugin typescript my-plugin
```

Here are the files in the project folder that we'll focus on:

```
index.ts                      # Implementation of the plugin
manifest.ts                   # API's schema, dependencies, abstract APIs
resolvers.ts                  # Resolvers for GraphQL schemas
schema.graphql                # GraphQL schema for queries / mutations
```

Let's take a look at each of these files.

### **`schema.graphql`**

This file contains the set of types which completely describe the set of possible data you can query on a GraphQL service. Then, when queries come in, they are validated and executed against that schema.

In the file, we have `type Query` and `type Mutation`.

```js
type Query {
  sampleQuery(query: String!): String!
}

type Mutation {
  sampleMutation(data: Bytes!): SampleResult!
}
```

### **`resolvers.ts`**

> ### 🚧 Under Construction

This file contains the resolvers.

```js
import { SamplePlugin } from '.';

import { PluginModule } from '@web3api/core-js';

export const query = (plugin: SamplePlugin): PluginModule => ({
  sampleQuery: async (input: { query: string }) => {
    return await plugin.sampleQuery(input.query);
  },
});

export const mutation = (plugin: SamplePlugin): PluginModule => ({
  sampleMutation: async (input: { data: Uint8Array }) => {
    return await plugin.sampleMutation(input.data);
  },
});
```
