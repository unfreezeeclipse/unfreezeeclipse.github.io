---
layout: post
title:  "How SSD Improves Eclipse Startup Time"
date:   2016-07-02 11:30:00 +0300
---
[Solid State Drives](https://en.wikipedia.org/wiki/Solid-state_drive) (SSD) have been around for years. They have already proved to be faster than the classic [Hard Disk Drives](https://en.wikipedia.org/wiki/Hard_disk_drive) (HDD). There are many articles explaining why. Here is [a good one](http://www.storagereview.com/ssd_vs_hdd) in case you want to get a basic understanding.

You may ask yourself what advantage does SSD gives over HDD for Eclipse in particular?

A usual Eclipse installation consists of thousands of files. Some of them are rather big (a few megabytes), but most of them are small. Similar is the situation with the Eclipse workspace. The metadata spreads across hundreds and thousands of small files. Code projects that you import into the workspace usually consists of tons of small files too. Large projects may grow to thousands and even more files.

Using Eclipse means working with tons of small files. Here we would expect the SSD excellence to shine. Accessing lots of files in short time is slow for HDD drives. Their read/write head has to jump from file to file across the platter. This takes time and slows down the I/O performance. The lack of moving parts in SSD drives saves this extra time.
So, we can expect significant performance improvement if we switch from HDD to SSD.

Today I executed a small performance test. I measured the Eclipse startup time when installed on an HDD and on an SSD.

## Setup

I used my 3+ years old Lenovo T430 laptop that runs Fedora 24.

The hardware configuration is:

* Intel i7-3520M CPU @ 2.90GHz
* 16 GB RAM
* 240 GB SSD Kingston SV300S37A240G
* 1 TB HDD WD Blue WD10JPVX

I used two Eclipse installations:

* The Eclipse IDE for Java Developers (4,530 files)
* The Eclipse IDE for Java EE Developers + JBoss Tools + Everything from the Red Hat Central (23,701 files)

Both installations had a separate copy on the SSD and on the HDD. I also included the Oracle JRE 1.8.0_92 in the Eclipse installation. The latter was necessary to avoid loading the JRE from the SSD when starting Eclipse from the HDD.

I did a warmup start of each installation before the test. As part of the test, I did 3 launches of each installation and took the average startup time. I measured the time between executing the Eclipse binary and displaying the workbench. Before each launch I cleaned the disk cache.

The setup is not as perfect as a real performance lab, but good enough for this test.

## Results

| Installation                  | SSD     | HDD     | Ratio |
|:----------------------------- | -------:| -------:| -----:|
| Eclipse Java                  | 9.97 s  | 24.60 s | 2.47x |
| Eclipse Java EE + JBoss Tools | 12.11 s | 30.43 s | 2.51x |

## Conclusion

As shown on the above table, starting Eclipse on SSD is 2.5 times faster than on HDD.

Of course, the results may vary on a different setup. Remember also that at the time of writing this post my hardware is already 3+ years old. Storage drives may have improved since then. I would actually expect that, as a new technology, SSD improves faster than HDD. Switching today from HDD to SSD may give you even higher performance gain than I have measured.
