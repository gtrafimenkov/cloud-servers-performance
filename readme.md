# Cloud Servers Performance

Practical performance tests of various cloud virtual machines and servers.

## Tests

There are two tests:

- building of linux kernel with `make -j $(nproc)` which tests multicore performance
- bzipping of a 10Gb file which tests single core performance

All dedicated servers participated in the tests had SSD or NVMe drives, unless specified otherwise.  Cloud VMs
had different disks types (SSD, NVMe, locally attached, network attached) depending on a type and the cloud
provider.

## Results

```
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
| Server Type   | CPU                                                     | Cores | Kernel     | 10GB bzip | OS, Linux Kernel      |  Test Date | Approx     |
|               |                                                         |       | build time | time      | Version               |            | cost/month |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
|               |                                                         |       |            |           |                       |            |            |
|               | AWS                                                     |       |            |           |                       |            |            |
|               |                                                         |       |            |           |                       |            |            |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
| t2.micro      | Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz               |     1 |            | 2m5s      | u1604                 |            |            |
| t2.medium     | Intel(R) Xeon(R) CPU E5-2686 v4 @ 2.30GHz               |     2 |            | 1m54s     | u1604                 |            |            |
| t2.large      | Intel(R) Xeon(R) CPU E5-2676 v3 @ 2.40GHz               |     2 |            | 1m56s     | u1604                 |            |            |
| m5.large      | Intel(R) Xeon(R) Platinum 8175M CPU @ 2.50GHz           |     2 |            | 1m43s     | u1604                 |            |            |
|               |                                                         |       |            |           |                       |            |            |
| t3.medium     | Intel(R) Xeon(R) Platinum 8175M CPU @ 2.50GHz           |     2 | 127m15s    | 2m36s     | u1604, 4.4.0-1065-aws | 2018-09-09 | $34.56     |
| t3.2xlarge    | Intel(R) Xeon(R) Platinum 8175M CPU @ 2.50GHz           |     8 | 26m3s      | 2m20s     | u1604, 4.4.0-1065-aws | 2018-09-09 | $276.48    |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
|               |                                                         |       |            |           |                       |            |            |
|               | Google Cloud                                            |       |            |           |                       |            |            |
|               |                                                         |       |            |           |                       |            |            |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
| n1-standard-1 | Intel(R) Xeon(R) CPU @ 2.00GHz                          |       |            | 2m12s     | u1604                 |            |            |
| n1-standard-2 | Intel(R) Xeon(R) CPU @ 2.00GHz                          |       |            | 2m5s      | u1604                 |            |            |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
|               |                                                         |       |            |           |                       |            |            |
|               | Scaleway                                                |       |            |           |                       |            |            |
|               |                                                         |       |            |           |                       |            |            |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
| C2M           | Intel(R) Atom(TM) CPU  C2750  @ 2.40GHz                 |     8 | 54m10s     |           | u1604                 | 2018-09-09 | €17.99     |
| Start1-L      | Intel(R) Atom(TM) CPU C3955 @ 2.10GHz                   |     8 | 43m17s     |           | u1604                 | 2018-09-09 | €15.99     |
| X64-15GB      | Intel(R) Xeon(R) CPU D-1531 @ 2.20GHz                   |     6 | 23m11s     |           | u1604                 | 2018-09-09 | €24.99     |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
|               |                                                         |       |            |           |                       |            |            |
|               | Hetzner Cloud                                           |       |            |           |                       |            |            |
|               |                                                         |       |            |           |                       |            |            |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
| CX51          | Intel Xeon Processor (Skylake, IBRS)                    |     8 | 26m40s     | 2m0s      | u1604                 | 2018-09-09 | €35.28     |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
|               |                                                         |       |            |           |                       |            |            |
|               | Hetzner Dedicated                                       |       |            |           |                       |            |            |
|               |                                                         |       |            |           |                       |            |            |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
| EX51-SSD      | Intel(R) Core(TM) i7-7700 CPU @ 3.60GHz (SMT on)        |     8 |            | 1m10s     | u1604                 |            | €51.92     |
| EX61-NVMe     | Intel(R) Core(TM) i7-8700 CPU @ 3.20GHz (SMT on)        |    12 | 11m33s     | 1m3s      | u1604                 | 2018-09-09 | €63.72     |
| PX121-SSD     | Intel(R) Xeon(R) CPU E5-1650 v3 @ 3.50GHz (SMT on)      |    12 | 15m52s     | 1m25s     | u1604                 | 2018-09-09 | €137.84    |
| PX61-NVMe     | Intel(R) Xeon(R) CPU E3-1275 v5 @ 3.60GHz (SMT on)      |     8 |            | 1m24s     | u1604                 |            | €63.72     |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
|               |                                                         |       |            |           |                       |            |            |
|               | packet.net                                              |       |            |           |                       |            |            |
|               |                                                         |       |            |           |                       |            |            |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
| c2.medium.x86 | AMD EPYC 7401P 24-Core Processor (SMT on)               |    48 | 5m43s      | 1m54s     | u1604, 4.4.0-134      | 2018-09-09 | $720       |
| c2.medium.x86 | AMD EPYC 7401P 24-Core Processor (SMT on)               |    48 | 5m41s      | 1m54s     | u1604, 4.18.6         | 2018-09-09 | $720       |
| c2.medium.x86 | AMD EPYC 7401P 24-Core Processor (SMT off)              |    24 | 6m53s      | 1m54s     | u1604, 4.18.6         | 2018-09-09 | $720       |
|               |                                                         |       |            |           |                       |            |            |
| m1.xlarge.x86 | 2 x Intel(R) Xeon(R) CPU E5-2650 v4 @ 2.20GHz (SMT on)  |    48 | 5m47s      | 1m46s     | u1604, 4.4.0-134      | 2018-09-09 | €1224      |
| m1.xlarge.x86 | 2 x Intel(R) Xeon(R) CPU E5-2650 v4 @ 2.20GHz (SMT on)  |    48 | 5m56s      | 1m41s     | u1604, 4.18.6         | 2018-09-09 | €1224      |
| m1.xlarge.x86 | 2 x Intel(R) Xeon(R) CPU E5-2650 v4 @ 2.20GHz (SMT off) |    24 | 6m58s      | 1m43s     | u1604, 4.18.6         | 2018-09-09 | €1224      |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
|               |                                                         |       |            |           |                       |            |            |
|               | Various Dedicated                                       |       |            |           |                       |            |            |
|               |                                                         |       |            |           |                       |            |            |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
|               | 2 x Intel(R) Xeon(R) CPU E5-2690 v2 @ 3.00GHz (SMT off) |    20 | 8m9s       | 1m45s     | u1604                 | 2018-09-09 |            |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
|               |                                                         |       |            |           |                       |            |            |
|               | Various Dedicated with HDD drives                       |       |            |           |                       |            |            |
|               |                                                         |       |            |           |                       |            |            |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
|               | Intel(R) Core(TM) i7-2600 CPU @ 3.40GHz (SMT on)        |     8 | 21m45s     | 1m34s     | u1604, 4.17.19        | 2018-09-09 |            |
|               | Intel(R) Core(TM) i7-4770 CPU @ 3.40GHz (SMT on)        |     8 | 27m49s     | 1m18s     | u1604, 4.17.19        | 2018-09-09 |            |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
|               |                                                         |       |            |           |                       |            |            |
|               | Various Personal                                        |       |            |           |                       |            |            |
|               |                                                         |       |            |           |                       |            |            |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
| Laptop        | Intel(R) Core(TM) i3-3120M CPU @ 2.50GHz (SMT on)       |     4 | 81m35      | 2m10s     | u1804, 4.18.6         | 2018-09-09 |            |
|---------------+---------------------------------------------------------+-------+------------+-----------+-----------------------+------------+------------|
```

## Test Commands

```
git clone https://github.com/gtrafimenkov/recent-stable-kernel.git && cd recent-stable-kernel
git reset --hard 4.18.6 && git clean -fdx && ./build-kernel.sh 4.18.6
```

```
time (dd if=/dev/zero bs=1024 count=10485760 | bzip2 -c >/dev/null)
```

## Operating Systems

- u1604 - Ubuntu 16.04
- u1804 - Ubuntu 18.04

## License

MIT
