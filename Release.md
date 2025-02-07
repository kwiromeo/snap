# Release Notes for SNAP

Stanford Network Analysis Platform (SNAP) is a general purpose, high
performance system for graph and network manipulation and analysis.

This file contains a high-level description of changes in SNAP releases.

## Release 6.0, Dec 4, 2020

This is a major release, significant new functionality includes: a large family
of egonet functions, dense and sparse floating-point vector attributes, graph
union functions.

Here is a detailed list:

- implemented a large family of egonet functions GetEgonetHop(),
  GetInEgonetHop(), GetOutEgonetHop(), GetInEgonetSub(), GetEgonetAttr(),
  GetInEgonetAttr(), GetOutEgonetAttr(), GetInEgonetSubAttr()
- implemented dense and sparse floating-point vector attributes for TNEANet
- implemented graph union functions GetGraphUnion(), GetGraphUnionAttr()
- implemented a new method TSnapQueue::Sample()
- implemented AddNodeWithAttributes() and AddEdgeWithAttributes()
- improved CommunityGirvanNewman(), so that the input graph is not modified
- improved GetClustCf(), so that all output parameters are initialized
- added dummy AddEdge(), IsEdge() methods with edge IDs to TUNGraph and
  TNGraph classes for compatibility with TNEANet
- changed the parameter names for GetClustCf(), which is needed for snap.py
- updated the definition of gettimeofday() for compilation of snap.py with
  python 3.5 and 3.6 on Windows
- completed the implementation of aaMean policy in AggregateVector()
- defined '/' operator for TStr, which is required in AggregateVector()
- fixed the problem of GetStrVal() and AddRow() not being available in snap.py
- fixed the handling of the random generator in GenDegSeq() and GenPrefAttach()
- fixed a bug in edge attribute iterator in IntAttrValueEI()
- fixed bugs in AddIntVAttrDatE(), AppendIntVAttrDatE()
- fixed a few minor issues in the documentation
- fixed compilation problems with TTable::GetStrVal()
- improved parameters for OpenMP compilation on Cygwin and macOS
- improved doxygen parameters and updated doxyblock.py for python3
- updated Makefiles with $(HOME) references
- updated Makefiles with additional instructions for building on Anaconda
- updated graphviz baseline files for graphviz version 2.38.0

---

## Release 5.0, Aug 29, 2019

This is a maintenance release and brings several upgrades.

Here is a detailed list:

- upgraded Visual Studio files to version 2019
- added support for g++ compiler versions 6.0+
- modified the code for python3 support
- added a license text
- implemented rolx:FPrintNodeMappings() to determine node IDs for features
- turned on the printing of feature matrix in rolx
- removed the Visual Studio 2008 solution file

---

## Release 4.1, Jul 25, 2018

This is a minor release and brings several bug fixes and improvements.

Here is a detailed list:

- fixed the parsing of floating point numbers in TSsParserMP
- fixed bugs in temporal motif counting, ignore self loops
- fixed a bug in GetWeightedShortestPath()
- fixed a bug in GenRndPowerLaw(), GenDegSeq() requires a sorted vector
- fixed a crash in GetESubGraph() for multigraphs
- improved LoadPajek(), so that it can read edges without weights
- improved the parsing of integers in TSsParserMP
- improved the quality of word2vec embeddings
- added a flag for random walk output in node2vec
- defined a new type TFltVFltV for TVec<TFltV>
- fixed compilation errors and a few compilation warnings on macOS
- implemented GetSubGraphRenumber(), which is required by Snap.py
- implemented GetNodeTriadsAll(), which is needed by Snap.py
- implemented GetBfsEffDiamAll(), which is needed by Snap.py
- implemented GetClustCfAll(), which is needed by Snap.py
- implemented GetTriadsAll(), which is needed by Snap.py
- added 'const' to node2vec code to make it work with Snap.py

---

## Release 4.0, Jul 27, 2017

