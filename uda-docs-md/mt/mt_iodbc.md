<div id="mt_iodbc" class="chapter">

<div class="titlepage">

<div>

<div>

# Chapter 14. OpenLink ODBC Driver Manager (iODBC SDK)

</div>

<div>

<div class="abstract">

**Abstract**

This document provides information on linking your ODBC Applications
with iODBC. iODBC is an alternative ODBC Driver Manager solution for
developing ODBC components and applications for non-Windows systems
(e.g. Mac OS Classic, Mac OS X, Linux....). iODBC is a free project
licensed exclusively under the LGPL and BSD licenses, developed and
maintained by OpenLink Software. iODBC permits non-Windows systems to
communicate with databases via ODBC.

The ODBC API consists of a set of functions to enable any C/C++
applications linked against it to access and manage data. The ODBC
specification is currently maintained by Microsoft Corporation.

iODBC is compliant with the actual Microsoft ODBC version 3.51.

iODBC SDKs are different for each platform. iODBC SDKs are available
free of charge from the iODBC web site, released under the GNU Library
General Public License (LGPL). The SDKs are made up of include files
(.h), libraries for the corresponding platform, and a sample application
for testing and demonstration (odbctest). The sample application is an
Interactive Dynamic SQL Interpreter. Its sources are included for your
use as you see fit.

There are no drivers included with the iODBC SDK, but you can find many
on the OpenLink web site and from other third party middleware vendors.

You can find below a set of URLs for the right iODBC SDK regarding the
platform (which is the operating system and the CPU) you are targeting
at <a href="http://www.iodbc.org/opliodbc.htm" class="ulink"
target="_top">iodbc.org</a>.

</div>

</div>

</div>

</div>

<div class="toc">

**Table of Contents**

<span class="section">14.1. [iODBC SDK on
Unix](mt_iodbcsdklinux.html)</span>

<span class="section">14.2. [Configuring Data
Sources](mt_iodbcsdkconfdsn.html)</span>

<span class="section">14.2.1. [The Configuration
Files](mt_iodbcsdkconfdsn.html#mt_iodbcsdkunixfiles)</span>

<span class="section">14.2.2. [Making a Test
Connection](mt_iodbcsdkconfdsn.html#mt_iodbcsdktestunix)</span>

<span class="section">14.2.3. [Compiling Sample
Program](mt_iodbcsdkconfdsn.html#mt_compsampodbc)</span>

<span class="section">14.2.4. [Developing ODBC
Applications](mt_iodbcsdkconfdsn.html#mt_devodbc)</span>

<span class="section">14.2.5. [Further
Reading:](mt_iodbcsdkconfdsn.html#mt_furtherread)</span>

<span class="section">14.3. [Linking iODBC and ODBC Applications on Mac
OS](mt_iodbcappsmacos.html)</span>

<span class="section">14.3.1. [Mac OS
Classic](mt_iodbcappsmacos.html#mt_iodbcmacclassic)</span>

<span class="section">14.3.2. [Mac OS
X](mt_iodbcappsmacos.html#mt_iodbcmacosx)</span>

<span class="section">14.3.3.
[References](mt_iodbcappsmacos.html#mt_iodbcsdkrefs)</span>

<span class="section">14.3.4. [Porting Mac OS Classic ODBC applications
to Mac OS X](mt_iodbcappsmacos.html#mt_iodbcportappmac)</span>

</div>

</div>