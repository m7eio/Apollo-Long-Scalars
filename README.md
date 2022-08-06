# Apollo Long Scalars

This is external scalar for Apollo server. Support Long type.

Long integer type for Apollo server. This package provides 2 implementation options for working with large integers.

## First implementation

This implementation allows working with only 53 bit integers. To work in the 53-bit number mode, you need to create an instance of the GraphQLBigInt class and pass the string "safe" to the constructor.

Example:
```typescript
import { makeExecutableSchema } from "graphql-tools";
import Long from "@m7eio/apollo-long-scalars";

const typeDefs = `
scalar Long

type Query {
  Test: Long
}
`;

const resolvers = {
	Long: new Long("safe")
};

export default makeExecutableSchema({ typeDefs, resolvers });
```

## Second implementation

The second implementation allows you to work with 63 bit integers using a new data type in JavaScript - BigInt. To work in this mode, you need to create an instance of the GraphQLBigInt class and pass the "bigInt" to the constructor for the term.

Example:

```typescript
import { makeExecutableSchema } from "graphql-tools";
import Long from "@m7eio/apollo-long-scalars";

const typeDefs = `
scalar Long

type Query {
  Test: Long
}
`;

const resolvers = {
	Long: new Long("bigInt")
};

export default makeExecutableSchema({ typeDefs, resolvers });
```