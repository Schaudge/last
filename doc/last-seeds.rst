LAST seeding schemes
====================

LAST's critical first step is to find *seeds*, i.e. initial matches
between query and reference sequences.  It can use various seeding
schemes, which allow different kinds of mismatches at different seed
positions.

   A seeding scheme consists of a seed alphabet, such as::

     1  A C G T
     0  ACGT
     T  AG CT

   and one or more patterns, such as this one::

     1T1T10T1101101

   Each symbol in a pattern represents a grouping of sequence letters:
   in this example, ``T`` represents the grouping ``AG CT``.  At each
   position in an initial match, mismatches are allowed between
   letters that are grouped at that position in the pattern.

   Although the patterns have fixed lengths, LAST's initial matches do
   not.  LAST finds shorter matches by using a prefix of the pattern,
   and longer matches by cyclically repeating the pattern.

   A *restricted* symbol omits letters of the main sequence alphabet,
   which are then forbidden at those positions::

     r  AG

   An *exact* symbol groups no letters::

     Y  C T

   In 2nd and subsequent cycles, restricted symbols are made
   unrestricted: if it is exact then the omitted letters are added as
   separate groups, else they are added as one group.

BISF
----

This seeding scheme is for aligning bisulfite-converted DNA
*forward* strands to a closely-related genome (MC Frith, R Mori, K
Asai, NAR 2012 40:e100).
It uses this seed alphabet::

  1  CT A G
  0  ACGT

And this pattern::

  1111110101100

It sets this lastdb default:
-w2

It sets this lastal default:
-pBISF

BISR
----

This seeding scheme is for aligning bisulfite-converted DNA
*reverse* strands to a closely-related genome (MC Frith, R Mori, K
Asai, NAR 2012 40:e100).
It uses this seed alphabet::

  1  AG C T
  0  ACGT

And this pattern::

  1111110101100

It sets this lastdb default:
-w2

It sets this lastal default:
-pBISR

MAM4
----

This DNA seeding scheme is like MAM8, but a bit less sensitive, and
uses about half as much memory.  [From Frith & No?? 2014 NAR 42:e59
Table S11, row 12.]
It uses this seed alphabet::

  1  A C G T
  0  ACGT
  T  AG CT

And these patterns::

  11100TT01T00T10TTTT
  TTTT110TT0T001T0T1T1
  11TT010T01TT0001T
  11TT10T1T101TT

MAM8
----

This DNA seeding scheme finds weak similarities with high
sensitivity, but low speed and high memory usage (e.g. ~50 GB for
mammal genomes).  [From Frith & No?? 2014 NAR 42:e59 Table S12, row
15.]
It uses this seed alphabet::

  1  A C G T
  0  ACGT
  T  AG CT

And these patterns::

  1101T1T0T1T00TT1TT
  1TTTTT010TT0TT01011TTT
  1TTTT10010T011T0TTTT1
  111T011T0T01T100
  1T10T100TT01000TT01TT11
  111T101TT000T0T10T00T1T
  111100T011TTT00T0TT01T
  1T1T10T1101101

MURPHY10
--------

This protein seeding scheme is popular for finding long-and-weak
similarities (LR Murphy et al. Protein Eng. 2000 13:149).
It uses this seed alphabet::

  1  ILMV FWY A C G H P KR ST DENQ

And this pattern::

  1

It sets this lastdb default:
-p

NEAR
----

This DNA seeding scheme is good for finding short-and-strong
(near-identical) similarities.  It is also good for similarities
with many gaps (insertions and deletions), because it can find the
short matches between the gaps.  (Long-and-weak seeding schemes
allow for mismatches but not gaps.)
It uses this seed alphabet::

  1  A C G T
  0  ACGT

And this pattern::

  1111110

It sets this lastal default:
-r6 -q18 -a21 -b9

YASS
----

This DNA seeding scheme is good for finding long-and-weak
similarities.  It is a good compromise for both protein-coding and
non protein-coding DNA (L No?? & G Kucherov, NAR 2005 33:W540-W543).
It uses this seed alphabet::

  1  A C G T
  0  ACGT
  T  AG CT

