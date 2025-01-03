<div>

<div>

<div>

<div>

## 14.11. Python Hosting

</div>

</div>

</div>

Virtuoso functionality can be enhanced through external libraries by
loading shared objects or DLLs. The new functions are written in a
language of choice and compiled to produce a shared library appropriate
to the operating system. The path to the shared library must be declared
in the Virtuoso INI file and the server restarted before it can be used.

The Python language is hosted within Virtuoso in this way.
`hosting_python.so` (or `hosting_python.dll` ) is the library used.

The Python hosting module requires the Python library, version 2.2.2 or
above, to build and use the module, which then must be installed in the
Plugins-Load-path defined in the Virtuoso ini file. The source code and
build script (`build.py` ) for building the `hosting_python.so` module
are included in the Unix distribution in the `custom/hosting/python`
directory. The Unix installer will offer to build it near the end of the
installation process. The build.py is a kind of Makefile. On unix it
requires `libtool` and `cc` in the path. On windows it requires `cl.exe`
in the path.

The Virtuoso INI file uses a \[Plugins\] configuration section for
listing shared libraries for the server to load upon startup. An example
of this is:

``` programlisting
[Plugins]
LoadPath = /home/virtuoso/hosting
Load1 = Hosting, hosting_python.so
..
```

The "Hosting" type defines the entry points for initialization of the
runtime hosting environment, destruction of the user environment and
execution of a file or string containing commands in the hosted
language. It also returns a list of file extensions that it is capable
of processing. Virtuoso dynamically defines memory-resident (no disk
image) HTTP server handlers for each specified type.

The Python hosting plugin supports the 'py' extension. Hence, upon
initialization of the hosting plugin, Virtuoso defines the
`__http_handler_py(..)` function according to the API for file type
handlers in the Virtuoso HTTP server. With this handler in place, each
hit on a .py file (file system or WebDAV) with appropriate execute
permissions will cause the HTTP server to execute the code within it and
return the result instead of simple the file contents.

The python interpreter has a global lock unrelated to the Virtuoso
hosting module, thus no more than one thread can run python code at a
time.

The handler will call the \_\_hosting_http_handler VSE with a special
set of parameters to represent the HTTP environment correctly. Virtuoso
will, by default call the plugin to memory as required, and expel it
when finished. This behavior can be controlled by the INI file
parameter:

``` programlisting
[HTTPServer]
PersistentHostingModules = 1/0 default 0
```

Setting `PersistentHostingModules` to "1" prevents Virtuoso from
removing the interpreters from the HTTP threads after each request.

<div>

|                            |                                                                        |
|:--------------------------:|:-----------------------------------------------------------------------|
| ![\[Tip\]](images/tip.png) | See Also:                                                              |
|                            | <a href="vseplugins.html" class="link" title="18.6. VSEI Plugins">VSEI 
                              Plugins</a>                                                             |

</div>

<div>

**Example 14.68. Using the Python Plugin**

<div>

Executing Python code directly:

``` programlisting
select __hosting_http_handler ('py', 'print "hello world"; ', '', vector (), 'helloworld.py');
```

``` programlisting
returns : hello world
```

Executing a python script file (python/test_print.py in the Virtuoso
working directory):

``` programlisting
python/test_print.py
-------------------
#!/usr/bin/python
print "hello world file";
```

``` programlisting
select __hosting_http_handler ('py', 'python/test_print.py');
```

``` programlisting
returns : hello world file
```

</div>

</div>

  

</div>
