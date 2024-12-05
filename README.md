# SISC

## About SISC (Second Interpreter of Scheme Code)

SISC is an extensible Java based interpreter of the algorithmic
language Scheme.  SISC uses modern interpretation techniques, and
handily outperforms all existing JVM interpreters (often by more than
an order of magnitude).

In addition, SISC is a complete implementation of the language. The
entire R5RS Scheme standard is supported, no exceptions.  This includes
a full number tower including complex number support, arbitrary
precision integers and floating point numbers, as well as hygenic R5RS
macros, proper tail recursion, and first-class continuations (not just
the escaping continuations as in many limited Scheme systems). SISC
also attempts to implement the standard as correctly as possible,
while still providing exceptional performance.

SISC also provides useful real-world extensions, such as networking,
elegant exception handling, a scope-friendly module system, support
for SLIB, numerous SRFIs, and an extensible type system 
with a Java foreign-function interface.

Finally, native functionality can be added through the use of native
libraries that may add new types, values, and functions to the
language. These extensions can be packaged into scopable modules at
the Scheme level as well.


## Building

This version of SISC needs to bootstrap itself.  You have two options:

1. Use an existing installation of SISC.  If you use this method, Ant expects
   to find an executable called 'sisc' in your PATH.  This method is preferred.
2. You can download a distribution of pre-expanded files.  You need to extract
   it under the 'src/sisc/boot' directory.  On Unix, the procedure looks like this:

    wget https://github.com/downloads/amoe/sisc/sisc-psyntax-expanded.zip
    unzip -d src/sisc/boot sisc-psyntax-expanded.zip
    ant -Dbuild.disableExpand=true

(Defining `build.disableExpand` is not necessary, but avoids a spurious warning.)

JDK 6 is required both to build and run this branch of SISC.

You need Apache Ant installed.  When you have it, simply run "ant".

Tests will be built by default.  You will need to have JUnit installed in order
to build the tests.  Drop the JUnit JAR file into the 'lib' subdirectory.  This
version should be compatible with JUnit version 3 and 4.

The Java FFI, s2j, needs the ASM bytecode manipulation library to build.  This
should also be dropped in the 'lib' subdirectory.  You need both the main ASM3
jar and the 'commons' jar.  This is distributed by upstream in a single
'asm-VERSION-bin.zip' file.  This version should be compatible with ASM versions
3 and 4, and possibly older versions.

To build the manual, you need the DocBook XSL stylesheets installed.  On a
Debian system you can find them in the package 'docbook-xsl'.  You also need the
command line XSLT processor 'xsltproc'.

On Debian, you can install and symlink in the relevant jars like this:

  sudo aptitude install junit libasm3-java
  ln -st lib /usr/share/java/{junit,asm3,asm3-commons}.jar

Download links:
* JUnit: https://github.com/KentBeck/junit/downloads
* ASM: http://forge.ow2.org/projects/asm/


## Installation

Define SISC_HOME in your environment variables to point to the
directory in which you installed the SISC distribution. Then, install
"sisc" (Unix) or "sisc.bat" (Windows) in your path. 
If you are running on a Unix or Unix-like system, you may also wish to 
run the "install-srfi22.sh" script, which will set up SRFI-22 support 
for running Scheme programs directly from the shell.

To run SISC, just type "sisc" or "sisc.bat", followed by any scheme source
files you wish to load.  Refer to the SISC Manual (which accompanies
the full distribution and can be found on the SISC website) for the
full command-line usage instructions.


## Bugs

If you encounter an unexpected error, please send an email to
sisc-devel@lists.sourceforge.net, with the following information:

1. Build version
2. Steps to reproduce the error
3. A stack trace, 
  (print-exception (get-last-exception))

If you're running the Lite build, you will not be able to perform step 3. 
Please obtain the full build and see if your error occurs there as well,
then submit a report with the stack trace from the full build.  


## Website

More information about SISC, including a paper on the implementation
and the full SISC manual, can be found at the SISC website,

http://sisc.sourceforge.net


(C) 2000-2007 Scott G. Miller <scgmille@freenetproject.org>
This software is distributed under a dual licensing scheme, with the
GNU General Public License, v2, and the Mozilla Public License.  The
source code should be available from the same place you found this
binary distribution.
