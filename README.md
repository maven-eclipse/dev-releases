# Eclipse SWT for Maven Users - Dev Version

**This repo is for the dev milestone (M) and release candidate (RC) versions. [See the main repository for stable releases](http://github.com/maven-eclipse/maven-eclipse.github.io)**

SWT is not available in Maven Central making it difficult to use in Maven projects. Existing maven repos are either not maintained and abandoned, don't have all platforms, don't contain sources, don't contain debug jar, or don't automate downloading and extracting the JARs. 

This repo contains SWT 4.5+ on all supported platforms

 - Stable releases
  - 4.6RC1 - 12 May 2016
  - 4.6M7 - 28 Apr 2016
  - 4.6M6 - 17 Mar 2016
  - 4.6M5 - 28 Jan 2016
  - 4.6M4 - 9 Dec 2015
  - 4.6M3 - 29 Oct 2015
  - 4.6M2 - 16 Sep 2015
  - 4.6M1 - 5 Aug 2015
  - 4.5.2RC4 - 12 Feb 2016
  - 4.5.2RC3 - 3 Feb 2016
  - 4.5.2RC2 - 28 Jan 2016
  - 4.5.2RC1 - 13 Jan 2016
  - 4.5.1RC3 - 4 Sep 2015
  - 4.5.1RC2 - 27 Aug 2015
  - 4.5RC4 - 3 Jun 2015
  - 4.5RC3 - 28 May 2015
  - 4.5RC2a - 22 May 2015
  - 4.5RC1 - 14 May 2015
  - 4.5M7 - 30 Apr 2015
  - 4.5M6 - 20 Mar 2015
  - 4.5M5a - 3 Feb 2015
  - 4.5M5 - 29 Jan 2015
  - 4.5M4 - 10 Dec 2014
  - 4.5M3 - 29 Oct 2014
  - 4.5M2 - 18 Sep 2014
  - 4.5M1 - 6 Aug 2014
 - Platforms
  - org.eclipse.swt.win32.win32.x86
  - org.eclipse.swt.win32.win32.x86_64
  - ~~org.eclipse.swt.cocoa.macosx~~ - Obsoleted after 4.5M1
  - org.eclipse.swt.cocoa.macosx.x86_64
  - org.eclipse.swt.gtk.linux.x86
  - org.eclipse.swt.gtk.linux.x86_64
  - org.eclipse.swt.gtk.solaris.sparc
  - org.eclipse.swt.gtk.solaris.x86
  - org.eclipse.swt.gtk.aix.ppc
  - org.eclipse.swt.gtk.aix.ppc64
  - org.eclipse.swt.gtk.hpux.ia64
  - org.eclipse.swt.gtk.linux.ppc
  - org.eclipse.swt.gtk.linux.ppc64
  - org.eclipse.swt.gtk.linux.ppc64le
 - Each ZIP is extracted as follows
  - swt.jar - Main JAR
  - swt-debug.jar - Add `<classifier>debug</classifier>` 
  - src.zip - `sources` classifier, most IDE's can handle downloading this
 
Want JFace support? Please see [Issue #1](https://github.com/maven-eclipse/maven-eclipse.github.io/issues/1)
  
# Why?
Eclipse has an open bug report to to publish SWT to Maven however its been stalled since 2007: https://bugs.eclipse.org/bugs/show_bug.cgi?id=199302

Currently the only available automated downloader is [swt-release-fetcher](http://github.com/hennr/swt-release-fetcher) which only supports the latest release and is very complex. This has been replaced with a much simpler and more flexible bash script that you can even use to setup your own independent repo 

As of creating this project, existing public SWT maven repositories are not usable
 - https://code.google.com/p/swt-repo/ - Abandoned, last release is 4.4
 - https://github.com/urish/swt-repo - Deleted
 - https://github.com/swt-repo/swt-repo - Abandoned, last release 4.2.2 only for linux
 - https://bitbucket.org/confluenity/maven ([from StackOverflow](http://stackoverflow.com/a/19857630)) - Abandoned, original domain doesn't work, bitbucket repo isn't web accessible, last release is 4.3.1

# How to use
If you were using [swt-repo on Google Code](http://code.google.com/p/swt-repo/) this is a drop in replacement

Add this to your pom.xml:

```
<repositories>
	<repository>
		<id>maven-eclipse-repo-dev</id>
		<url>http://maven-eclipse.github.io/dev-releases/maven</url>
	</repository>
</repositories>
```

Then add dependencies for each platform you wish to support. The most common are

```
<dependencies>
	<dependency>
		<groupId>org.eclipse.swt</groupId>
		<artifactId>org.eclipse.swt.win32.win32.x86</artifactId>
		<version>${swt.version}</version>
    <!-- To use the debug jar, add this -->
    <classifier>debug</classifier>
	</dependency>
	<dependency>
		<groupId>org.eclipse.swt</groupId>
		<artifactId>org.eclipse.swt.win32.win32.x86_64</artifactId>
		<version>${swt.version}</version>
	</dependency>
	<dependency>
		<groupId>org.eclipse.swt</groupId>
		<artifactId>org.eclipse.swt.gtk.linux.x86</artifactId>
		<version>${swt.version}</version>
	</dependency>
	<dependency>
		<groupId>org.eclipse.swt</groupId>
		<artifactId>org.eclipse.swt.gtk.linux.x86_64</artifactId>
		<version>${swt.version}</version>
	</dependency>
	<dependency>
		<groupId>org.eclipse.swt</groupId>
		<artifactId>org.eclipse.swt.cocoa.macosx.x86_64</artifactId>
		<version>${swt.version}</version>
	</dependency>
</dependencies>
```

