---
layout: page
title: About me
---

<p class="message">
  Hi there!
  I'm Javier :wave:, a <em>HPC software engineer</em> and <em>Ph.D. in Computer Science and Technology</em> based in Madrid (Spain), passionate about C++, OS internals, and compiler design / implementation.
</p>

Formerly, I was working in the CERN [EP/SFT](https://ep-dep-sft.web.cern.ch/) (SoFTware for experiments) group.  Specifically, most if not all of my work in 2020&ndash;2023 was happening under the [ROOT project](https://root.cern/) umbrella.
ROOT is an open-source data analysis framework written mostly in C++ and developed mainly at CERN.
ROOT was designed for high-energy physics (HENP) data analysis, but it is known to be also used in other domains, e.g. astronomy, bio-informatics, finances, etc.
Among other components, ROOT provides columnar data storage (via TTree / RNTuple) and a C++ interpreter based on clang and LLVM.

My primary work areas at ROOT were:

- [RNTuple](https://github.com/root-project/root/tree/master/tree/ntuple/v7), the ROOT's new, experimental columnar I/O subsystem that addresses the shortcomings of the former TTree I/O.
RNTuple is similar to Apache Parquet, but offers many unique features, a user-friendly interface, and superior performance for HENP use cases, as shown in [this publication](https://iopscience.iop.org/article/10.1088/1742-6596/2438/1/012118/pdf).
Concretely, my contributions lie in the following areas:
    - Development of a backend for the Intel DAOS object store, thus allowing for transparent storage of HEP data in DAOS
    - Late model extension, i.e. allowing for incremental updates to the schema
    - Manual schema evolution, i.e. handling changes to the data schema over time while retaining backward compatibility
    - Extensions to the type system: new stdlib types, user-defined class hierarchies and collections
    - Support for big-endian architectures
    - Partial contributions to zero-copy file merge on filesystems that support reflink (e.g. [on XFS](https://blogs.oracle.com/linux/post/xfs-data-block-sharing-reflink))
    - General improvements to the file format

- [Cling](https://github.com/root-project/cling/), the interactive C++ interpreter based on clang and LLVM infrastructure, contributing with:
    - Adding support for entity redefinition (otherwise disallowed by ISO C++ one definition rule).  This extension is implemented as an AST transformer that can be enabled/disabled separately.
    See the publication in ACM Compiler Construction conference 2020 [here](https://dl.acm.org/doi/abs/10.1145/3377555.3377901)
    - Improvements to cling's unloading infrastructure.  Unloading makes it possible to "forget" about previous declarations and their emitted symbols
    - General improvements and bug fixing

- General ROOT aspects: enhancements to the terminal input library, build system, etc.

Other than purely technical tasks, I was also in charge of the supervision of 5+ interns in the group, serving as a mentor for CERN-HSF during Google Summer of Code 2022, and involved in other training / support responsibilities.

Shortly before joining the ROOT team (2017-2020), I signed a predoctoral contract to conduct my research within the Computer Architecture, Communications and Systems (ARCOS) research group at University Carlos III of Madrid.
The <a href="https://www.educacion.gob.es/teseo/mostrarRef.do?ref=1895079" target="_blank">Ph.D. thesis</a> contributes to the area of software reliability, verification and optimization.
As a requirement for a thesis' chapter, I wrote a <a href="https://github.com/arcosuc3m/clang-contracts" target="_blank">prototype implementation in clang</a> of proposal <a href="https://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0542r5.html" target="_blank">P0542R5</a> for C++ contracts.

For more information, please see a summarized version of my CV ([English](/public/cv_en-US.pdf) | [Espa&ntilde;ol](/public/cv_es-ES.pdf)).  A list of relevant publications can be accessed [here](/publications).
In my spare time, I also maintain / contribute to a number of [open-source projects](/projects).
See also my [GitHub profile](https://github.com/jalopezg-git/).