This is a major release and brings significant new functionality: local
higher-order clustering, counting of temporal motifs, node embedding with
node2vec, locality sensitive hashing, K nearest neighbor graph construction,
fast object loading using memory mapped files, and sparse attributes.

Here is a detailed list:

- implemented local higher-order clustering, see examples/localmotifcluster
- implemented counting of temporal motifs, see examples/temporalmotifs
- implemented node embedding with node2vec, see examples/node2vec
- implemented locality sensitive hashing, see examples/lshtest
- implemented K nearest neighbor graph construction, see
  examples/knnjaccardsim
- implemented methods for computing biased random walks, required for node2vec
- implemented fast loading of objects using a memory mapped files via shared
  memory for the following classes: TVec, TStrPool, TBigStrPool, THashKeyDat,
  THash, TStrHash, TUNGraph, TNGraph, TMMNet, TNEANet, TNodeNet, TNodeEDatNet,
  TNodeEdgeNet, TUndirNet, TDirNet, TTable, TTableContext
- implemented a shared-memory class TShMIn for input stream objects
- implemented sparse attributes (vector rather than hash based) in TMMNet and
  TNEANet
- implemented a backward compatible load function TNEANet::Load_V2()
- implemented a method to convert a dense network to sparse
  TNEANet::ConvertToSparse()
- implemented node2vec for TNEANet, TNGraph, and TNodeEDatNet
- defined a number of new vector and hash classes
- implemented base TNum class for integer based classes
- implemented a class for 64-bit integers TInt64
- expanded TVVVec to work with 64-bit integers
- expanded TVVec to work with 64-bit integers
- changed API for centrality calculations so that IsDir is the last parameter
- improved the code for betweenness centrality for directed graphs
- implemented AddNodeUnchecked() for TNodeNet, TNodeEDatNet, TNodeEdgeNet,
  TNEANet, TUndirNet, TDirNet
- implemented SortNodeAdjV() for TUndirNet, TDirNet
- implemented TAttr::Load() to work with sparse attributes
- fixed a division by 0 in TTable::FillBucketsByWindow()
- fixed a bug in GenRewire() for directed graphs
- fixed a problem in GetGraphAnf(), dist=1 was redundant
- fixed a negative index error in casc.cpp
- fixed incorrect GCC_ATOMIC to better support ToNetwork() on Windows
- fixed a possible infinite loop in GetRndEdgeNonAdjNode()
- fixed node2vec crashing on directed graphs
- fixed and optimized TMMNet::ToNetworkMP
- added assertions for preventing writing to read only objects
- added a test for GenRwire()
- added tests for fast loading from shared memory
- added tests for jaccard similarity
- improved printing of 64-bit values
- renamed AddAtm() to AddMP()
- replaced GetMn() with explicit code to enable compilation in Snap.py
- removed profiling code from GetTriangleCnt()
- removed a redundant openmp flag from Makefile
- removed dependency of table.h on centr.h
- moved MapPageRank() and MapHits() from table.h to centr.h
- moved GetMapPageRank() and GetMapHitsIterator() from table.h to centr.cpp
- made edits for the code to compile with gcc on Mac OS X 10.9 and clang on
  macOS 10.12
- updated code for compilation of Snap.py on Windows
- commented out obsolete GetMergeSortedV()
- commented out CountTriangles(), a previous implementation of
  GetTriangleCnt()
- commented out dummy definitions of TNGraphMP, TNEANetMP
- fixed a few documentation typos in alg.h
- fixed a minor typo in agm comments
- edited ReadMe.txt to use only ASCII characters

---

## Release 3.0, Jul 18, 2016

This is a mega large release. It brings major new functionality: relational
tables, multimodal graphs, multi-threaded operations, personalized pagerank,
motif-based network clustering, and hundreds of other additional features and
capabilities.

