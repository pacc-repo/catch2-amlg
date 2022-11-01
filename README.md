<a id="top"></a>

## Catch2 Amalgamated

This repository contains amalgamated version of Catch2 for easy use with [pacc](https://github.com/PoetaKodu/pacc).

## Installation and usage

Install it with:

```sh
pacc install catch2-amlg
```

then include it in your project:

```cpp
// use the following include
#include <Catch2/catch_amalgamated.hpp>

```

## What is Catch2?

<hr/>
🟣 The following content was copied from the original repository. 🟣
<hr/>
<br/>

Catch2 is mainly a unit testing framework for C++, but it also
provides basic micro-benchmarking features, and simple BDD macros.

Catch2's main advantage is that using it is both simple and natural.
Test names do not have to be valid identifiers, assertions look like
normal C++ boolean expressions, and sections provide a nice and local way
to share set-up and tear-down code in tests.

**Example unit test**
```cpp
#include <catch2/catch_test_macros.hpp>

#include <cstdint>

uint32_t factorial( uint32_t number ) {
    return number <= 1 ? number : factorial(number-1) * number;
}

TEST_CASE( "Factorials are computed", "[factorial]" ) {
    REQUIRE( factorial( 1) == 1 );
    REQUIRE( factorial( 2) == 2 );
    REQUIRE( factorial( 3) == 6 );
    REQUIRE( factorial(10) == 3'628'800 );
}
```

**Example microbenchmark**
```cpp
#include <catch2/catch_test_macros.hpp>
#include <catch2/benchmark/catch_benchmark.hpp>

#include <cstdint>

uint64_t fibonacci(uint64_t number) {
    return number < 2 ? 1 : fibonacci(number - 1) + fibonacci(number - 2);
}

TEST_CASE("Benchmark Fibonacci", "[!benchmark]") {
    REQUIRE(Fibonacci(5) == 5);

    REQUIRE(Fibonacci(20) == 6'765);
    BENCHMARK("Fibonacci 20") {
        return Fibonacci(20);
    };

    REQUIRE(Fibonacci(25) == 75'025);
    BENCHMARK("Fibonacci 25") {
        return Fibonacci(25);
    };
}
```

## Catch2 v3 has been released!

You are on the `devel` branch, where the v3 version is being developed.
v3 brings a bunch of significant changes, the big one being that Catch2
is no longer a single-header library. Catch2 now behaves as a normal
library, with multiple headers and separately compiled implementation.

The documentation is slowly being updated to take these changes into
account, but this work is currently still ongoing.

For migrating from the v2 releases to v3, you should look at [our
documentation](docs/migrate-v2-to-v3.md#top). It provides a simple
guidelines on getting started, and collects most common migration
problems.

For the previous major version of Catch2 [look into the `v2.x` branch
here on GitHub](https://github.com/catchorg/Catch2/tree/v2.x).


## How to use it
This documentation comprises these three parts:

* [Why do we need yet another C++ Test Framework?](github.com/catchorg/Catch2/blob/devel/docs/why-catch.md#top)
* [Tutorial](github.com/catchorg/Catch2/blob/devel/docs/tutorial.md#top) - getting started
* [Reference section](github.com/catchorg/Catch2/blob/devel/docs/Readme.md#top) - all the details


## More
* Issues and bugs can be raised on the [Issue tracker on GitHub](https://github.com/catchorg/Catch2/issues)
* For discussion or questions please use [our Discord](https://discord.gg/4CWS9zD)
* See who else is using Catch2 in [Open Source Software](docs/opensource-users.md#top)
or [commercially](docs/commercial-users.md#top).