# Node.js Server Unresponsiveness During Long Tasks

This repository demonstrates a common issue in Node.js servers: unresponsiveness during long-running requests.  The problem arises from blocking the event loop with synchronous code, preventing the server from handling other requests.

## Problem

The `server.js` file contains a simple HTTP server that simulates a long-running task using a `while` loop.  During this 5-second delay, the server becomes unresponsive to new requests.  This is because Node.js uses a single-threaded event loop, and the blocking synchronous operation prevents the event loop from processing other events (such as incoming requests).

## Solution

The `serverSolution.js` file demonstrates the solution using asynchronous operations (specifically, `setTimeout`).  By delegating the long-running task to `setTimeout`, the event loop remains free to handle other requests, preventing the server from hanging.

## How to Run

1. Clone this repository.
2. Navigate to the directory in your terminal.
3. Run `node server.js` to observe the unresponsive server.
4. Run `node serverSolution.js` to see the improved, responsive server.

This example highlights the importance of using asynchronous programming techniques in Node.js to maintain responsiveness and prevent performance bottlenecks.