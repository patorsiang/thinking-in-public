# BKK.js summer 2026

Cr. <www.facebook.com/share/v/1DLp4BWZfj>

## game Engine on the web: how hard could it be?

by phoomparin mano

- js already have a audio, canvas, and messaging engine and it is async await then it have to wait the previous process first, but game engine it has to use them in parallel.
- off screen canvas
- DAG + toposort = render graph.
  - DAG -> non start and end point graph
  - and sort that graph
- OffscreenCanvas + WebGL2Context
  - Frame buffer object
  - cons: many previews singconization store
  - solve by PBO + fenceSync: Async Pixel Read
  - everything should not run in main thread
    - it have to run on worker
      - but it have to be clean and simple
    - WebAssembly + web worker
      - use web workers run on WebAssembly
      - like ML worker (normally it heavy to run on web but bring it to web worker and WebAssembly might be work, tensorflow on web, )
- Web serial -> use to connect with hardware

ref: github.com/heypoom/patchies

my feeling: <I want to learn to code on webassambly as well>

## WebMCP

by warat wongmmanneekit

- WebMCP tool inspector
- like frontend provide javascript for AI to call directly especially.
- have code have to use cloud AI, it can integrate with on-device AI to work with utilize task.
- it have still have doubts and if model is better and more efficient it will not necessary to apply.
- skill and mcp is still mass it should be make it more structure don't have to having tech much.
- AI will be more and more effective; it might be replace me.

## Vibe Coding without leaving tech debt

by thada wangthammang

- Current:
  - vibe code by AI like Claude code
  - it make the working period from several month to 3 weeks by all code is coded by AI.
- Why it leave tech debt
  - technique such as
    - no architecture
    - no design pattern
    - no doc
    - context overload
  - mindset
    - wanting things to be done quickly actually makes the work worse. -- brain fatigue - tired
      - previous: routine fatigue
      - current strategic fatigue
    - decision direction = every prompt is the decision.
      - when you are hurried -> take just a little bit time with prompt (direction) -> it will left a tech debt
      - leave refactor for tomorrow?
    - decision such as
      - using clean architecture
      - using microservice
  - solution
    - set up system to replace making decision
    - triangle
      - rule:
        - tell AI everything that it have to do - spec, context, goal, verify
        - set it as template
          - such as <github.com/thaitype/thaitype-stack-mongodb-template>
        - if the rule is not clear - bad enforce rule
          - example:
            - type-level: AI is better on value level
              - <type-level-typescript.com>
              - if we want type-safe - set in rule
              - zod is fix type with their schema (hard to change - typebox)
              - how to enforce clean architecture
                - matches function -> match zod with
          - setup doc
            ![docs](/assets/image.png)

            ![topic of design pattern](/assets/image-1.png)

            ![topic of architecture](/assets/image-2.png)
          - checking !!!
            - type
            - lint
            - format
            - unit test
        - if we don't have a clear rule; the cost of refactor will high
        - but if template set the clear structure, it will save cost.
      - human
        - externalize: take the decision out of our head -> don't make your prompt make AI to work out-of-scope
        - chief agent framework <github.com/thaitype/chief-agent-framework>
          - example of usecase:
            - suggestion decision - suggest spec <in our team use gemini to review>
            - duplication rule
            - like design of project a and b is not the same ask the dev first which one is the correct direction.
            - make the agent notice that the things the it is doing is positive or negative is the error of unit test lower and lower
              - if it negative return to ask dev again
          - example of skill <github.com/mattpocock/skills/blob/main/grill-me/SKILL.md>
            - help dev to deep in your idea
      - AI: select tool
        - using argentic coding, orchestrator + automatic feedback from outside

## Bun, Typescript, Postgres: Build a reliable Event-Driven Application without Kafka, RabbitMQ, or Mosquito

by Dheerapat tookkane

- using worker instead of message broker
  - but multi worker may be cause of race condition
    - Postgress provide
      - notify / listen
      - select ... for update skip lock
    - lib: timgit/pg-boss
    - superbaseQ is base on this lib but have to  event bus by yourself
      - PGBoss like vitual queue
    - PGBoss connect to Postgress to publish event
    - BYOD: bring your own database idea
    - query builder? ORP?
    - kysely transaction to make pgboss use the same transaction with kysely
    - elysia app for eventHandler
    - PGBossEventBus to bridge
    - tools using to dev
      - Bruno Doc
      - Neovim
  - pros:
    - transactional consistency out of the box
    - idea for low to medium traffic with simple event handling
    - low complexity , low ops cost
    - effortless scaling, no race conditions for free
  - cons:
    - bottleneck by postgresql IOP
    - Not build for high-throughput event handling
    - event sourcing is theoretically possible, but painful in practice
    - poor fit for polyglot environments
    - small, limited community

## fully type safe from server to client

by Kongkeit khynpanitchot

- type awere
  - tRPC
    - type server -> client (e2e type safety)
    - JSON RPC (no file upload etc)
    - API documentation is hard
    - lack "real"api server capability
  - old framework like express.js can do type server -> client check
  - suggest: which can check type from server to client and restAPI
    - Elysia: 2x faster in type inference, and api doc easy
    - Hono
  - if your server code change, knows it at exact line
  - type safe for code and database
    - such as drizzle prisma and kysely
  - dedicated schema -> type box -> elelysia validation
  - elysia + openAPI = API doc