- implemented a new class TTable for relational tables
  - implemented new supporting classes for TTable: TPredicate, TAtomicPredicate,
    TPredicateNode, TTableContext, TPrimitive, TTableRow, GroupStmt,
    TRowIterator, TRowIteratorWithRemove, TTableIterator
  - implemented a wide range of standard relational operations on TTable
  - implemented fast parallel select and join operations on TTable
  - implemented IsNextK, SimJoin and SimJoinPerGroup methods
  - implemented MapPageRank function to compute pagerank of a graph sequence
- implemented a new class TMMNet for multimodal networks
  - implemented new subclasses of TMMNet: TModeNet for modes and TCrossNet
    for cross nets
- added new methods and examples: randwalk, motifcluster, cascadegen
  - randwalk computes random walk scores and personalized pagerank
    between pairs of nodes
  - motifcluster implements a spectral method for motif-based network clustering
  - cascadegen computes cascades from a list of events
- created a new contrib directory for contributions to SNAP
- added a new contribution from University of Catania: RI algorithm for
  one-to-one exact subgraph isomorphism problem maintaining topological
  constraints
- implemented new methods for motif-based network clustering (motifcluster)
- implemented new methods for personalized pagerank (randwalk)
- implemented fast pagerank and hits, sequential and parallel
- implemented new methods for weighted pagerank, sequential and parallel
- implemented a new method for shortest paths
- implemented new methods for weighted farness centrality,
  closeness centrality, and betweennesscentrality
- extended routines for calculating betweenness and closeness centrality
  to both directed and undirected graphs, and TNEANet
- implemented fast methods for triangle counting, sequential and parallel, and
  supporting methods
- implemented new methods that build cascades from a list of events (cascadegen)
- implemented a fast top-down BFS algorithm, TBreathFS::DoBfsHybrid()
- turned on OpenMP functionality on supported platforms: Linux and Mac with GCC
  - introduced GCC_ATOMIC flag for __sync_... GCC functions
  - unified all OpenMP flags to USE_OPENMP
  - implemented many parallel operations
- implemented a new class TUndirNet for undirected networks
- implemented a new class TDirNet for directed networks
- implemented a new class TNGraphMP for directed graphs, supporting
  multi-threaded operations
- implemented a new class TNEANetMP for directed multigraphs with
  attributes, supporting multi-threaded operations
- implemented new class THashMP, hash table with multiprocessing support
- implemented a new experimental class in glib-adv, THashGenericMP,
  a hash table which supports multithreading and non-integer value types
- implemented a new class TSsParserMP, a multithreaded parser for parallel
  text load
- implemented a new class TAttr, a hash-based implementation of sparse
  attributes
- implemented a new class TMaxPriorityQueue, max priority queue
- implemented a new class TStopwatch to benchmark operations
- implemented new methods for converting tables to graphs and networks,
  sequential and parallel
- implemented new methods for loading tables into multimodal networks
- implemented new attribute type for TNEANet: integer vectors
- implemented sparse attributes for TNEANet nodes and edges
- implemented new methods in TNEANet to return integer attribute names, values
- implemented a new method in TNEANet for summing the weights of all the
  outgoing edges of a node
- implemented new functions for converting numpy arrays to SNAP and vice versa
- added a method to sort the adjacency list of a node in a graph
- added methods to add nodes and edges without performing consistency checks
- implemented gettimeofday() on Windows
- implemented new methods to access individual components in TTriple
- implemented new methods to access individual components in TQuad
- implemented new TVec methods Reduce(), CopyUniqueFrom(), GetRndVal(),
  AddMP(), MoveLastMP(), SearchBinLeft()
- implemented new THash method GetDatWithDefault()
- implemented new TStrPool method GetMemUsed()
- implemented new TCh method IsHashCh()
- implemented new TBigStrPool method GetMemUsed()
- implemented new TStrHash methods GetMemUsed(), GetStr()
- implemented new TStrHashF_DJB methods GetPrimHashCd(), GetSecHashCd()
- implemented new TGnuPlot methods PlotValRank(), PlotValOverTm(),
  PlotCntOverTm()
