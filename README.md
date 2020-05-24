# Server-Side Programming Languages/Runtimes non-TLDR Guide

## Intro

Most programming languages/runtimes can be divided into 4 categories of speed.

1. Very Fast
2. Fast
3. Fast (with caveats)
4. Slow

All languages/runtimes in a given category will perform comparably to each other, while languages from another category will be an order of 
magnitude faster or slower (with the exception of `Fast` and `Fast (with caveats)` which will operate comparably once the program is operating at full capacity).

---

## Categories

| Category | Languages/Platforms | Category Description |
| -- | -- | -- |
| `Very Fast` | C, C++, Rust | Languages in this category are all compiled to native machine code and require manual memory management. These properties make this class of programs insanely fast during runtime (and have a very small final artifact), but adds a sizeable development overhead due to the high learning curve of these languages |
| `Fast` | Go, Swift | Languages in this category gain significant performance from static typing, while retaining nice features like memory management built into the runtime. They are fast, and can be compiled into a static binary just like the `Very Fast` category of languages leading to no-dependency artifacts and good performance. These languages are significantly less cumbersome to work with over `Very Fast` languages . |
| `Fast (with caveats)` | JVM Languages (Java, Scala, Kotlin, Groovy, Clojure), C#, NodeJS, Cython |
These languages leverage the use of a cross-platform virtual machines, or selective native C/C++ compilation during runtime.
Hence, they cannot be deployed in a zero runtime environment like `Very Fast` and `Fast` languages (due to having to package a dependency like a JVM, or node/npm).<br />
Furthermore, although while running at full speed, they can usually match the runtime performance of `Fast` languages,
`Fast (with caveat)` languages suffer from lengthy cold-start times because they make heavy use of
just in time compilation (JIT).
This means in order to achieve speeds comparable to the `Fast` family of languages, further optimization needs to occur during the startup phase of a `Fast (with caveat)`.<br />
This means that these languages are somewhat unsuited to run in a microserviced environments where sub-millisecond application scaleout/scalein times are crucial to optimize cost/performance of systems running in cloud infrastructure. |
| `Slow` | Python, Ruby, Perl,  | These languages are the easiest to develop in, but have no place in high-performance computing contexts. Furthermore, they are also unsuited to deploy in microservices because they are interpreted languages that require an interpreter inside the execution environment |

## Languages that do not fit this model
1. Crystal [https://github.com/crystal-lang/crystal](https://github.com/crystal-lang/crystal): Ruby syntax, C speed. Very promising
2. V-Lang [https://vlang.io/](https://vlang.io/): Go-like syntax, C speed.
