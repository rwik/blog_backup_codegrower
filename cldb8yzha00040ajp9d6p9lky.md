---
title: "Clang vs GCC"
datePublished: Wed Jan 25 2023 05:50:13 GMT+0000 (Coordinated Universal Time)
cuid: cldb8yzha00040ajp9d6p9lky
slug: clang-vs-gcc
canonical: https://dev.to/rwik/clang-vs-gcc-3d4h
cover: https://cdn.hashnode.com/res/hashnode/image/stock/unsplash/Sc1GJCninik/upload/1997d60b176b107b135a7b8d767f343e.jpeg
tags: compiler, gcc

---

Clang is relatively new in cpp world. Clang came out of apple’s stable and became open sourced in 2007. Apple uses LLVM extensively. For some unknown reason they choose to drop gcc’s front end , and create a new compiler front end from scratch. Thus Clang is born .  
GCC’s main popularity lies in the fact that it is the only option to compile Linux kernel. So if you are working in \*nix world GCC is surely your daily driver. Also GCC supports more legacy languages ( like Fortran, ADA). But on the other hand Clang+LLVM reduces compilation time for single threaded applications by 5-10% . For a more comprehensive benchmark comparison check [here](https://www.alibabacloud.com/blog/gcc-vs--clangllvm-an-in-depth-comparison-of-cc%2B%2B-compilers_595309) .