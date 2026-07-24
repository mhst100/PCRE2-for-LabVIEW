PCRE2 Toolkit for LabVIEW

PCRE2 Toolkit for LabVIEW is a library of functions and VIs to support PCRE2 regular expressions. 

The source code for the DLLs can be found on the PCRE2 projects site on github
https://github.com/PCRE2Project/pcre2


MatchRegex.vi is a polymorphic VI

MatchRegExStd.vi
This VI works similarly to the Match Pattern function. Wire the String and the match pattern
and returns before substring, match substring, after substring and the offsets

string: specifies the input string you want the function to search
match pattern: the regular expression
offset: the starting point in string for the match
Options: the compile and match options  (see Pcre2CompileOption.ctl, Pcre2MatchOption.ctl)
capture index: the index of the substring (the default is the complete match)

before substring: the part of the string before the substring
match substring: the matched substring
after substring: the rest of the string after the match
match offset: is the match position in string
offset past match: is the position in string just after the match

all other VIs in MatchRegex.vi work similar. They may have differnt´outputs, work 
with named substrings.

The two VIs MatchRegExJit.vi and MatchRegExJitToSubstringOffsets.vi use the JIT compiler.
The extra step for the just in time compiler slows down the execution time. It usually 
doesn't make sense to use these VIs. Except for testing a regular expression or as a 
template for a more complex VI. The JIT compiler can speed up the matches in case of
repeated searches of the same pattern.


SearchAndReplace.vi MatchRegex.vi is a polymorphic VI

SearchAndReplaceStd.vi 
implements a classic (or very simple) search and replace operation.

SearchAndReplaceEx.vi 
tries to implement the same functionality like the Search and Replace String
function of LabVIEW (with Regular Expression option enabled). It should work very 
similar. But note, that it uses PCRE2 which is different in some cases.

RegExSubstitude.vi
uses the substition function of PCRE2.
See https://pcre.org/current/doc/html/pcre2api.html#SEC38 how it works.
One simple example: If "heLLo" is captured and the replacement string is \u\L$1, then the
resulting string is "Hello".

SearchAndReplaceJitEx.vi
works similar like SearchAndReplaceEx.vi but it uses the JIT compiler.
Like all other JIT VIs, this is mainly an example how the JIT compiler can be used to
speed up subsequent identical matches.

SearchAndReplaceJitEx.vi
works similar like SearchAndReplaceEx.vi but it uses the JIT compiler.
Like all other JIT VIs, this is mainly an example how the JIT compiler can be used to
speed up subsequent identical matches.

RegExJitSubstitude.vi
works similar like RegExSubstitude.vi but uses the JIT compiler.
Like all other JIT VIs, this is mainly an example how the JIT compiler can be used to
speed up subsequent identical matches.


SplitSubjectToSubstrings.vi
Uses the offsets (from MatchRegExToSubstringOffsets.vi or MatchRegExJitToSubstringOffsets.vi)
and extracts all substrings into an array of strings.


SubstringFromSubject.vi is a polymorphic VI

Pcre2SubstringFromSubjectByOffsets (s).vi
Pcre2SubstringFromSubjectByOffsets (ba).vi
Pcre2SubstringFromSubjectByOffsets (bsa).vi
using the match offset and offset past match to extract the substring from the subject string.
the (s) VI returns only the subject, (ba) returns only the strings before and after the subject
and (bsa) returns all three strings.

The other functions are something special, because they need the match data pointer of PCRE2.
They can be used when using lower level VIs. The VI Pcre2SubstringFromSubjectByNumber8 (s).vi
and the (ba) and (bsa) variants using the substring number (index) to return the substring
while Pcre2SubstringFromSubjectByName8 (s).vi and the (ba) and (bsa) variants are using the
name of the substring.


In the advanced folder, there are also some LabVIEW Rings for the different options. Like 
the compile options, match options, compile context options, jit compile options, and much more. 
Not all of the rings are on the Advanced Palette.

The Advamced folder also includes several VIs which are actually not in use by any of the
higher level VIs. These are related to the compile context, jit stack, pattern info, make tables.

