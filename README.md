# RAG-SEARCH

A small TypeScript experiment that retrieves context from a Langbase memory and sends it to a Langbase support pipe.

## Request flow

1. `create-memory.ts` creates the `knowledge-base` memory with `openai:text-embedding-3-large`.
2. `create-pipe.ts` creates the `ai-support-agent` pipe.
3. `agents.ts` retrieves up to four memory results and adds their text to a system prompt.
4. `index.ts` sends a sample question through the retrieval and response flow.

The prompt asks the model to cite sources by number. The code does not number the retrieved chunks before it adds them to the prompt. `upload-docs.ts` is empty, so this repository does not include a document upload flow.

## Requirements

- Node.js and npm
- A Langbase API key
- A Langbase memory named `knowledge-base`
- A Langbase pipe named `ai-support-agent`

## Set up

Install the declared packages:

```sh
npm install
```

Create a `.env` file in the repository root:

```dotenv
LANGBASE_API_KEY=your-langbase-api-key
```

Create the Langbase memory and pipe, then run the example:

```sh
npx --yes tsx create-memory.ts
npx --yes tsx create-pipe.ts
npx --yes tsx index.ts
```

The scripts create remote resources in your Langbase account. Run each setup command only when you want to create that resource. The `tsx` runner is not a project dependency. `npx` can download it when needed.

## Current limits

This repository is a starter experiment. It has no configured build command or automated test suite. Its `npm test` script is a placeholder that exits with an error.

The package metadata lists the ISC license.
