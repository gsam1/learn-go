# Custom GO Tutorial

A folder dedicated to my personal go cariculum. It intends to teach me the how to program with go by building a couple of applications.

Go for Builders: A Project-Oriented Curriculum

The application structure should be built out and tests that verify the application.

## Phase 1: The CLI Power Tool
Goal: Master Go’s toolchain, structs, JSON marshaling, and the net/http package.

Instead of a basic weather app, you’ll build a GitHub Issue Tracker. It should allow users to list, view, and create issues on a specific repo from the terminal.

Key Concepts:

Struct tags for JSON parsing.

Using flag or spf13/cobra for command-line arguments.

Environment variables for API tokens.

The Challenge: Implement a "search" feature that caches results locally in a hidden file to limit API hits.

## Phase 2: The Resilient REST Backend
Goal: Learn standard library routing, middleware patterns, and SQL integration.

Build a Task Management API (The classic "Todo" but with a multi-tenant twist).

Key Concepts:

Dependency Injection: Passing your DB connection to handlers without global variables.

Middleware: Authentication, logging, and recovery.

Migrations: Handling schema changes (using golang-migrate).

Database: Use pgx for PostgreSQL; avoid ORMs initially to understand database/sql.

The Challenge: Implement a custom "Middleware" that logs the execution time of every request and rejects requests without a valid X-API-KEY.

## Phase 3: The Distributed Job Scheduler (MQTT)
Goal: Master Concurrency (Goroutines/Channels) and asynchronous messaging.

As requested, you'll build a Distributed Task Runner. A "Producer" sends compute-heavy jobs over MQTT, and one or more "Workers" pick them up, execute them, and report back.

Key Concepts:

The context Package: Managing timeouts and cancellations across the network.

Goroutines & Channels: Handling incoming MQTT messages without blocking the main thread.

Mutexes vs. Channels: Knowing when to use sync.Mutex for shared state.

The Challenge: Ensure "Graceful Shutdown." If you kill a worker, it should finish its current job and disconnect cleanly before exiting.

# Phase 4: The "In-Between" (The Swiss Army Knife)
Goal: Performance profiling and low-level I/O.

Build a Log Aggregator & File Watcher. This tool watches a specific directory, tail-follows new log files, and streams updates to a central dashboard (or simply prints a filtered view).

Key Concepts:

fsnotify for filesystem events.

io.Reader and io.Writer interfaces (the heart of Go).

Benchmarks: Use testing.B to see how much memory your log parser consumes.

The Challenge: Make the parser concurrent—one goroutine watches the file, another parses the lines, and a third handles the output.