- implemented new TSsParser methods GetUInt64(), IsUInt64() to support int64
- implemented a new TSecTm method GetYmdTmStr2()
- defined new TTriple type TIntStrStrTr
- defined new TVec type TIntStrStrTrV
- defined new THash types TIntStrPrVH, TIntIntStrPrH, TIntPrH,
  TIntIntPrPrIntH, TIntIntPrPrFltH, TIntIntPrPr
- added new tests TTable, TUndirNet, TDirNet, TMMNet, TModeNet, TCrossNet,
  TAttr, multimodal, priority-queue, randwalk
- added new tutorials for TAttr, TDirNet, TUndirNet, multimodal, TSsParser
- implemented Visual Studio 2010 project files for all the examples
- expanded the test for TTNEANet
- expanded the tutorials for TNGraph, TUNGraph, demo-gio
- improved the code for recognition of input file type in bigclam, cesna, coda
- implemented non-consecutive node numbering for bigclam input graphs
- changed the flows sample input from binary to text
- updated documentation for cesna
- extended testSnap.cpp with a betweenness calculation
- renamed min and max macros in glib-core/bd.h to MIN and MAX to avoid conflicts
- changed class TMIn to use uint64 size rather than int
- expanded TMin with methods for reading of memory mapped files on Linux
- added time support to gnuplot
- updated TVec::Resize() code to support 2B elements for TInt
- changed TVecPool::AddV() to use TSize rather than TSizeTy and uint 
  for length type
- changed the local path for gnuplot on Mac
- added range checking to TSsParser GetInt(), GetFloat(), GetUInt64()
- made minor updates for gnuplot output format
- made minor updates in json.h
- improved handling of TZipIn::SevenZipPath
- updated TZipIn TZipOut to properly handle paths
- commented out TDir::Exists() on Windows
- fixed the return type of IsDirected
- fixed a bug in TNodeEdgeNet::TNodeI::GetInNDat
- fixed TNEANet::DelEdge(), which crashed if any attributes were detected
- fixed a bug in GetEgonet, so in and out-edges to center node are included
- fixed the initialization of TBreathFS
- fixed a minor warning in Crash()
- fixed reading of empty lines in TSsParser::Next()
- fixed redundant space at the end of TSsParser::GetLnStr()
- fixed syntax errors in circles.h
- added a new experimental directory snap-exp/bfs-dev for BFS code
- added a new experimental directory snap-exp/cascades-dev for code that
  creates cascades
- added a new experimental directory snap-exp/cascades-benchmark for code
  that benchmarks cascade operations
- added a new experimental directory snap-exp/multimodal-dev for code
  for multimodal networks
- implemented an experimental TUNGraphMP for undirected graphs, supporting
  multi-threaded operations
- implemented an experimental class TMNet for multimodal networks with
  three different subvariants TSVNode, TMVNode, TCVNode
- added a new experimental directory snap-exp/test-dev for various test programs

---

## Release 2.4, May 11, 2015

