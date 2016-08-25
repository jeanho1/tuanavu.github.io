---
title: "Notebook Introduction"
categories:
  - Test
tags:
  - Test
---
# An introduction to the IPython notebook


The IPython web notebook is a frontend that allows for new modes
of interaction with IPython: this web-based interface allows you to execute Python and IPython
commands in each input cell just like you would at the IPython terminal or Qt console, but you can
also save an entire session as a document in a file with the `.ipynb` extension.

The document you are reading now is precisely an example of one such notebook, and we will show you
here how to best use this new interface.

The first thing to understand is that a notebook consists of a sequence of 'cells' that can contain 
either text (such as this one) or code meant for execution (such as the next one):

* Text cells can be written using [Markdown syntax](http://daringfireball.net/projects/markdown/syntax) 
(in a future release we will also provide support for reStructuredText and Sphinx integration, and we 
welcome help from interested contributors to make that happen).

* Code cells take IPython input (i.e. Python code, `%magics`, `!system calls`, etc) like IPython at
the terminal or at the Qt Console.  The only difference is that in order to execute a cell, you *must*
use `Shift-Enter`, as pressing `Enter` will add a new line of text to the cell.  When you type 
`Shift-Enter`, the cell content is executed, output displayed and a new cell is created below.  Try
it now by putting your cursor on the next cell and typing `Shift-Enter`:


```
"This is the new IPython notebook"
```




    'This is the new IPython notebook'



You can re-execute the same cell over and over as many times as you want.  Simply put your
cursor in the cell again, edit at will, and type `Shift-Enter` to execute.  

**Tip:** A cell can also be executed
*in-place*, where IPython executes its content but leaves the cursor in the same cell.  This is done by
typing `Ctrl-Enter` instead, and is useful if you want to quickly run a command to check something 
before tping the real content you want to leave in the cell. For example, in the next cell, try issuing
several system commands in-place with `Ctrl-Enter`, such as `pwd` and then `ls`:


```
ls
```

    00_notebook_tour.ipynb          callbacks.ipynb                 python-logo.svg
    01_notebook_introduction.ipynb  cython_extension.ipynb          rmagic_extension.ipynb
    Animations_and_Progress.ipynb   display_protocol.ipynb          sympy.ipynb
    Capturing Output.ipynb          formatting.ipynb                sympy_quantum_computing.ipynb
    Script Magics.ipynb             octavemagic_extension.ipynb     trapezoid_rule.ipynb
    animation.m4v                   progbar.ipynb


In a cell, you can type anything from a single python expression to an arbitrarily long amount of code 
(although for reasons of readability, you should probably limit this to a few dozen lines):


```
def f(x):
    """My function
    x : parameter"""
    
    return x+1

print "f(3) = ", f(3)
```

    f(3) =  4


## User interface

When you start a new notebook server with `ipython notebook`, your
browser should open into the *Dashboard*, a page listing all notebooks
available in the current directory as well as letting you create new
notebooks.  In this page, you can also drag and drop existing `.py` files
over the file list to import them as notebooks (see the manual for 
[further details on how these files are 
interpreted](http://ipython.org/ipython-doc/stable/interactive/htmlnotebook.html)).

Once you open an existing notebook (like this one) or create a new one,
you are in the main notebook interface, which consists of a main editing
area (where these cells are contained) as well as a menu and 
permanent header area at the top, and a pager that rises from the
bottom when needed and can be collapsed again.

### Main editing area

Here, you can move with the arrow keys or using the 
scroll bars.  The cursor enters code cells immediately, but only selects
text (markdown) cells without entering in them; to enter a text cell,
use `Enter` (or double-click), and `Shift-Enter` to exit it again (just like to execute a 
code cell).

### Menu

The menu bar conains all the commands you can use to manipulate the notebook.

The *File* menu has the usual open/save file operations, as well as Export,
for downloading the notebook to your computer.

*Edit* has controls for cut/copy/paste, and moving cells around.

*View* lets you toggle visibility of the header elements,
to recover precious screen real estate.

The *Cell* menu lets you manipulate individual cells,
and the names should be fairly self-explanatory.

The *Kernel* menu lets you signal the kernel executing your code. 
`Interrupt` does the equivalent of hitting `Ctrl-C` at a terminal, and
`Restart` fully kills the kernel process and starts a fresh one.  Obviously
this means that all your previous variables are destroyed, but it also
makes it easy to get a fresh kernel in which to re-execute a notebook, perhaps
after changing an extension module for which Python's `reload` mechanism
does not work.

The *Help* menu contains links to the documentation of some projects
closely related to IPython as well as the minimal keybindings you need to
know.  But you should use `Ctrl-m h` (or click the `QuickHelp` button at
the top) and learn some of the other keybindings, as it will make your 
workflow much more fluid and efficient.

You will also see a few buttons there for common actions,
and hovering over each button will tell you which command they correspond to,
if the icons are not clear enough.

### Header bar

The header area at the top allows you to rename an existing 
notebook and open up a short help tooltip.  This area also indicates
with a red **Busy** mark on the right whenever the kernel is busy executing
code.

### The pager at the bottom

Whenever IPython needs to display additional 
information, such as when you type `somefunction?` in a cell, the notebook
opens a pane at the bottom where this information is shown.  You can keep
this pager pane open for reference (it doesn't block input in the main area)
or dismiss it by clicking on its divider bar.

### Tab completion and tooltips

The notebook uses the same underlying machinery for tab completion that 
IPython uses at the terminal, but displays the information differently.
Whey you complete with the `Tab` key, IPython shows a drop list with all
available completions.  If you type more characters while this list is open,
IPython automatically eliminates from the list options that don't match the
new characters; once there is only one option left you can hit `Tab` once
more (or `Enter`) to complete.  You can also select the completion you
want with the arrow keys or the mouse, and then hit `Enter`.

In addition, if you hit `Tab` inside of open parentheses, IPython will 
search for the docstring of the last object left of the parens and will
display it on a tooltip. For example, type `list(<TAB>` and you will
see the docstring for the builtin `list` constructor:


```
# Position your cursor after the ( and hit the Tab key:
range(
```

Moreover, pressing tab several time in a row allows you change the behaviour of the tooltip.

* first `tab` press, you get a classical tooltip
* second tab, the tooltip grow vertically, and allow you to scroll the docstring
* third tab, tooltip will be made sticky for 10 seconds, allowing you to carry on typing while it stays open.
* forth tab, the tooltip help is sent to the pager at the bottom of the screen.
<script>
    IPython.tooltip.tabs_functions = [  function(cell,text){
                                    IPython.tooltip._request_tooltip(cell,text);
                                    IPython.notification_widget.set_message('tab again to expand pager',2500);
                                    setTimeout(function(){
                                        $('.tooltiptext pre').text("function signture : You've invoked a tooltip !\n\nWell done! Here usualy lies the current function *call signature* and it's *docstring*. You can now expand the tooltip pressing <tab> a second time...")},400);
                                    },
                                 function(){
                                    IPython.tooltip.expand();
                                    IPython.notification_widget.set_message('tab again to make pager sticky for 10s',2500);
                                    setTimeout(function(){
                                        $('.tooltiptext pre').text("Now the tooltip is expanded !\
                                          \n\nThis is really usefull if you have long docstring and if you want to be able to scroll them. \
For example, I can give you many information about the tooltip:\n - The tooltip is smart, and \
you don't always need to press tab to invoke it, if you press an opening bracket `(` then nothing \
for some time, tooltip will be invoked by itself.\
\n - Also you can hoover over the icon on the top right to know what they are dooing...\
\n\nBack to the next lesson.\n\nSometime you need to the tooltip to stay on screen while\
you type. That's the reason for the sticky mode (indicated by a small clock on the top left of the tooltip),\
\n\nNow press <tab> a 3rd time and continue typing some text to test it...")
                                            },400);
                                 },
                                 function(){
                                     var time = 35;
                                     IPython.tooltip.stick(time);
                                     $('.tooltiptext pre').text("Type more text !...\n\n range(7,125,3)\n\n The tooltip is in sticky mode, it won't be dismissed for at least 10 secondes ",400);
                                     setTimeout(function(){
                                         $('.tooltiptext pre').text("That was sticky mode...\nI'll keep it on 15 more seconds just for you.\n\nLast thing you can do is send the current help displayed in the tooltip to the pager at the bottom of the screen. To do that, press tab 4 time in a row after a parenthesis. \n\n Now I'll stop bothering you and let you Play with the tooltip !");
                                         reset_tooltip()
                                            },15000);
                                 },
                                 function(cell){
                                    IPython.tooltip.cancel_stick();
                                    reset_tooltip()
                                    IPython.tooltip.showInPager(cell);
                                    IPython.tooltip._cmfocus();
                                    }
                                ];
    
    reset_tooltip = function(){
    IPython.tooltip.tabs_functions = [  function(cell,text){
                                    IPython.tooltip._request_tooltip(cell,text);
                                    IPython.notification_widget.set_message('tab again to expand pager',2500);
                                    },
                                 function(){
                                    IPython.tooltip.expand();
                                    IPython.notification_widget.set_message('tab again to make pager sticky for 10s',2500);
                                 },
                                 function(){
                                     IPython.tooltip.stick();
                                     IPython.notification_widget.set_message('tab again to open help in pager',2500);
                                 },
                                 function(cell){
                                    IPython.tooltip.cancel_stick();
                                    IPython.tooltip.showInPager(cell);
                                    IPython.tooltip._cmfocus();
                                    }
                                ];
    }
</script>

## The frontend/kernel model

The IPython notebook works on a client/server model where an *IPython kernel*
starts in a separate process and acts as a server to executes the code you type,
while the web browser provides acts as a client, providing a front end environment
for you to type.  But one kernel is capable of simultaneously talking to more than
one client, and they do not all need to be of the same kind.  All IPython frontends
are capable of communicating with a kernel, and any number of them can be active
at the same time.  In addition to allowing you to have, for example, more than one
browser session active, this lets you connect clients with different user interface features.

For example, you may want to connect a Qt console to your kernel and use it as a help
browser, calling `??` on objects in the Qt console (whose pager is more flexible than the
one in the notebook).  You can start a new Qt console connected to your current kernel by 
using the `%qtconsole` magic, this will automatically detect the necessary connection
information.

If you want to open one manually, or want to open a text console from a terminal, you can 
get your kernel's connection information with the `%connect_info` magic:


```
%connect_info
```

    {
      "stdin_port": 52858, 
      "ip": "127.0.0.1", 
      "hb_port": 52859, 
      "key": "7efd45ca-d8a2-41b0-9cea-d9116d0fb883", 
      "shell_port": 52856, 
      "iopub_port": 52857
    }
    
    Paste the above JSON into a file, and connect with:
        $> ipython <app> --existing <file>
    or, if you are local, you can connect with just:
        $> ipython <app> --existing kernel-b3bac7c1-8b2c-4536-8082-8d1df24f99ac.json 
    or even just:
        $> ipython <app> --existing 
    if this is the most recent IPython session you have started.


## The kernel's `raw_input` and `%debug`

The one feature the notebook currently doesn't support as a client is the ability to send data to the kernel's
standard input socket.  That is, if the kernel requires information to be typed interactively by calling the
builtin `raw_input` function, the notebook will be blocked.  This happens for example if you run a script
that queries interactively for parameters, and very importantly, is how the interactive IPython debugger that 
activates when you type `%debug` works.

So, in order to be able to use `%debug` or anything else that requires `raw_input`, you can either use a Qt 
console or a terminal console:

- From the notebook, typing `%qtconsole` finds all the necessary connection data for you.
- From the terminal, first type `%connect_info` while still in the notebook, and then copy and paste the 
resulting information, using `qtconsole` or `console` depending on which type of client you want.

## Display of complex objects

As the 'tour' notebook shows, the IPython notebook has fairly sophisticated display capabilities.  In addition
to the examples there, you can study the `display_protocol` notebook in this same examples folder, to 
learn how to customize arbitrary objects (in your own code or external libraries) to display in the notebook
in any way you want, including graphical forms or mathematical expressions.

## Plotting support

As we've explained already, the notebook is just another frontend talking to the same IPython kernel that
you're familiar with, so the same options for plotting support apply.

You can enable inline plotting with `%pylab inline`:


```
%pylab inline
```

    
    Welcome to pylab, a matplotlib-based Python environment [backend: module://IPython.zmq.pylab.backend_inline].
    For more information, type 'help(pylab)'.


If you start the notebook server itself with `--pylab`, you will get matplotlib's floating, interactive windows and you
can call the `display` function to paste figures into the notebook document.  If you start it with 
`--pylab inline`, all plots will appear inline automatically.  In this regard, the notebook works identically
to the Qt console.

Note that if you start the notebook server with pylab support, *all* kernels are automatically started in
pylab mode and with the same choice of backend (i.e. floating windows or inline figures).
For this reason, it is recommended that you
start the notebook server simply by typing `ipython notebook`, and then selectively turn on pylab support 
only for the notebooks you want by using the `%pylab` magic (see its docstring for details).


```
plot(rand(100))
```




    [<matplotlib.lines.Line2D at 0x1124ba350>]




![png](output_32_1.png)


## Security

By default the notebook only listens on localhost, so it does not expose your computer to attacks coming from
the internet.  By default the notebook does not require any authentication, but you can configure it to
ask for a password before allowing access to the files.  

Furthermore, you can require the notebook to encrypt all communications by using SSL and making all connections
using the https protocol instead of plain http.  This is a good idea if you decide to run your notebook on
addresses that are visible from the internet.  For further details on how to configure this, see the
[security section](http://ipython.org/ipython-doc/stable/interactive/htmlnotebook.html#security) of the 
manual.

Finally, note that you can also run a notebook with the `--read-only` flag, which lets you provide access
to your notebook documents to others without letting them execute code (which can be useful to broadcast
a computation to colleagues or students, for example).  The read-only flag behaves differently depending
on whether the server has a password or not:

- Passwordless server: users directly see all notebooks in read-only mode.
- Password-protected server: users can see all notebooks in read-only mode, but a login button is available
and once a user authenticates, he or she obtains write/execute privileges.

The first case above makes it easy to broadcast on the fly an existing notebook by simply starting a *second* 
notebook server in the same directory as the first, but in read-only mode.  This can be done without having
to configure a password first (which requires calling a hashing function and editing a configuration file).

**NOTE:**  IPython 0.13's javascript rewrite did not include read-only UI, so it does not work well.
Code/notebooks are still protected from unauthorized access, but the UI is not appropriately restricted.
