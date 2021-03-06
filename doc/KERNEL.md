# Kernels

## Available OpenCL kernels

See directory `kernel`.


## Parameter configuration

### Common

In general, switching kernels requires reconfiguring mining parameters,
such as (but not necessarily limited to) `thread-concurrency`, `intensity`,
`gpu-engine` and `gpu-memclock`.

A description of how to do this is available in `doc/MINING`.


### alexkarnew

Alexey Karimov's optimised kernel, based on `ckolivas`. For Catalyst >=13.4.

Only supports `vectors=1`.

[Announcement](https://litecointalk.org/index.php?topic=4082.0).


### alexkarold

Alexey Karimov's optimised kernel, based on `ckolivas`. For Catalyst <13.4.

Only supports `vectors=1`.

[Announcement](https://litecointalk.org/index.php?topic=4082.0).


### ckolivas

The original Colin Percival `scrypt` kernel, maintained for a long time by
Con Kolivas in `cgminer` and renamed to reflect the fact.

Only supports `vectors=1`.


### psw

Pavel Semjanov optimised kernel, SHA256 speedups.

[Announcement](https://bitcointalk.org/index.php?topic=369858.0).


### zuikkis

Zuikkis' optimised kernel, based on `ckolivas`.

Only supports `vectors=1`, `lookup-gap=2` and `worksize=256`.

[Announcement](https://litecointalk.org/index.php?topic=6058.msg90873#msg90873).


## Submitting new kernels

### Requirements

* OpenCL source code only, licenced under GPLv3 (or later).
* Not hard-coded for a specific GPU model or manufacturer.
* Known limitations and any specific configuration quirks must be mentioned.


### Procedure

1. Copy the kernel you wish to modify, change the file encoding to UTF-8
and commit it without any further modifications.

This way, it is easy to verify that there are no hidden changes. Note in
the commit message which kernel is used as a base.

2. Make changes to the kernel. Commit them.

This allows to produce a diff that makes sense.

3. Search for KL_CKOLIVAS and CKOLIVAS_KERNNAME in the top-level source
directory and make additions to the listed files in order to integrate
the new kernel.

Now it can be selected when starting via the `--kernel` argument or
`kernel` configuration option.

4. Recompile and test that the kernel actually works.

5. Add yourself to the "kernels" section in `AUTHORS.md`. Keep it short.

6. Submit a pull request on GitHub, or file it at the issue tracker,
outlining the changes made, known limitations, and tested GPUs. List
your git repository and branch name. The current repository and issue
tracker links should be in `README.md`.