- implemented TLSHash() class for locality sensitive hashing
- implemented SaveEdgeListNet(), LoadEdgeListNet()
- expanded Load/SaveEdgeListNet() with support for node attributes
- implemented IsAttrDeletedN(), IsIntAttrDeletedN(), IsFltAttrDeletedN()
- implemented IsStrAttrDeletedN(), IsAttrDeletedE(), IsIntAttrDeletedE()
- implemented IsFltAttrDeletedE(), IsStrAttrDeletedE()
- implemented GetIntAttrIndDatE(), GetFtlAttrIndDatE(), GetStrAttrIndDatE()
- implemented GetIntAttrIndDatN(), GetStrAttrIndDatN(), GetFltAttrIndDatN()
- implemented GetAttrIndN(), GetAttrIndE()
- implemented IsEmpty() and IsEnd methods() for THashSetKeyI
- implemented Next() method to THashSetKeyI
- added Load() method to TCh
- added functions to compare triples by 2nd and 3rd value
- added functions for checking whether a directory exists
- added *= operator to TUInt64 to support the type in vector indexes
- added contrib directory and its readme
- made sentinel line optional for LoadEdgeListNet()
- fixed NodeId to NodeI for iterators
- fixed an incorrect method reference in AttrValueEI()
- fixed a problem in subgraph.cpp:GetEgonet() with bidirectional connections
- updated GLib code with upstream code
- added a comment on PNG support for GNUPlot on Mac
- added comments for methods in gio.cpp
- added an example on how to update values in a hash table
- put back tutorials Xcode project files

---

## Release 2.3, Jun 16, 2014

- implemented RolX algorithm for detecting node roles
- implemented flow agorithms
- added an example for the RolX algorithm
- added an example for the flow algorithms
- implemented a new function GetEgonet()
- added tests and demo code for functions in alg.h
- changed gnuplot version test, so that it runs only on demand, not at start
- expanded cncom tests and the demo
- expanded the code to work on non-OpenMP Mac OS X
- renamed GetIntAttrDatN to GetIntAttrIndDatN so that it works in Snap.py
- renamed GetIntAttrDatE to GetIntAttrIndDatE so that it works in Snap.py
- updated the AGM related code to work with SWIG
- added an error description when file open fails
- fix a bug in loading attributes when the node ids are non-integers
- fixed kronfit to use the right output file name given by arg "-o:"
- fixed TUNGraph::AddNode() to add reciprocal edges when given vector
- fixed a bug with GetMxSccSz
- fixed GenCircle and GenGrid to add reciprocal edges properly
- improved the fix for sorting the SCC sizes
- improved the handling of getrusage()

---

## Release 2.2, Mar 12, 2014

- added CoDA, 2-mode community detection method, in examples/coda
- added CESNA, community detection method for networks with node attributes,
  in examples/cesna
- added Infomap community detection algorithm in examples/community
- added a second demo of connected components in tutorials/demo-cncom1.cpp
- added a demo of text file parsing in tutorials/demo-TSsParser.cpp
- added a function to plot multiple TMom hash tables on a single plot
- extended TMom to compute the mode value of the data
- added a PlotValV() function that plots error bars/variances
- added SetVal() to TVec
- added support for generating PNG on Mac OS X
- improved Resize() to allocate maximum number of elements possible 
- improved error handling of TZipIn for non-zip files
- appended 'X' to the names of copy out scalar parameters in snap-core
- added GetVal(), GetPrimHashCd() and GetSecHashCd() to TCnCom
- replaced aborts with exceptions for Snap.py
- updated Makefiles and code to compile on OS X Maverics
- added g++ flags in Makefile
- added compilation switches Snap.py, Snapworld, and backtraces in Makefile
- added checks in accessing attributes in TNEANet
- changed FailR to EFailR in TZipIn
- fixed bug in TMom standard error computation
- fixed an incorrect assertion in TBreathFS<PGraph>::GetRndPath()
- fixed infinite loop in TNEANet::DelEdge()
- fixed a problem in TNEANet::DelEdge()
- fixed a problem in TNEANet::DelNode()
- fixed TNEANet::Add{Int,Str,Flt}AttrDat[NE]() to use KeyId instead of NId
- fixed a problem with a missing variable initialization in mag.cpp
- fixed #26, change in endianness detection due to gcc compiler bug
- fixed a bug in CntUniqBiDirEdges()
- fixed small bugs in Cnt... functions in alg.h
- fixed TMom plots
- fixed incorrect index in glib-core/tm.h:GetMonthNm()
- fixed incorrect index in TTm::GetCurLocTm().GetMonth()
- made minor code changes to reduce compiler warnings

