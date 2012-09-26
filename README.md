Simulation of simplicity analysis and code generation
=====================================================

`simplicity` is an automatic code generator for Simulation of Simplicity (SoS), a technique for avoiding
degeneracies in exact geometric computation.  Given a geometric predicate such as the determinant of
a small matrix, SoS adds different infinitesimal shifts to each input variable.  Even if the original predicate
evaluates to zero, the infinitesimal shifts guarantee a (possibly infinitesimal) nonzero value.  Thus, algorithms
which make use of SoS predicates can pretend that degeneracies never occur.  For more details on the underlying technique, see

* Edelsbrunner, H., Mucke, E., "Simulation of simplicity: a technique to cope with degenerate cases in geometric algorithms",
  http://arxiv.org/abs/math/9410209.

There are two dependencies:

* [other/core](https://github.com/otherlab/core): Otherlab core library (BSD license)
* [sage](http://www.sagemath.org): Open source symbolic mathematics (GPLv2)

The Python code generation scripts themselves depend only on sage, and are therefore GPL.  The generated C++
code is *not* GPL for the same reason that code compiled with gcc is not GPL: the generated code does link or
include sage either directly or indirectly.  Therefore, the generated code is safe for inclusion in BSD licensed
libraries such as other/core (see `other/core/exact/predicates.*`).

### Usage

To generate `predicates.h` and `predicates.cpp` in directory `<dir>`, run

    ./simplicity.py <dir>

For example, to regenerate the predicate code in other/core/exact, do

    ./simplicity.py $OTHER/core/exact
