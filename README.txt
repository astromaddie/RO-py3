The RO Python Package
---------------------

RO is a package of python utilities with an emphasis on cross-platform support (MacOS X, Windows and unix), Astronomy, Tkinter GUI extensions and Tkinter-compatible networking. It was developed to support a telescope user interface ([TUI](#TUI)).

### Download and Installation

Installing RO requires and python3-setuptools. saoDS9 is required to use RO.DS9.
Installing can be done with `sudo python3 setup.py install`

### Documentation

Find the modules you wish to use in the list here, then read the doc strings in the module and the examples at the end of most modules for more information.

-   **AddCallback**: mixin class for adding callback functionality to any object.
-   **Alg**: algorithms:
    -   GenericCallback, a shim between a caller who supplies too little information and the actual function you want to call. Also known as [function currying](http://en.wikipedia.org/wiki/Currying)
    -   **IDGen**: simple integer generator with programmable start and wrap values.
    -   **ListPlus**: extend lists with some useful dict methods.
    -   **MatchList**: Find matches for a string in a list of strings,optionally allowing abbreviations and ignoring case.
    -   **MultiDict**: a dictionary whose elements are a list of one or more items. *multidict*[*key*] = *value* adds *value* to the list of items for the specified *key* (or starts a new list if *key* was not present).
    -   **OrderedDict**: a dictionary that preserves the order of information as entered. (Note: this is not a sorted dict and the RO package does not yet include one.)

-   **Astro**: Astronomy package, including conversion between various coordinate systems and time functions. Note that this library is based Pat Wallace's slalib and as such requires payment to for commercial use.
    -   **Cnv**: Astronical routines using spherical coordinates. Includes a spherical version of coordConv, a general coordinate conversion function.
    -   **Sph**: Astronical routines using cartesian coordinates. Includes a cartesian version of coordConv, a general coordinate conversion function.
    -   **Tm**: time routines
    -   **llv**: low-level routines. These are mostly Python versions of slalib routines.
    
-   **CnvUtil**: type conversion utilities, including as asBool (unlike bool, accepts common string representations of True or False) and asIntOrNone and asFloatOrNone (unlike float, these return None for None or "NaN") and variants that allow specifying strings representing unknown values.
-   **Comm**: event-based network communications and timing using Twisted framework or tcl socket using Tkinter.
    -   **Generic**: contains a TCP/IP socket, a socket server and a timer. Call RO.Comm.Generic.setFramework to choose whether these are based on Twisted or Tkinter.
    -   **HTTPGet**: retrieve files via http. Requires Tkinter. An associated widget RO.Wdg.HTTPGetWdg offers a graphical display of file transfer.
    -   **TCPConnection**: a socket that allows repeated disconnection and reconnection and support for authentication. Requires Twisted framework or Tkinter, as chosen by RO.Comm.Generic.setFramework.
    -   **TkSocket**: contains a TCP/IP socket and a socket server based on Tcl/Tk. Requires Tkinter.
    -   **TwistedSocket**: contains several sockets and servers based on Twisted framework.
    -   **TwistedTimer**: contains a one-shot timer for triggering callbacks based on Twisted framework.
    -   **TkSerial**: a Tcl/Tk-based RS-232 connection. Requires Tkinter.
    -   **BrowseURL**: display a URL in the user's browser. Useful for displaying on-line help. This is a thin wrapper around webbrowser module that does not use the Tcl/Tk event loop.

-   **DS9**: allows one to easily load images into the [ds9](http://hea-www.harvard.edu/RD/ds9/) image viewer. Images can be loaded from numpy arrays, binary files or fits files. **Warnings:**
    -   RO.DS9 has a few [extra requirements](#DS9Requirements).
    -   RO.DS9.DS9Win.showArray does not work on Windows with ds9 3.0.3; this appears to be a bug in ds9 or xpa.

-   **Constants**: a few constants for using the RO package, including severity levels and the base URL for on-line help (with a routine \_setHelpURLBase to set it).
-   **InputCont**: containers for input widgets. Allows easy get and put for a set of input widgets and formatting of complex command strings.
-   **KeyDispatcher**: parse input data for keyword/value pairs and set registered KeyVariables accordingly. Useful for certain kinds of networked control applications.
-   **KeyVariable**: containers for keyword/value data. Useful for certain kinds of networked control applications, especially in conjunction with KeyDispatcher.
-   **LangUtil**: language utilities. funcName returns the name of a callable (function or callable class).
-   **MathUtil**: simple math functions, including:
    -   **checkRange**: assert that a number is in an allowed range
    -   wrapCtr and wrapPos: wrap an angle (in deg) into the desired range
    -   xyFromRTheta and rThetaFromXY: convert between x,y and r-theta coordinates (angle in deg)
    -   rot2d rotating x,y coordinates by a specified angle (in deg)
    -   **nint**:round to the nearest integer
    -   sign
    -   trig functions in degrees
    
-   **OS**: file-related functions, including:
    -   **findFiles**: recursively search for files whose names match specified patterns and don't match others. Easier to use than os.walk.
    -   getHomeDir, getPrefsDirs, getAppSupportDirs, etc: get the path to various standard directories on Mac, Windows or unix
    -   **getResourceDir**: obtain the directory for a particular resource of your application; useful for distributing bundled applications.
    -   **PlatformName**: one of "mac", "win" or "unix".
    -   **removeDupPaths**: remove duplicates from a list of paths
    -   **splitPath**: a variant of os.split that splits all components at once.

-   **ParseMsg**: parse keyword-value data. Intended for use by KeyDispatcher.
-   **PhysConst**: some basic units conversion constants and physical constants, especially those related to Astronomy.
-   **Prefs**: a complete implementation of user-settable preferences (using Tkinter), including automatic updating of fonts and colors and programmable updating of other attributes. Includes preferences for fonts, colors, sounds (pygame is required to play them), files and directories.
-   **procFiles**: easy batch processing of files. Differs from "fileinput" in that your user-defined function handles each input file in one call. This makes it very easy to do things such as include a header and footer for each file, write a separate output file for each input file or vary the output data depending on the file name. Ideal for drag-and-drop "droplets".
-   **PVT**: class for representing position, velocity, time data.
-   **ScriptRunner**: execute user-written scripts that wait for something to happen without halting the main Tkinter event loop. Based on generators.
-   **SeqUtil**: sequence utilities, such as isSequence (returns True if the argument is a sequence), asList (converts one item or a sequence of items to a list), etc.
-   **StringUtil**: string utilities including conversion of sexagesimal (dd:mm:ss and hh:mm:ss) strings to and from numbers.
-   **TkUtil**: utility functions for working with Tkinter, including:
    -   **getButtonNumbers**: returns the button number for the left, middle and right button (taking into account the difference between Mac and unix vs Windows).
    -   **addColors**: add colors with scaling or scale a single color.
    -   **colorOK**: check the validity of a color.
    -   **EvtNoProp**: function wrapper that prevents even propagation.
    -   **getWindowingSystem**: get the windowing system; one of: WSysAqua, WSysX11 or WSysWin.
    -   **TclFunc**: register a python function as a tcl callback.
    -   **Timer**: an event-based timer that calls a function after a specified delay.

-   **Wdg**: extensions of the standard Tkinter widgets and useful additional widgets. Almost all widgets support hot help strings (automatically displayed in a StatusBar, see below), linking to html htlp, a contextual menu, indication of severity level and indication of whether the data is current/defult. RO.Wdg widgets include:
    -   **Bindings**: various useful event bindings, including the ability to make Text and Entry widgets read-only while allowing the user to still copy data and bring up contextual menus. Also improves the standard bindings for Mac users.
    -   **CmdWdg**: widget for entering commands, with full command history. Often used with LogWdg (see below).
    -   **Entry**: entry widgets for integers, floats and sexagesimal (dd:mm:ss and hh:mm:ss) values. Includes range checking and (for sexagesimal values) the ability to omit fields.
    -   **Gridder**: simplifies gridding widgets that have a label, one or more data widgets and an optional units display. You supply the data display widgets and the gridder generates the label and units widget, auto-increments the row number and so on. The StatusConfigGridder does a similar job for displays that have the current values to the left and user-set new values to the right.
        -   **IsCurrentMixin**: mixin class to add support for indicating whether data in a widget is "current" or the default value (depending on how you use it). Most RO.Wdg widgets offer isCurrent support using this mixin.
    -   **Label**: widgets for displaying strings, numbers and sexagesimal (dd:mm:ss and hh:mm:ss) values. Also may be set automatically by KeyVariables, and offers integrated support for Prefs.
    -   **LogWdg**: widget for displaying logged data. Messages of different severity may be color-coded and shown or hidden. Includes provision for filtering out uninteresting entries, highlighting interesting entries and for searching.
    -   **OptionPanelControl**: supports showing and hiding panels of optional controls. The idea is somewhat similar to that of a tabbed pane, but multiple optional panels can be shown at one time.
    -   **RadiobuttonSet**: a wrapper around Tkinter.Radiobutton with help, default and isCurrent handling.
    -   **ScriptTk**: a wrapper around Tkinter.Tk that creates the usual root window but also creates a separate script window, so you can mess with things while your application is running. Formerly ROStdTk.
    -   **ScrolledWdg**: scrollable panel of widgets.
    -   **SeverityMixin**: mixin class to add support for indicating the severity level of the data. Most RO.Wdg widgets offer severity support using this class.
    -   **Sound**: play sound files using the pygame library.
    -   **StatusBar**: automatically displays "hot help" strings for RO.Wdg widgets in the same TopLevel. Also displays other messages color-coded by severity. Finally, can automatically display status for a command (a KeyVariable.KeyCommand sent to a KeyDispatcher).
    -   **Toplevel**: allows you to easily create multi-windowing applications that remember window position and which windows were open or closed.

License
-------

Most of RO is available under the MIT License (see docs/License.txt), but RO.Astro has a separate package (see its README.txt for details). The code is offered with no warranty of any kind.
    -   **HTTPGet**: download files via http with a display of all current, past and queued transfers. The user may abort a transfer. Basically this is like a typical web browser's file transfer manager, though without the ability to resume an interrupted transfer.
    
Notes
-----

The RO Package was developed to support [TUI](http://www.apo.nmsu.edu/35m_operations/TUI/), a user interface for the [Apache Point Observatory](http://www.apo.nmsu.edu/) 3.5m telescope. TUI is very specialized, but it does use most of the modules in RO. As such you may wish to examine TUI's [source code](http://www.apo.nmsu.edu/35m_operations/TUI-images/) for real-life examples of the use of various RO modules. Be sure to download the unix version, which is source code.

RO was partially developed using [WingIDE Professional](http://wingware.com/), an excellent integrated development environment. Thanks to the kind folks at WingWare for a free license.

    Russell Owen
    University of Washington
    PO Box 351580
    Seattle, WA 98195-1580
    rowen u washington edu
         @ .          .