---

## Release 2.1, Sep 12, 2013

- implemented a new network class TNEANet and PNEANet for graphs with
  attributes
- added new GetVal1() and GetVal2() methods to access components of TPair
- renamed Get*Values() to Get*Val()
- added a new function to create a rewired version (using configuation model)
  of a given graph
- added sorting to TGStatVec::GetValV
- extended function TSnap::PrintInfo() in gbase.h
- added statistics for undirected graphs.
- added Strong and Bi-connected component statistics
- added functions to plot k-Core decomposition plots
- updated graph statistics
- implemented TTable::Defrag
- changed some casts in unicode.h to fix compilation errors on gcc 4.8.1
- defined NDEBUG compilation flag to disable assertions in production
- improved saving of PNG and EPS files to take into account the full path
- added static variables in TGnuPlot: GnuPlotPath and GnuPlotFNm for
  gnuplot executable
- added a final renormalization step to GetHits() needed for disconnected
  graphs
- added GraphVizLayout sfdp
- added benchmark for THash and TVec
- improved PlotHops
- fixed a bug in TSsParser::GetLineStr()
- fixed a small bug in GetKCoreEdges()
- updated cncom.h:IsWeaklyConn() so that it does not crash for empty graphs
- fixed #38 community example does not work on email-Enron.txt
- fixed zygote example on Mac OS X
- made changes needed for snap.py on Windows
- changed gbase.h so that it compiles with swig
- moved WriteN() to util.cpp to prevent compile warnings on Mac OS X
- made Snapworld functions defined only on Unix-like systems
- make bigclam.cpp faster
- added fixed vector size to the hash, vec benchmarks
- made minor code changes to reduce compiler warnings
- fixed demo-topology-benchmark.cpp compilation on Cygwin
- commented out class IsDerivedFrom

---

## Release 2.0, May 13, 2013

- significantly changed several classes and methods, not backward compatible.
  This version is not able to read binary files or class serializations,
  produced by previous SNAP versions.
- added support for 64-bit vector length in TVec
- added support for 64-bit vector length in TVecPool
- implemented a new hash function for TVec with 10x improvement over the
  previous one. This change is not backward compatible for hash tables. Old
  hash functions are available in TVecHashF_OldGLib.
- implemented new 10x faster hash functions for TPair, TTriple, TQuad and TTuple
- added 64-bit random number generators GetUniDevInt64() and GetUniDevUInt64()
- implemented new TVec method UnionLen() and GetMemSize()
- moved vector access functions in TLocClust from private to public
- added new examples agmfit, bigclam, circles, zygote, XcodeTest
- added new tutorials for bfsdfs, cncom, gviz, triad
- added new unit tests for alg, bfsdfs, cncom, gvi, THashSet, triad
- added Mac OS X Xcode support for examples
- added Mac OS X support for doxygen
- fixed #36 normalized eigenvector centrality values to use L2 rather than L1
- fixed #17 integer overflow bug in TSnap::GenRndGnm()
- fixed a bug in THashSet::Defrag()
- fixed a bug in IsTree()
- fixed a bug in TVec::NextPerm()
- fixed GetNodeTriads(), it was not checking for an empty group
- changed GetTriads and GetClustCf to return triads as int64 rather than int
  to prevent integer overflow for large graphs
