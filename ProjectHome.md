# Moving to BitBucket #

**New project home:** https://bitbucket.org/almworks/sqlite4java

Sqlite4java is being moved to BitBucket, because [Google shuts down Google Code](http://google-opensource.blogspot.jp/2015/03/farewell-to-google-code.html). We have moved almost everything, but unfortunately some content will be lost:

  * Comments left on the wiki pages will not be moved. On BitBucket, please use Issues to raise any questions.
  * Votes / watches and reporters on the issues are not moved, as BitBucket cannot assign those to specific users. If you're watching / voting for an open issue, please visit [issue list](https://bitbucket.org/almworks/sqlite4java/issues?status=new&status=open) and vote / watch on the issues again.
  * Old attachments to issues do work but they are hosted on Google Code. They will stop working when Google Code shuts down.

We are sorry for the inconvenience. We'd love to keep the project here.


---


**Download latest version:**

  * [sqlite4java-392](https://d1.almworks.com/.files/sqlite4java/sqlite4java-392.zip) with **SQLite 3.8.7**, Windows/Linux/Mac OS X/Android binaries
  * [OSGi bundle 1.0.392](https://d1.almworks.com/.files/sqlite4java/com.almworks.sqlite4java-1.0.392.jar) with sqlite4java-392

Files for previous versions are available in the Downloads section.


---


# About sqlite4java #

sqlite4java is a minimalistic Java wrapper for SQLite. [SQLite](http://sqlite.org) is a free, compact, robust, embeddable SQL database engine. **sqlite4java** is built with the purpose to provide high-performance, low-garbage interface to SQLite for desktop Java applications.

sqlite4java is not a JDBC driver. Access to the database is made through the custom interfaces of `com.almworks.sqlite4java` package. Tighter integration with SQLite offers better performance and features not available through JDBC interfaces.

sqlite4java is built for use on Windows, Linux, Mac OS X and Android, although you can try to compile it on other platforms. Required JRE version is 1.5. SQLite is pre-compiled and distributed along with the Java classes as dynamic JNI libraries.

sqlite4java is a stable library that we (ALM Works) use in our production applications. The API may not support some of the SQLite functions, but most functionality is covered. Feel free to request improvements or suggest patches.

  * [Getting Started](GettingStarted.md)
  * [Comparison to Other Java Wrappers for SQLite](ComparisonToOtherWrappers.md)
  * [Javadoc](http://almworks.com/sqlite4java/javadoc/index.html)
  * [Using in a Maven 2 project](UsingWithMaven.md)

# Supported Platforms #

  * Windows i386/x64
  * Linux i686/amd64
  * Mac OS X 10.5 or later (i686/x64)
  * Android x86/armv7/armv5

# Features #

  * **Thin JNI-based wrapper** for <a href='http://sqlite.org/c3ref/funclist.html'>SQLite C Interface</a>. Most of SQLite's user functions (not extender functions) are either already provided by the library or can be easily added.
  * **Single-threaded model** - each SQLite connection is confined to a single thread, all calls must come from that thread. Application may open several connections to the same database from different threads. Along with the Serializable isolation level from SQLite, this feature facilitates writing very clean and predictable code.
  * **Bulk retrieval** from SELECT statements, greatly improving speed and garbage rate via minimizing the number of JNI calls to `step()` and `column...()` methods. See  [SQLiteStatement.loadInts()](http://almworks.com/sqlite4java/javadoc/index.html) for example.
  * **Interruptible statements** support allows to cancel a long-running query or update. See [SQLiteConnection.interrupt()](http://almworks.com/sqlite4java/javadoc/index.html).
  * **Long array binding** allows to represent a `long[]` Java array as an SQL table. Table lookup is optimized if you specify that the array is sorted and/or has unique values. See [SQLiteLongArray](http://almworks.com/sqlite4java/javadoc/index.html).
  * **Incremental BLOB I/O** maps to `sqlite3_blob...` methods, which provide means to read/write portions of a large BLOB. See [SQLiteBlob](http://almworks.com/sqlite4java/javadoc/index.html).
  * **BLOBs as streams** - you can bind parameter as an `OutputStream` and read column value as `InputStream`. See [SQLiteStatement.bindStream()](http://almworks.com/sqlite4java/javadoc/index.html) for example.
  * **Job queue implementation** lets you queue database jobs in a multi-threaded application, to be executed one-by-one in a dedicated database thread. See [JobQueue](JobQueue.md).
  * **SQL Profiler** collects statistics on the executed SQL.
  * **Backup API** support lets you use SQLite's hot backup feature. See [SQLiteConnection.initializeBackup()](http://almworks.com/sqlite4java/javadoc/index.html).


# License #

**sqlite4java** is licensed under Apache License 2.0. Contact info@almworks.com if you'd like to have it licensed under different terms.