And this pattern::

  1T1001100101

RY4-6 (abbreviation: RY4)
-------------------------

This DNA seeding scheme reduces run time and memory use, by only
seeking seeds at ~1/4 of positions in each sequence [from Table 3 of
MC Frith, L No??, G Kucherov].
It uses this seed alphabet::

  R  A G
  Y  C T

And these patterns::

  RRRRRY
  RRYRRY
  RRYRYY
  RYRRRR
  RYRRRY
  RYRYRY
  RYYRRR
  RYYRRY
  RYYRYR
  RYYRYY
  RYYYRY
  RYYYYY
  YRYRRY
  YYYRRR
  YYYRRY
  YYYYRY

It sets this lastal default:
-m2 -r6 -q18 -a21 -b9

RY8-8 (abbreviation: RY8)
-------------------------

This DNA seeding scheme reduces run time and memory use, by only
seeking seeds at ~1/8 of positions in each sequence.
It uses this seed alphabet::

  R  A G
  Y  C T

And these patterns::

  RRRRRRRY
  RRYRRRYY
  RYRRRRYR
  RYRRRRYY
  RYRRRYRY
  YRRRRRRY
  YRRRRRYR
  YRRRRRYY
  YRRRYRRY
  YRRYRRYR
  YRRYRRYY
  YRYRRRYY
  YRYRRYRY
  YRYRRYYR
  YRYRRYYY
  YRYRYRYY
  YYRRRRYR
  YYRRRRYY
  YYRRRYRY
  YYRRRYYR
  YYRRRYYY
  YYRRYRYR
  YYRRYRYY
  YYRRYYRY
  YYRRYYYR
  YYRRYYYY
  YYRYRYYR
  YYRYRYYY
  YYRYYRYY
  YYYRYYYR
  YYYRYYYY
  YYYYYYYR

It sets this lastal default:
-m2 -r6 -q18 -a21 -b9

RY16-8 (abbreviation: RY16)
---------------------------

This DNA seeding scheme reduces run time and memory use, by only
seeking seeds at ~1/16 of positions in each sequence.
It uses this seed alphabet::

  R  A G
  Y  C T

And these patterns::

  RRRRRYRY
  RRRRYYRY
  RRRYYYRY
  RRRYYYYY
  RRYRRYRY
  RRYYYYRY
  YRRRRYRY
  YRRRYRYR
  YRRRYRYY
  YRRRYYRY
  YRRYYRYR
  YRRYYRYY
  YRRYYYRY
  YRRYYYYY
  YYRRYRYR
  YYRRYRYY

It sets this lastal default:
-m2 -r6 -q18 -a21 -b9

RY32-10 (abbreviation: RY32)
----------------------------

This DNA seeding scheme reduces run time and memory use, by only
seeking seeds at ~1/32 of positions in each sequence.
It uses this seed alphabet::

  R  A G
  Y  C T

And these patterns::

  YRRYRRYRRR
  YRRYRYYRRR
  YRRYYRYRRR
  YRRYYYRRRR
  YRRYYYRRRY
  YRRYYYYRRR
  YRYRRYRRRR
  YRYRRYRRRY
  YRYRRYYRRR
  YRYRYRYRRR
  YRYRYYRRRR
  YRYRYYRRRY
  YRYRYYYRRR
  YRYYRRYRRR
  YRYYRYYRRR
  YRYYYRYRRR
  YRYYYYRRRR
  YRYYYYRRRY
  YRYYYYYRRR
  YYRRYRYRRR
  YYRRYYRRRR
  YYRRYYRRRY
  YYRYRYRRRR
  YYRYYRYRRR
  YYRYYYRRRR
  YYRYYYRRRY
  YYYRYYRRRR
  YYYRYYRRRY
  YYYYRRYRRR
  YYYYYRYRRR
  YYYYYYRRRR
  YYYYYYRRRY

It sets this lastal default:
-m2 -r6 -q18 -a21 -b9

