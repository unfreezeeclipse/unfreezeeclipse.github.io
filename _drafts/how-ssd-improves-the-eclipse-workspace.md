---
layout: post
title:  "How SSD Improves the Eclipse Workspace"
date:   2016-07-03 10:30:00 +0300
---

In a [previous post](post-url-link) we have seen that SSD drives improve the Eclipse startup time.

Can we expect similar performance boost for other tasks in Eclipse? Let's have a look!

Today I executed a more complex test. I imported some large projects in the workspace. I measured how long does Eclipse take to process them: parsing, indexing, validation, etc.

## Setup

Again, I used my 3+ years old Lenovo T430 laptop. It runs Fedora 24 and has:

* Intel i7-3520M CPU @ 2.90GHz
* 16 GB RAM
* 240 GB SSD Kingston SV300S37A240G
* 1 TB HDD WD Blue WD10JPVX

I had two Eclipse IDE setups:

1. An Eclipse Che Development Environment setup as described in the [Eclipse Che documentation](https://eclipse-che.readme.io/v4.4/docs/setup-che-workspace#author-extension-using-the-eclipse-ide). The workspace included the complete Che source code and dependencies: 71,146 items, totalling 1.7 GB.
2. An Eclipse for PHP Developers. The workspace included the Magento Community Edition: 62,878 items, totalling 488.4 MB.

Both installations had a separate copy on the SSD and on the HDD. I also included the Oracle JRE 1.8.0_92 in the Eclipse installation. The HHD copy of the Eclipse Che Development Environment used a local Maven repository on the HDD.

These extra configurations aimed to reduce the reading from the SSD when Eclipse on the HDD was used.

The test consisted of the following steps:

1. Restart the IDE.
2. Wait for all background jobs to finish.
3. Trigger the Garbage Collector.
4. Clean the disk cache.
5. Execute Project > Clean. Start the clock.
6. Watch the Progress view and wait for all background jobs to finish. Stop the clock.

I executed the above test 3 times for each installation and took the average time. I ensured that all networking, like downloading dependency, finished before running the tests.

## Results

| Installation                        | SSD            | HDD            | Ratio |
|:----------------------------------- | --------------:| --------------:| -----:|
| Eclipse Che Development Environment | 1:36&nbsp;mins | 2:21&nbsp;mins | 1.47x |
| Eclipse for PHP Developers          | 0:40&nbsp;mins | 1:44&nbsp;mins | 2.60x |

## Conclusion

As we can see, SSD gives a noticeable advantage over HDD when processing the project's code. The actual improvement depends on each use case. It can be just as low as 30% faster, or it can go up to more than 2 times faster. In any case, switching from HDD to SSD can only make things go faster.
