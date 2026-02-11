# bull-board-react-router

A bull-board adapter for React Router v7

## Example

Example using @react-router/fs-routes

```ts
// routes/ui.$.tsx
import { createBullBoard } from "@bull-board/api";
import { BullMQAdapter } from "@bull-board/api/bullMQAdapter";
import { ReactRouterAdapter } from "bull-board-react-router";
import { Queue } from 'bullmq';

import type { Route } from "./+types/ui.$";

const queue = new Queue(...)

const serverAdapter = new ReactRouterAdapter();
serverAdapter.setBasePath("/ui");

createBullBoard({
  queues: [new BullMQAdapter(queue)],
  serverAdapter,
});

export const action = async ({ request, context }: Route.ActionArgs) => {
  return serverAdapter.handleRequest(request)
};

export const loader = async ({ request, context }: Route.LoaderArgs) => {
  return serverAdapter.handleRequest(request)
};
```