- implemented much faster TSsParser
- added OpenMP compilation flags
- implemented stackdump for g++
- merged updates from the most recent version of GLib
- undefined __STDC_LIMIT_MACROS in base.h to prevent double definition warnings
- removed include <stdio.h> in examples/*/stdefx.h to correctly define SIZE_MAX
- removed a redundant GetNodeTriads() variant
- changed type of PGraph::TNodeI to PGraph::TObj::TNodeI in triad.h
- fixed warnings about implicit conversions from int64 to int in dt.h, tm.h,
  os.h.

---

## Release 1.11, Dec 21, 2012

- added new examples netinf, infopath
- added new advanced modules cascnetinf, cascdynetinf
- added new distribution functions to glib-core/dt.h::TRnd: GetRayleigh(),
  GetWeibull()
- added demo programs for graph input/output (gio.h), graph generators
  (ggen.h), THash
- added tests for graph input/output (gio.h), graph generators (ggen.h), THash
- unified the names of intermediate files for demos and tests to demo*.dat
  and test*.dat
- added cases to test edge iterator with very few nodes
- expanded TUNGraph test to include graphs with loops and the number of
  edges in such graphs
- added ManipulateEdges test for TUNGraph
- added test in TUNGraph for checking edge iterator following deletion
- added OSX Xcode project
- updated snap-test Xcode project with gtest code completion/syntax.
- improved tutorial and test Makefiles to work on Mac OS X
- improved Snap.o make rule, added dependencies for *.h, *.cpp in glib-core
  and snap-core
- improved demo Makefile so that individual targets do not need to be
  specified
- added path to snap-exp to examples makefiles
- changed function parameters in TStrPool to const reference
- added assertion for DegSeq vector to be sorted
- added an assertion for edges in random graphs to prevent infinite loops
- fixed #27 - No node checking when load Epinions in signnet.cpp
- fixed #28 - no TGraphViz class in signnet.cpp
- fixed #29 - no check for inserting node in bfsdfs.h
- fixed #17 "example/cliques" does not compile with gcc 4.7
- fixed #21, undetected 32-bit overflow in TGraphAnf<PGraph>::InitAnfBits(),
  the calculation is now done in 64-bits and an exception is thrown if the
  final result is more than 32-bit
- fixed bug in LoadPajek for graph files with colors
- changed EFailR() to FailR() when out of memory
- included bd.h in all files that use Class... macros, so that doxygen
  correctly documents those classes
- added #7, add Snap version number to reference manuals
- implemented #8, improve the front page for reference manuals
- added .gitignore file for Xcode project

---

## Release 1.10, Oct 15, 2012

- fixed TUNGraph to return correct number of edges, not backward compatible.
  This version is not able to read binary TUNGraphs, saved by previous SNAP
  versions.
- added a new example graphhash
- fixed #13, GHash incorrectly handles non-existent keys
- fixed #12, Graphviz keeps outputting a PostScript file on non-Windows
- fixed #15, bug in netevol.cpp
- fixed #14, TSnap::GenCircle creates self-loops
- fixed a bug in TSnap::GetBfsTree which failed for revised AddNode()
- included "<new>" in unicode.h to support Xcode with the Apple compiler
- fixed bug in TUNGraph:BegEI(), some edges could be missed by the iterator

---

## Release 1.9.2, Oct 2, 2012

- removed a default parameter in triad.h so that the code compiles in
  Visual Studio 2010
- in source code converted all 8bit characters to 7bit characters \xnn

---

## Release 1.9.1, Sep 28, 2012

- fixed name mismatch between GetUniq... and CntUniq... to CntUniq...
- reversed the changes in centr.h:GetNodeEcc() name and definition to pre-1.9

---

## Release 1.9, Sep 26, 2012

- names of functions in gviz.h have been changed, not backward compatible
- neighbor abbreviations have been changed thoughout the code,
    nbh -> nbr, Nbh -> Nbr, not backward compatible
- a new class TBPGraph has been added to support bipartite graphs
- new examples have been added agmgen, circles, kronem, magfit, maggen
- code automatically detects gnuplot version to address "set ticks"
- makefiles automatically detect OS version
- snap directory has been split to snap-core, snap-adv, snap-exp
- glib directory has been split to glib-core and glib-adv
- reference manuals have been created for users and developers
- tutorials have been created for many classes
- tests have been created for many classes
- programming guide has been created for developers
- code has been changed to remove compilation warnings
- merged with the latest glib version
- numerous code improvements and bug fixes
