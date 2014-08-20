Version history for the [RO Python Package](Overview.html)
----------------------------------------------------------

### 3.5.1 2014-07-24

-   RO.Wdg.Entry: disabling the widget now makes the widget lose focus and saves unsaved edits.
-   RO.TkUtil: Timer.\_\_init\_\_ now accepts keyword arguments for the callback function.
-   RO.ScriptRunner: added waitPause and waitSec methods.

### 3.5.0 2014-06-17

-   RO.Wdg.InputContPresetsWdg: added autoUpdate argument to display the current preset value; by default it is automatically determined by whether "text" is specified.
-   Added RO.Wdg.Menubutton to encapsulated my attempt to work around Tk 8.5 MacOS Aqua width bugs and provide basic help functionality.
-   Modified RO.Wdg.OptionMenu and RO.Wdg.InputContPresetsWdg to use RO.Wdg.Menubutton.
-   Changed all uses of isinstance(val, str) to isinstance(val, basestring); this affected RO.StringUtil.splitDMSStr, RO.Wdg.Entry, and RO.Prefs.PrefVar.
-   RO.Wdg.Button, RO.Wdg.Menubutton, RO.Wdg.PathWdg: fixed getEnable to handle active state properly.

### 3.4.5 2014-05-07

-   RO.ScriptRunner bug fix: ScriptRunner.value was lost (set to None) on resume.

### 3.4.4 2014-04-28

-   RO.AddCallback: added safeCall2, which gives more information on error than safeCall and modified current code to use it.
-   RO.SeqUtil.isSequence: bug fix: an unexpected exception was being raised for some values.
-   RO.Astro.Tm: fixed a bug in isoDateTimeFromPySec: an extra 0 before the decimal point if nDig\>0.

### 3.4.3 2014-04-10

-   RO.Comm.TwistedSocket: restored host and port attributes to Socket

### 3.4.2 2014-04-10

-   RO.Comm minor improvements:
    -   Added NullTCPSocket with host and port.
    -   TwistedSocket: moved host and port properties from Socket to TCPSocket and modified them to provide correct answers if the socket is not connected. This improves the error message from trying to write while not connected.
    -   TkSocket: improved the error message from trying to write while not connected.

### 3.4.1 2014-03-14

-   RO.Alg.SavedDict: pretty-print the saved dict to make it easier to edit.
-   RO.Wdg.InutContConfigWdg: added helpText and helpURL arguments.

### 3.4.0 2014-03-14

-   Added RO.Alg.SavedDict: a dictionary that saves changes to a file (e.g. for user-specified configs).
-   Added RO.Wdg.InutContConfigWdg: manage default and user-specified configs for input containers.
-   RO.Comm enhancements:
    -   Added didFail method to sockets, server sockets and TCPConnection.
    -   Added isDisconnected method to TCPConnection
    -   Sockets and TCPConnection accept a timeLim argument in their constructor to limit the time spent trying to make a connection.
    -   Sockets accept addStateCallback and removeStateCallback; setStateCallback is deprecated.
    -   The twisted version of TCPServer.port is the port actually used, if constructed with port=0
    -   TwistedSocket.Socket bug fix: readCallback is no longer called when the socket is closing.

-   RO.Wdg.OptionMenu:
    -   Added forceValid argument to set().
    -   Improve label handling: the widget width was affected by the current value, rather than the width of the label, and label="" was treated as None.

-   RO.Wdg.ToplevelSet: added getNamesInGeomFile method.
-   RO.Wdg.InputContPresetsWdg: fixed to not omit defaults when getting values from an input container.
-   RO.InputCont: added omitDef to all getValueDict and getValueList methods.
-   RO.CmdVar: bug fix: sent the command "None" when cancelled if no abortCmdStr was specified. This bug was introduced in 3.0.2.
-   Made numpy optional in the ups table, so as to work with minimal stacks that use system python and full stacks that use an included python and/or numpy.

### 3.3.0 2013-12-10

-   Added RO.AddCallback.safeCall: a function that calls another function and logs any errors without raising an exception.
-   Added RO.Generic.WaitForTCPServer: a functor that calls a callback function when a TCP server is available.
-   Updated tools/fitsinfo.py to handle multiple fits HDUs.
-   TkUtil.Timer.start accepts keyword arguments for the callback function.
-   Updated tools/fitsinfo.py to handle multiple HDUs and to only compute stats for image HDUs.
-   Added numpy to the ups table (for those who use eups to manage RO).

### 3.2.2 2013-09-05

-   Changed "import Image" to "from PIL import Image" for compatibility with Pillow, a modern replacement for PIL.

### 3.2.1 2013-09-03

-   Changed RO.Wdg.Sound to raise RuntimeError if the specified sound file does not exist. Unfortunately there is no warning if the file exists but is not in a usable format (I don't know how to get pygame.mixer.Sound to check; at one time I think it raised an exception but it certainly does not do so now).

### 3.2.0 2012-12-19

-   Added RO.Prefs.FontSizePrefVar: set font size while using the standard typeface.

### 3.1.0 2012-12-07

-   RO.Astro.Tm: added setClockError, getClockError and getCorrPySec to support keeping correct time even if the user's clock is off. You are responsible for figuring out the clock error and calling setClockError.

### 3.0.4 2012-12-06

-   RO.Wdg.Checkbutton, OptionMenu and Radiobutton: yet another refinement to the width workaround for Aqua Tk 8.5: apply no correction if the widget has a bitmap (in which case width is in pixels, not characters).
-   RO.Wdg.Radiobutton fix: if using bitmaps the active button was not highlighted, at least on Aqua Tk 8.5.
-   Fixed much demo code by setting RO.Comm.Generic framework to Tk by default in some cases. You should still call RO.Comm.Generic.setFramework if you want to use objects in RO.Comm.Generic.

### 3.0.3 2012-11-30

-   RO.Wdg:Checkbutton, OptionMenu and RadiobuttonSet: further improvement to Aqua Tk 8.5 width bug. The workaround now works if one changes the width after creating the widget. (Though OptionMenu has a second workaround for a different width bug that only applies if width=0 and is only engaged if you construct the widget with that width).
-   RO.Wdg.Radiobutton: added width bug workaround (moving it here from RadiobuttonSet).

### 3.0.2 2012-11-29

-   RO.Comm.TwistedSocket: socket now tries to convert text to ASCII before sending. This works around a Twisted Framework misfeature that unicode strings containing only ASCII are rejected (one that shows up often when using Tkinter with Tk 8.5 because many strings now always come back as unicode).
-   RO.Wdg: more workarounds for Aqua Tk issues:
    -   RO.Wdg.RadioButton: workaround the fact that the widget is too narrow if width is nonzero. Fix demo code and demo nonzero width.
    -   RO.Wdg.CheckButton: improve workaround for widget too narrow if width is nonzero; it now acts very similar to unix if using default fonts. I could get fancier and use font metrics, but at this point I think it's good enough. Fix demo code and demo nonzero width.
    -   RO.Wdg.OptionMenu: improved workaround for widget too narrow if width is nonzero. Fix demo code and demo nonzero width.

### 3.0.1 2012-11-19

-   RO.TkUtil: added getTclVersion function.
-   Work around more display bugs in Tk on MacOS X
    -   RO.Wdg.OptionMenu
        -   Work around Tck/Tk bug \#3587262: menubutton is sometimes too narrow on MacOS if width=0.
        -   Work around Tcl/Tk bug or misfeature \#3580194: menubutton is too narrow on MacOS if width is nonzero.

    -   RO.Wdg.Checkbutton: work around a Tcl/Tk bug: the width is too narrow on MacOS X if width is nonzero.

### 3.0.0 2012-09-28

-   RO.Comm
    -   This is a major overhaul. The big news is the addition of support for communicating using Twisted instead of Tkinter. Backward-incompatible changes include:
        -   You must call RO.Comm.Generic.setFramework before using RO.ScriptRunner, RO.KeyDispatcher, RO.KeyVariable or anything in the new sub-package RO.Comm.Generic.
        -   Many methods are now attributes, for example: isDone() is now isDone and getState() is now state.
        -   State constants are now always strings, not integers. As a result getFullState() is now fullState and only returns two items, not three.
        -   RO.Comm.FTPGet: state constants are now class constants, like all other RO.Comm classes.

    -   RO.Comm.Generic: event-based TCP/IP connections and event-based timers using Tcl/Tk or Twisted.
    -   RO.Comm.TkSocket:
        -   Renamed TkSocket to TCPSocket.
        -   Renamed TkSocket addr argument to host for consistency with TCPConnection and Twisted framework.
        -   Renamed TkServerSocket to TCPServer and expanded its capabilities.
        -   Removed BaseServer; use TCPServer instead.
        -   Eliminated the binary argument to TCPSocket and eliminated tcl end-of-line translation; instead writeLine always appends \\r\\n and readLine breaks on any of \\r\\n, \\n or \\r. This provides more predictable behavior and matches the behavior of TwistedSocket.TCPSocket.

    -   RO.Comm.TwistedSocket: event-based TCP/IP communications using Twisted framework.
    -   RO.Comm.TwistedTimer: event-based timers using Twisted framework.
    -   Added some unit tests in ROPackage/tests; these must be run using Twisted Trial.

-   Eliminated the dependency on Tkinter in the following modules; you may use Twisted for the event loop, instead. As noted above, you must call RO.Comm.Generic.setFramework before using these:
    -   RO.ScriptRunner. Note that the "master" argument is now optional and moved to later in the argument list.
    -   RO.KeyDispatcher
    -   RO.KeyVariable

-   RO.Wdg
    -   RO.Wdg.DirWdg and FileWdg: modified to treat a path of "" like None. This improves path and dir preference behavior when no default is specified.
    -   Removed almost all use of update\_idletasks. Most were relics of older, buggier versions of Tcl/Tk for MacOS X. A few needed some other workaround.

-   RO.TkUtil.Timer:
    -   Added isActive property
    -   Bug fix: could not construct a Timer if sec and callFunc were specified in the constructor.
    -   Modified most code in RO that used Tk "after" to use Timer instead.

### 2.9.7 2012-06-04

-   RO.Wdg.StripChartWdg: reduce CPU usage by doing less work if not visible.

### 2.9.6 2012-06-01

-   RO.ScriptRunner: improve handling of callbacks in waitCmdVar and waitCmdVars.
-   RO.KeyVariable: improved callback cleanup in CmdVar.

### 2.9.5 2012-06-01

-   RO.Wdg.StripChartWdg: added a clear method (also added a clear method to lines).

### 2.9.4 2011-10-11

-   RO.Wdg.ScrolledWdg: set highlightthickness = selectborderwidth = 0 on contained Canvas to make alignment easier.
-   RO.Wdg.DropletApp: added doneMsg argument (with a useful default); documented recursionDepth.
-   RO.Wdg.DropletRunner: deprecated; use RO.Wdg.DropletApp instead.

### 2.9.3 2011-09-09

-   RO.OS.findFiles: misfeature fix: could return paths that start with "./".

### 2.9.2 2011-08-29

-   RO.Wdg.GrayImgaeDispWdg: bug fix: display was incorrect if data type was not 32-bit float.

### 2.9.1 2011-08-19

Warning: if you are using a Python older than 2.6 then you must install simplejson.

-   Fall back to importing simplejson if json not found, thus making it compatible with versions of Python older than 2.6.
-   RO.Wdg.OptionMenu changes:
    -   Modified getString to return the default value only if the current value is invalid. Formerly it would return the default if the current value was noneDisplay, which was undesirable if noneDisplay was a valid value.
    -   Modified asValue to return the default only if value == noneDisplay and noneDisplay is not a valid value (the latter condition is new).
    -   Added method isValid.

### 2.9.0 2011-08-16

Warning: this version requires Python 2.6 or later, due to use of the json module.

-   MathUtil.rThetaFromXY: API change and bug fix: it now returns theta=NaN if too near the pole; formerly it was documented to raise an exception if too near the pole, but that exception was not raised reliably, if at all.
-   Message dictionary change: renamed "type" to "msgType" to avoid conflict with the Python built in function. This introduces minor API changes to:
    -   RO.KeyDispatcher: KeyDispatcher methods dispatch, logMsgDict and makeMsgDict
    -   RO.KeyVariable: KeyVar.set and CmdVar.reply
    -   ParseMsg.parseHubMsg

-   RO.KeyDispatcher.KeyDispatcher API change: the log function now receives an extra keyword argument: cmdID.
-   RO.Wdg
    -   RO.Wdg.CtxMenu modified to restore focus to the widget on which the menu is raised. This give better visual feedback when using the menu to work with data, since the field containing the data is highlighted.
    -   RO.Wdg.DropletApp: added support for recursion. Added arguments: patterns, exclPatterns, dirPatterns, exclDirPatterns, recursionDepth and processDirs. Call update\_idletasks after processing each file so messages are more likely to be printed when they arrive.
    -   RO.Wdg.Entry changes:
        -   doneFunc is no longer called in response to methods such as set, but in response to user interaction.
        -   doneFunc is much less likely to be called multiple times for the same value. The test resets whenever the displayed value changes.
        -   Added a method inMethodCall which indicates whether callbacks are being called due to method calls (such as set) or user interaction.

    -   RO.Wdg.Gridder: the object returned by gridWdg now has \_\_getitem\_\_, \_\_iter\_\_ and \_\_len\_\_ methods for accessing the widgets.
    -   RO.Wdg.GrayImgaeDispWdg: improved efficiency by reusing an internal scaled array when possible.
    -   RO.Wdg.StateTracker: a new object used by Toplevel and ToplevelSet to save and restore widget state.
    -   RO.Wdg.StatusConfigGridder bug fix: getMaxNextCol was not reliable.
    -   RO.Wdg.Toplevel and ToplevelSet: added support for saving and restoring widget state.

-   RO.OS.findFiles: added arguments patterns, exclPatterns, dirPatterns, exclDirPatterns, recursionDepth and processDirs.

### 2.8.0 2011-03-29

-   Added RO.Wdg.DropletApp: a base class for applications that process files dropped on them.

### 2.7.2 2011-02-18

-   AddCallback: added callbacksEnabled method.
-   InputCont: added allCallbacksEnabled method.
-   KeyVariable: document that addROWdgSet can take fewer widgets than values.

### 2.7.1 2011-01-31

-   Bug fix: RO.Astro.Sph.angSideAng incorrectly returned unknownAng=False in a few instances when ang\_B was nearly zero.
-   Corrected a broken link in the documentation (found by Integrity).

### 2.7.0 2010-12-23

-   RO.Wdg.StripChartWdg
    -   Backward-incompatible change: addLine now returns an object on which you call addPoint
    -   Lines no longer need unique names (or names at all)
    -   Added removeLine method
    -   addPoint now ignores the data if y is None

### 2.6.2 2010-12-07

-   Bug fix: HTTPGet timeLim was mishandled.
-   Bug fix: fixed a minor memory leak in RO.Wdg.StripChartWdg. Unfortunately it has a much larger memory leak as well due to a bug in matplotlib 1.0.0 (reported as bug [3124990](https://sourceforge.net/tracker/?func=detail&atid=560720&aid=3124990&group_id=80706)).

### 2.6.1 2010-10-19

-   RO.Wdg.GrayImageWdg: the value at the cursor is now shown as floating point. This handles float images and NaNs better.

### 2.6.0 2010-10-01

-   Added RO.Alg.RandomWalk.
-   Added RO.Wdg.StripChartWdg. This requires matplotlib.

### 2.5.6 2010-08-04

-   RO.Astro.Sph.angSideAng: fixed two more bugs in special cases.

### 2.5.5 2010-08-03

-   Made the license more liberal (except for RO.Astro).
-   Bug fix: RO.Wdg.GrayImageDispWdg was broken because the 2.5.4 PyPI distribution was missing its bitmap files.
-   To avoid future such probelems I modified releaseNewVersion.py to verify that the bitmap files are present before uploading.

### 2.5.4 2010-07-30

-   RO.Astro.Sph.angSideAng:
    -   Changed output flag from zero\_bb to unknownAng. In some cases this is set when side\_bb = 180.
    -   Bug fix: in some cases side\_bb should have been 180 when ang\_A and ang\_C unknown.
    -   Improved the accuracy for some edge cases (all unit tests now pass).
    -   Greatly expanded the unit tests.

-   RO.MathUtils.wrapPos: bug fix: could return 360.0 in special cases.
-   RO.TkUtil: added Timer class
-   RO.KeyDispatcher
    -   Added resetAll argument to refreshAllVar method.
    -   Added readUnixTime field

-   RO.Wdg.DropletRunner: changed to a new-style class (as always intended) and modified the syntax to make compatible with older versions of Python.

### 2.5.3 2010-06-28

-   RO.Wdg.LogWdg: added addOutputList and isScrolledToEnd methods.
-   RO.Astro.Tm: fixed isoDateFromPySec.
-   Cleaned up a few minor issues found by pychecker.

### 2.5.2 2010-06-18

-   RO.Wdg.DropletRunner: bug fix: the droplet script was not being run with sys.executable (thus for a bundled application the droplet script had no access to the application's python and python libraries).
-   Added installation instructions for users of the eups package management system.

### 2.5.1 2010-06-18

-   RO.Wdg.DropletRunner: added title and initialText arguments to constructor.

### 2.5.0 2010-06-07

-   Added RO.Wdg.DropletRunner: runs a script as a "droplet" (an application onto which you drop files) with a log window.

### 2.4.1 2010-06-07

-   RO.Wdg.Entry: modified to not call doneFunc if \_enableCallbacks False.

### 2.4.0 2010-05-27

This version requires Python 2.5 or later (at least to use RO.AddCallback).

-   RO.AddCallback
    -   Added method \_disableCallbacksContext; to temporarily disabling callbacks use:
         `with self._disableCallbacksContext():`
    -   Added new boolean member variable \_enableCallbacks.
    -   Added a guard to prevent infinite recursion while running callbacks (using \_enableCallbacks).

-   RO.Alg.SetDict: modified to use sets.
-   RO.TkUtil.Geometry: fixed a bug whereby toTkStr might return extent information even when it shouldn't.
-   RO.Wdg.Checkbutton: added trackDefault argument to constructor. **Warning:** the default value is None, which tracks autoIsCurrent. Thus the behavior of some controls may change. I don't expect this to be a significant change, and it matches the behavior of RO.Wdg.Entry widgets.
-   RO.Wdg.IsCurrentMixin: corrected some doc strings for which methods the supporting object must support.

### 2.3.5 2010-05-05

-   RO.TkUtil: added the Geometry class, a representation of tk geometry strings. Geometry includes the ability to constrain geometry to the visible area of the user's displays.
-   RO.Wdg.Toplevel: modified to constrain windows to be fully visible on the user's displays even if the requested geometry is not.

### 2.3.4 2010-03-08

-   RO.Constants: added SevNameDict and NameSevDict.
-   RO.Wdg
    -   RO.Wdg.LogWdg: added message severity support.
    -   RO.Wdg.Gridder
        -   Changed the default for gridWdg to copy helpText and helpURL from the first data widget.
        -   Bug fix: gridWdg would fail if helpText or helpURL was True and the first data widget was missing the associated attribute.

### 2.3.3 2010-03-08

-   RO.Wdg.StatusBar bug fix: command replies were sometimes displayed with the wrong color.

### 2.3.2 2010-03-05

-   RO.ScriptRunner
    -   Added isPaused method.
    -   Changed isAborting to didFail for consistency with isDone and improved the documentation of both methods.

-   RO.Wdg
    -   RO.Wdg.*x*Entry
        -   Added autoSetDefault option.
        -   Modified to call doneFunc when the value is changed via set.

    -   RO.Wdg.LogWdg: added tabs option.
    -   RO.Wdg.StatusBar: fixed an error in tracking command severity.

### 2.3.1 2010-01-15

-   RO.Astro.Tm:
    -   Added iso[Date/DateTime/Time]FromPySec functions.
    -   Added getUTCMinusTAI and pySecFromTAI functions.
    -   Changed default UTC-TAI from -33 to -34 seconds.

-   Bug fix: setup.py was not installing the bitmaps needed by RO.Wdg.GrayImageDispWdg.

### 2.3.0 2009-10-23

-   RO.Wdg.Sound: modified to use pygame instead of snack to play sound files.

### 2.2.20 2009-09-10

-   RO.KeyDispatcher: bug fix: check self.\_refreshAllID before using it with after\_cancel.

### 2.2.19 2009-09-02

-   RO.Constants: added sevCritical.
-   RO.Wdg.WdgPrefs: added Critical Color.

### 2.2.18 2009-08-25

-   RO.Wdg.LogWdg: added doAutoScroll option.

### 2.2.17 2009-08-25

-   RO.Wdg.Bindings: Control-Button-1/2/3 events on X11 are no longer blocked. These events were blocked for the sake of Macs with 1-button mice running X11 Tcl/Tk, but that is now too obscure a case to justify blocking control-click events.

### 2.2.16 2009-08-04

-   Added radialLine to RO.CanvasUtil, primarily for use as an annotation on RO.Wdg.GrayImageDispWdg.
-   Improved installation documentation and fixed a broken link to a ReadMe file on my web page (reported by Marshall Perrin).

### 2.2.15 2009-07-20

-   Added RO.CnvUtil.posFromPVT.
-   RO.KeyVariable: Removed support for refreshTimeLim (it is now a constant in the KeyDispatcher).
-   RO.KeyDispatcher:
    -   Renamed method add to addKeyVar and remove to removeKeyVar.
    -   Overhauled keyVar refresh to be more efficient.
    -   Reverted logging behavior: do not log if logFunc=None. Renamed and simplified the convenience logging function that makes logging easy.

### 2.2.14 2009-07-18

-   tools/tcpclient.py: removed an inline conditional statement to restore compatibility with Python 2.4.
-   RO.Comm.HubConnection: eliminated deprecation warning in Python 2.6 by using hashlib if present.

### 2.2.13 2009-07-06

-   RO.KeyVariable: bug fix: an error message had values reversed.
-   RO.Wdg.StatusBar: setMsg function: duration can now be float (it is truncated to int); improved the documentationt.
-   RO.KeyDispatcher: modified to log to stderr if no log function supplied.

### 2.2.12 2009-06-02

-   Added command-line options to tools/fitsinfo.py to allow showing only the image header or image statistics.
-   RO.KeyVariable.TypeDict: added "d" (debug) and removed obsolete "s" (status).
-   Moved tcpclient.py from python/RO/Comm to tools/

### 2.2.11 2009-05-04

-   RO.CnvUtil: allow "?" to indicate unknown value for bool, int and float in the appropriate converters.
-   RO.KeyDispatcher: fixed a bug that made KeyVar refresh inefficient.
-   RO.Wdg.Toplevel bug fix: tl\_CloseDisabled toplevels could be iconified on MacOS X with cmd-W. As part of the fix, application Quit and toplevel Close are now handled by virtual events \<\<Quit\>\> and \<\<Close\>\>.

### 2.2.10 2009-01-26

-   RO.DS9
    -   Restored full operation under MacOS X. It turns out the error "The process has forked and you cannot use this CoreFoundation functionality safely. You MUST exec()." was caused by running a Tiger (MacOS X 10.4) version of DS9 under Leopard (MacOS X 10.5).

-   RO.Comm.TkSerial
    -   Bug fix: isOpen returned the wrong value.
    -   Bug fix: if a read or write error occurred, the exception would be thrown repeatedly. Now the connection is automatically closed on error.

### 2.2.9 2009-01-06

-   Added RO.Astro.ImageWindow, a class to convert between binned and unbinned windows (subimages).
-   Added RO.StringUtil.unquoteStr.
-   RO.DS9
    -   Added closeFDs argument to DS9Win at the suggestion of Paulo Henrique Silva.
    -   Bug fix: MacOS X 10.5 reported "The process has forked and you cannot use this CoreFoundation functionality safely. You MUST exec()." while opening ds9; ufortunately the fix eliminates the ability to set the title of the window on MacOS X.

### 2.2.8 2008-07-17

-   Added a tools directory with some useful scripts.
-   RO.Comm: added TkSerial, an interface to a serial port using the tcl event loop.
-   RO.CnvUtil:
    -   Added BoolOrNoneFromStr class.
    -   Added "on" and "off" as valid boolean values.

-   RO.ScriptRunner:
    -   Improved output in debug mode
    -   Bug fix: unicode data in a ScriptError caused a traceback.

-   RO.StringUtil:
    -   Added strFromException, a unicode-safe replacement for str(exception).
    -   Made prettyDict unicode-safe by using repr.

-   RO.Wdg:
    -   RO.Wdg.Entry: added getDefaultWidth method and added adjustWidth argument to setRange method.
    -   RO.Wdg.GrayImageWdg:
        -   Masked pixels may be exluded from the intensity stretch calculation by setting doStretch false in the MaskInfo for the desired mask bits.
        -   Added 98, 97, 96 and 95% options to range menu.

    -   RO.Wdg.Log: added addMsg method (like addOutput but appends a trailing \\n).
    -   RO.Wdg.ScriptWdg: add \_\_file\_\_ local variable to each loaded script file, making it easier to locate help files.

### 2.2.7 2008-02-14

-   RO.Alg.MatchList: bug fix: was not compatible with unicode.
-   RO.Comm
    -   RO.Comm.TCPConnection: added mayConnect method.

### 2.2.6 2008-01-30

-   RO.Comm
    -   RO.Comm.TCPConnection: tweaked connect to raise RuntimeError if connecting or connected (instead of just connected).

-   RO.StringUtil: removed unused variable (found by pychecker).
-   RO.Wdg
    -   RO.Wdg.GrayImageDispWdg: added defRange argument to \_\_init\_\_.

-   The first version served on [PyPI](http://pypi.python.org/pypi?:action=display&name=RO).

### 2.2.5 2008-01-23

-   Modified setup.py to use [setuptools](http://pypi.python.org/pypi/setuptools) for installation.
-   RO.Comm
    -   RO.Comm.TkSocket: added pre-test for socket existing to write and writeLine.
    -   RO.Comm.TCPConnection:
        -   Removed getProgress method. It was clumsy and better handled by the user.
        -   Modified connect to raise RuntimeError if host and self.host are both blank or if already connected.

-   RO.Wdg
    -   RO.Wdg.GrayImageDispWdg:
        -   Added method evtOnCanvas.
        -   Changed default scaling from ASinh 0.01 to Linear by request of Russet McMillan.

    -   RO.Wdg.LogWdg.py: fixed incompatibility with Tcl/Tk 8.5 (the Text index method returns an object instead of a string). Note: this and other incompatibilities in Tkinter.Text will eventually be fixed in Tkinter.
    -   RO.Wdg.StatusConfigGridder: added numStatusCols argument. This makes it easier to start all configuration widgets in the same column.

### 2.2.4 2007-11-16

-   Corrected download links in documentation (they pointed to an obsolete ftp repository).

### 2.2.3 2007-10-16

-   RO.DS9: updated to find DS9 5.0 on the Mac (SAO changed things yet again).
-   RO.Wdg
    -   RO.Wdg.GrayImageDispWdg: the test code now demonstrates the use of masks.

### 2.2.2 2007-09-28

Fixed some bugs found by pychecker.

-   RO.Astro.Cnv
    -   RO.Astro.Cnv.ObsFromTopo and RO.Astro.Cnv.TopoFromObs mis-called numpy.asarray (which does not accept the copy argument). Fixed by switching to numpy.array to force a copy.

-   RO.Wdg
    -   RO.Wdg.Gridder: gridWdg ignored the helpText and helpURL arguments.
    -   RO.Wdg.LogWdg.py: fixed the setEnable method.

### 2.2.1 2007-09-10

-   RO.Wdg.OptionMenu:
    -   Modified to not check the initial value of var (if supplied) even if its value is not in the list of items. This improves backwards compatibility.
    -   Added checkCurrent argument to setItems method.
    -   Bug fix: defValue not shown as initial value when it should have been.

-   RO.Prefs:
    -   Font preference improvements:
        -   Reduced the minimum font size to 6 from 9.
        -   The default font on Windows is now MS Sans Serif instead of Helvetica.
        -   The initial value of the font family and size are now shown even if not an option in the menu.
        -   The options menu button is now labelled Options instead of being blank.

### 2.2 2007-09-07

-   RO.CnvUtil:
    -   Added FloatOrNoneFromStr and IntOrNoneFromStr classes. Unlike asFloatOrNone and asIntOrNone the user may specify one or more bad values (and only string values are accepted for input).

-   RO.InputCont: added allDefault method.
-   RO.KeyVariable.PVTVar: added hasVel method.
-   RO.PVT.PVT: added hasVel method.
-   RO.Wdg
    -   RO.Wdg.OptionMenu:
        -   One can now set the value to None; formerly set(None) was ignored.
        -   Added noneDisplay argument: the string to display when the value is None.
        -   restoreDefault now updates the display even if defValue = None.
        -   Added showDefault argument to setDefault.
        -   If ignoreCase is True, setItems retains the current value if it matches a new item case-blind (formerly an exact match was always required).

    -   RO.Wdg.OptionPanelControl: added setBool method.
    -   RO.Wdg.ScriptRunner: Overhauled helpURL handling. Now it looks in the script for a variable named HelpURL.
    -   RO.Wdg.Toplevel: added a workaround for Tk [bug 1771916: Bad geometry reported...](http://sourceforge.net/tracker/index.php?func=detail&aid=1771916&group_id=12997&atid=112997); geometry is not saved and a warning is printed if y \< 0.

### 2.1 2007-06-07

-   Modified to use numpy instead of numarray and Numeric.
-   RO.Astro: added runTests.py to run all unit tests in this package. Note that two tests fail for RO.Astro.Sph.AngSideAng; this is a known issue.
-   RO.StringUtil.dmsStrFromSec bug fix: gave wrong answer if nFields != 3.
-   RO.Wdg:
    -   RO.Wdg.LogWdg: added setEnable method.

### 2.0 2007-01-22

-   The first release with an installer and a version number.
-   All source code changed to using 4 spaces instead of tabs for indentation.
-   RO.DS9:
    -   Help and example code improved.
    -   Bug fix: on unix there was an error in reporting ds9 not found.

-   RO.OS.getResourceDir: modified to support pyinstaller-packaged applications (but if using pyinstaller you must manually expand sys.executable at startup for this to work reliably).
-   RO.Wdg:
    -   RO.Wdg.AutoIsCurrentMixin: modified to use isDefault method instead of getString and getDefault.
    -   RO.Wdg.Checkbutton: added isDefault method.
    -   RO.Wdg.Entry:
        -   Added label argument.
        -   For numeric entries: improved isDefault argument to compare numeric values after comparing string values. This allows 1 to match 1.0, etc.
        -   Bug fix: supplying a doneFunc disabled some range checking.

    -   RO.Wdg.GrayImageDispWdg: improved compatibility with PIL 1.1.6 and later (by specifying more arguments to frombuffer).

### 2007-01-02

-   RO.Constants: added sevDebug.
-   RO.DS9: modified to work with Mac ds9 4.0b10 (SAO keeps unpredictably renaming the Mac application).
-   RO.KeyVariable: Added keyVars argument to CmdVar. This allows retrieving data returned as the result of a command.
-   RO.KeyDispatcher: overhauled logging.
-   RO.OS: added delDir function.
-   RO.ScriptRunner:
    -   Added waitUser and resumeUser methods.
    -   Added checkFail argument to waitCmd and waitCmdVars methods.
    -   waitCmd now returns the cmdVar in sr.value.
    -   Added keyVars argument to startCmd and waitCmd.

-   RO.TkUtil: added addColors function.
-   RO.Wdg:
    -   Deleted RO.Wdg.CmdReplyWdg. I guessed it was not used, and LogWdg changed enough to make updating a headache. If you need it, let me know.
    -   Added RO.Wdg.ResizableRect.
    -   RO.Wdg.Entry: added doneFunc argument: a function to call when the user types \<return\> or the widget loses focus.
    -   RO.Wdg.GrayImageDispWdg: added imPosFromArrIJ method.
    -   RO.Wdg.OptionMenu: added index method to work around a tk misfeature
    -   RO.Wdg.LogWdg: totally overhauled. Now includes just the log area (users are expected to add the extra controls needed). Includes powerful new methods for filtering and searching.
    -   RO.Wdg.ScriptWdg: Bug fix: if a script paused itself, the pause button still showed "Pause" instead of "Resume".
    -   RO.Wdg.Gridder and StatusConfigGridder: Added support adding help text and URL to created widgets.
    -   RO.Wdg.Text: added search method with elide argument because Tkinter's Text.search doesn't yet support elide.

-   Minor fixes to the version history.

### 2006-07-11

-   RO.Comm.TkSocket
    -   Modified BaseServer to be compatible with Python 2.3.
    -   Added BaseServer to \_\_all\_\_.
    -   Bug fix: invalid import in test code.

-   RO.DS9: modified to handle version 4.0b9 of ds9 (which has a new name on the Mac: "SAOImage DS9.app").
-   RO.Wdg
    -   FileWdg: bug fix: initial defPath was not shown.
    -   GrayImageDispWdg: added imPosFromArrIJ method.

### 2006-06-07

-   RO.KeyDispatcher: bug fix: if a message could not be parsed, logging the error failed (due to logging in a way that involved parsing the message again).
-   RO.ScriptRunner:
    -   Bug fixes to debug mode:
        -   waitCmd miscomputed iterID.
        -   startCmd dispatched commands.

    -   Improved error handling in \_continue.

-   RO.Prefs
    -   Bug fix: DirectoryPrefVar, FilePrefVar and SoundPrefVar's edit widgets would not restore the initial or current value when requested. To fix this, I now instantiate the editors in the PrefEditor module instead of PrefVar. Thus these vars no longer have useful getEditWdg methods.

-   RO.Wdg
    -   DirWdg and FileWdg:
        -   If the current path is missing when the user selects a new one, the dialog box starts at the parent dir (if found).
        -   Bug fix: if the current path was missing, the choose dialog would not come up.
        -   Bug fix: FileWdg does not set defPath or path if defPath is a directory (but it still uses the value as the initial directory of the choose dialog).

    -   GrayImageDispWdg MaskInfo changes:
        -   Added setColor method.
        -   Bug fix: mask colors were slightly mishandled (the rgb values ranged to 64k instead of 256).

    -   Entry:
        -   Added trackDefault argument.
        -   Added getNumOrNone to numeric entry types.
        -   Improved doc strings for checkValue and \_basicCheck methods.

    -   LogWdg:
        -   Added helpText argument.
        -   Made the control frame explicit so it can be easily hidden.

    -   OptionMenu:
        -   Added trackDefault argument.
        -   Bug fix: added isCurrent argument to set.
        -   Bug fix: setItems properly preserves non-item-specific help.

    -   RadiobuttonSet
        -   Added trackDefault argument.
        -   Bug fix: added isCurrent argument to set and setDefault.

    -   ScriptRunner: modified to report reload failures.
    -   Toplevel:
        -   Added a patch (an extra call to update\_idletasks) for a bug in Tcl/Tk 8.4.13 that caused certain toplevels to be displayed in the wrong place.
        -   Removed a patch in makeVisible for an older tk bug; the patch was now causing iconified toplevels to be left iconified.
        -   Always pack the widget with expand="yes", fill="both"; this fixes a situation where the user first creates a Toplevel and later decides to make it resizable.
        -   Commented out code in makeVisible that supposedly avoids toplevels shifting; I can't see how it can help.

### 2006-04-17

-   RO.Wdg
    -   GrayImageDispWdg:
        -   Added optional display of bitmasks.
        -   Modified to make linear the initial function.
        -   Bug fix: initial scaling function was not set.

    -   RadioButtonSet:
        -   Treat a default value of None as "no default", rather than "the first value".
        -   Bug fix: defIfBlank argument was ignored.

### 2006-04-05

-   RO.ScriptRunner: scripts may run subscripts.
-   RO.Wdg
    -   CmdReplyWdg: bug fix: did not auto-scroll after a command was entered (broken in 2006-03-10).
    -   HTTPGetWdg: bug fix: status display failed if state was aborting or aborted.
    -   RadioButtonSet:
        -   Added "side" argument to pack the widgets as specified.
        -   Added isCurrent and autoIsCurrent support.
        -   Modified getWdgSet to return a copy.

    -   Added isDefault method to the following: xxxEntry, OptionMenu, RadioButtonSet. Warning: it has not yet been tested; also, it may not behave as desired if the default is None.

### 2006-03-10

-   RO.KeyVariable.KeyVar now emulates a normal sequence for read-only access to its values, thus "a in var", var[i], var[i:j] and len(var).
-   RO.OS
    -   getHomeDir fixed to work on Windows (formerly returned None).
    -   getWinDirs: removed py2exe compatibility because it's more appropriate for the py2exe setup.py script (see the module's doc string for the necessary code).

-   RO.ScriptRunner: added support for defining a script as a class (scriptClass argument), making it much easier to pass data between the init, run and end functions.
-   RO.SQLUtil.NullDBCursor:
    -   Added lastrowid.
    -   execute's output truncates long values.

-   RO.Wdg
    -   Added CmdWdg (split off from RO.Wdg.CmdReplyWdg).
    -   CmdReplyWdg: modified to use new RO.Wdg.CmdWdg.
    -   Added DirWdg and FileWdg: buttons that display a path; press to change it.
    -   DMSEntry.setIsHours bug fix: switching from hours to degrees could raise an exception (if it decided the precision of a value in hours was 0, it would try to use -1 for the converted value).
    -   ProgressBar: added setUnknown to display an unknown remaining time.
    -   ScriptWdg: looks for "ScriptClass" and uses that in preference to "init", "run" and "end" functions.

### 2006-01-20

-   RO.SeqUtil
    -   Added asCollection
    -   Redefined Collection to mean any non-string-like iterable (adopting a test suggested by Michael Spencer on comp.lang.python).
    -   Collection and Sequence are now defined in the module's doc string.

-   RO.SQLUtil
    -   formatFieldEqVal: added sepStr argument.
    -   removed getLastInsertedIDMySQL since it didn't work as advertised; use the cursor's lastrowid instead; for more information, see the MySQLDb manual entry for insert\_id(). (Note: despite the 1.2.0 manual, insert\_id() is an attribute of the connection, but is used to create the cursor's lastrowid.).

### 2006-01-09

-   RO.StringUtil: Fixed a bug in dmsStrFromDeg: dmsStrFromDeg(-50.650002) = "-50:38:60.0" and a related bug in dmsStrFroMSec. Thanks to John Lucey for the bug report.
-   RO.PgSQLUtil renamed to RO.SQLUtil...
    -   because all but one function should work with any DBAPI-2.0 database.
    -   Renamed getLastInsertedID to getLastInsertedIDPgSQL.
    -   Added getLastInsertedIDMySQL.
    -   Added NullDBConn and NullDBCursor, for testing database code without actually modifying databases.
    -   Modified insertRow so fieldsToAdd defaults to all fields.
    -   Modified rowExists so fieldsToCheck defaults to all fields.

### 2005-11-04

-   RO.DS9.DS9Win.showArray: displaying an array in non-native byte order no longer requires copying the input array. Based on code by Tim Axelrod and Rick White.

### 2005-10-31\_2

-   RO.DS9.DS9Win.showArray: bug fix: the input array would be altered if it was not in native byte order. Fixed by copying the input array if it is not in native byte order; this is a temporary fix until I figure out how to use the array unaltered. Thanks to Tim Axelrod for the bug report.

### 2005-10-31

-   RO.DS9.DS9Win.showArray bug fix: mis-handled arrays that were not in native byte order. Thanks to Tim Axelrod for the bug report.

### 2005-10-13

-   RO.DS9:
    -   MacOS X:
        -   Fully supports MacOS X version of ds9 (so long ds9.app is in one of the standard application directories). Thus darwin xpa is no longer necessary (though still usable).
        -   Add /usr/local/bin to env var PATH and set env var DISPLAY, if necessary. This makes bundled apps more likely to work because they do not see the user's Terminal login modifications to env variables.

    -   Windows: supports xpa installed in its default location (or installed in the same directory as ds9, which is still preferable for command-line use).

### 2005-10-07

-   RO.DS9: fixed Windows bugs introduced in 2005-09-30 release.
-   RO.OS
    -   Fixed Windows bugs introduced in 2005-09-30 release.
    -   Added inclNone argument to all getXXXDirs functions; inclNone defaults to False, giving the pre-2005-09-30 behavior.
    -   getWinDirs modified to be compatible with py2exe (one needs trickery to import win32com.shell).
    -   splitPath bug fix: on Windows the first element (disk letter) ended with a backslash.

### 2005-09-30

-   RO.DS9:
    -   Corrected the instructions for installing xpa and ds9 on Mac and Windows.
    -   It explicitly looks for xpaget and ds9 (on all platforms) and complains if it cannot find them. It then checks again each time you try to do anything (so you can install the components and keep working without reloading the module). Warning: this requires a "which" function on unix.
    -   MacOS X and Windows: it now looks in the standard locations for applications (rather than typical locations on English systems).
    -   MacOS X: DS9Win launches X11 if necessary.
    -   Bug fix: used the warnings module without importing it.

-   RO.Prefs
    -   PrefSet: Changed oldPrefNames argument to oldPrefInfo: one can now map old pref names to new pref names.
    -   PrefsWdg:
        -   Added getCategories and showCategory methods.
        -   Renamed internal method selectCategory to \_showSelectedCategory.

-   RO.SeqUtil: added get.
-   RO.Wdg
    -   Bindings: on Mac, added support for Command-Q = quit and Command-W = withdraw toplevel.
    -   Checkbutton: If var supplied and defValue left None then the default value is the current value of var.
    -   GrayImageViewerWdg: propagates left-mouse-button events (but still does not propagate middle or right mouse-button events, to avoid unwanted copy or paste), making it easier to write code that uses the "normal" mode.

### 2005-09-07

-   RO.Comm.TkSocket
    -   Bug fix: an exception could occur in the read callback if the remote host closed the connection. Formerly the internal socket read callback tried to check the connection before calling the user's read callback, but that test could fail due to timing issues. Now the user's read callback is always called and read and readLine always return "" (or default for readLine) if the socket is closed—they never raise an exception.
    -   Bug fix: leaked tcl functions.

-   RO.TkUtil.TclFunc: Removed useless \_\_del\_\_ from TclFunc and updated the documentation.
-   RO.Wdg.StatusBar: bug fix: if text=... was present in a command reply, the info was shown in parenthesis.

### 2005-08-12

-   RO.Alg.OrderedDict:
    -   The following changes were kindly suggested by "bearophile":
        -   Redefined copy to make subclassing easier and safer (in fact ReverseOrderedDict.copy was broken).
        -   **Incompatible Change**: Renamed checkIntegrity to \_checkIntegrity.
        -   Eliminated use of obsolete string module

    -   Modified \_\_repr\_\_ to return a string that can recreate the OrderedDict. Note: this has an unfortunate side effect for ReverseOrderedDict: the items are shown in reversed order.
    -   Added \_\_str\_\_ to return the traditional dict representation formerly returned by \_\_repr\_\_.

-   RO.Alg.ReverseOrderedDict: bug fix: copy returned an OrderedDict instead of a ReverseOrderedDict.
-   RO.Comm.
    -   TCPConnection: added isDone and getProgress methods.
    -   TkSocket
        -   **Incompatible Change**: Changed state constants from module constants to class constants.
        -   Added class TkServerSocket.
        -   Bug fix: TkSocket was not sending binary data through correctly.

-   RO.Prefs.PrefVar: changed help text for file, directory and sound prefs to the standard help text.
-   RO.Wdg.
    -   Bindings: fixed bug in makeReadOnly: was not trapping button-release-2 (which pastes the selection, at least on unix).
    -   ProgressBar: modified to handle min=max gracefully: it will display an empty bar instead of raising an exception.
    -   StatusBar: bug fix: clear() reset the temporary message ID, which could cause clearTempMsg() to clear the wrong message.

-   Refactored the package to separate code and resource files. This will make it easier to package projects that use RO.

### 2005-07-11

-   RO.AddCallback: added method \_removeAllCallbacks.
-   RO.Alg.OrderedDict:
    -   Added index and insert methods
    -   Bug fix: the pop method needed to be overridden.

-   RO.CanvasUtil: improved Spiral:
    -   Keep track of geom ID for more reliable clear during redraw.
    -   Use list comprehension to speed computation of coords.

-   Plugged various potential memory leaks by making the following perform better cleanup when done (including removing references to callback functions):
    -   RO.Comm.TkSocket
    -   RO.KeyVariable.CmdVar
    -   RO.Comm.FTPGet
    -   RO.Comm.FTPLogWdg

-   RO.Comm.FTPGet is deprecated (use the new RO.Comm.HTTPGet, instead, if possible). I do not intend to update it any further. However, it did receive some changes for this release:
    -   Eliminated callback function support. Callbacks were not Tk safe and that was a nasty trap. Note that RO.Wdg.FTPLogWdg.getFile supports Tk-safe callbacks.
    -   Fixed a bug that could cause an existing file to get deleted even if the overwrite argument was false.

-   RO.Comm.HTTPGet added. This downloads files using the http protocol. It uses tcl libraries to perform the download and thus is nicely integrated into the tk event loop (unlike RO.Comm.FTPGet, which is now deprecated).
-   RO.KeyDispatcher:
    -   Modified logMsg to take severity instead of typeChar.
    -   Bug fix: \_isConnected was not getting set properly if connection was omitted. It may also have not been set correctly for real connections in special cases.
    -   Fixed a typo in the test code. It works again.

-   RO.KeyVariable:
    -   Added getSeverity method to KeyVar and CmdVar.
    -   Added getCmdrCmdID method to KeyVar.
    -   Changed CmdVar.replies to CmdVar.lastReply. This was to avoid wasting memory; some commands may run for a very long time.
    -   Modified TypeDict; 2nd element of each value is now severity (one of RO.Constants.sev...) instead of a logger category.

-   RO.OS:
    -   Added getDocsDir
    -   Changed getAppSuppDirs to return None for unknown dirs (so you can tell which is user-specific and which one is shared).
    -   Removed Mac-specific doCreate argument for getAppSuppDirs and getPrefsDir.

-   RO.Prefs: improved the file chooser for FilePrefVar so that it does a better job of starting out in the right place.
-   RO.Prefs.WdgPrefs: bug fix: was using == for assignment in one location (caught by pychecker).
-   RO.ScriptRunner: changed default cmdStatusBar from statusBar to no bar.
-   RO.SeqUtil: added isCollection, isString and asSet.
-   RO.Wdg.HTTPLogWdg added. This shows the state of RO.Comm.HTTPGet downloads and includes method getFile to initiate such a transfer.
-   RO.Wdg.TkUtil moved to RO.TkUtil to reduce the chance of import loops.
-   RO.Wdg.Bindings: Modified stdBindings to use TkUtil. Also, may have improved stdBindings's disabling of \<\<Paste-Selection\>\> on Windows.
-   RO.Wdg.Button: added severity support. However, it does not work on MacOS X Aqua.
-   RO.Wdg.Checkbutton: Modified default padding when indicatoron is false so it looks better under Tk 8.4.9, especially on Aqua (something changed in Tk at some point such that the old aqua margins were too small).
-   RO.Wdg.Entry:
    -   Modify to check value on getString, getStringOrDefault, getNum and getNumOrDefault. Thus these methods will now raise an exception if the value is invalid (e.g. out of range for numeric values).
    -   DMSEntry, IntEntry and FloatEntry (changes made in parent class \_NumEntry):
        -   Modified getNum to return if empty (thus it acts like getString instead of getStringOrDefault) or raise an exception if the current value is invalid.
        -   Added getNumOrDefault: return the default if the field is empty (like getStringOrDefault and the old getNum), or raise an exception if the current value is invalid (like the new getNum but not like the old getNum).
        -   Mis-handled None as a limit. It might test minLim \< maxLim even if one or both were None and it would always reject "-" if minLim was None.
        -   Modified to complain if "-" isn't the first character if maxVal \< 0.

    -   Modified \_checkVar (which checks each character as it is entered) to clear the field if both the new value and the previous value are invalid (based on checking partial value). This should only happen if the validity criterion (such as range for numeric entry fields) is changed while the user is entering data.
    -   Modified try/except blocks to not swallow system exit and keyboard interrupt.

-   RO.Wdg.FTPLogWdg is deprecated (use the new RO.Wdg.HTTPLogWdg, instead, if possible). I do not intend to update it any further. However, it did receive some changes for this release:
    -   Bug fix: was not trimming excess log entries correctly.
    -   Modified to auto-scroll only when last entry selected (or no entry selected) rather than basing it on scroll position.

-   RO.Wdg.GrayImageDispWdg:
    -   Added helpURL argument.
    -   Added showMsg method.
    -   Increased maximum zoom to 10x (and you can make it larger if you like, though you'll have to edit the file).
    -   Improved use of memory while zooming.
    -   Added memory exception handling.
    -   Changed level mode to work on first click.
    -   Improved mode handling with no image. The mode icon is now illuminated and the zoom frame appears but nothing else happens.
    -   Bug fix: could not display images that were all the same intensity.
    -   Bug fix: level mode set incorrect levels if there was a border around the canvas.

-   RO.Wdg.HTTPGetWdg added. This includes a getFile method to initiate downloading files to disk via http, and displays the status of such downloads.
-   RO.Wdg.InputCont: Bug fix: was referencing TclError, not Tkinter.TclError (caught by pychecker).
-   RO.Wdg.OptionPanelControl: modified to use RO.Wdg.Checkbutton's default padding (which is now sensible for unix and Aqua).
-   RO.Wdg.ScriptWdg: documented change of default cmdStatusBar from statusBar to no bar. .
-   RO.Wdg.StatusBar:
    -   Added cmdSummary argument to doCmd.
    -   Modified to use severity built into RO.Wdg.EntryWdg (prefs no longer need color prefs and the code is simpler).
    -   Modified command output to ignore info messages unless they contain a "Text" keyword.

-   RO.Wdg.StatusConfigGridder: bug fix: gridWdg mis-set nextCol if cfgWdg False or None. Also improved error message for units and cfgUnits being the same widget.
-   RO.Wdg.TkUtil: added getButtonNumbers to work around a tk misfeature: buttons are numbered 1, 3, 2 on MacOS X Aqua and 1, 2, 3 on Unix/X11 and Windows.
-   Cleaned up indentation oddities in many files.
-   Changed old-style classes to new-style classes (inherit from object) as follows: RO.AddCallback:BaseMixin; RO.Alg.IDGen, MatchList and MultiListIter; RO.CanvasUtil.Spiral; RO.CnvUtil.StrCnv and StrCnvNoCase; RO.Comm.TCPConnect.TCPConnect; RO.Comm.TkSocket.TkSocket and NullSocket; RO.KeyDispatcher.KeyDispatcher, NullLogger and StdErrLogger; RO.KeyVariable.CmdVar and KeyVarFactory; RO.PVT; RO.PgSQLUtil.FieldDescr; RO.Prefs.PrefEditor; RO.Prefs.PrefVar.PrefVar, PrefSet and ColorUpdate; RO.Wdg.CtxMenu; RO.Wdg.GrayImageDispWdg.Annotation; RO.Wdg.Gridder; RO.InputCont.BasicFmt, BasicContListFmt and VMSQualFmt; RO.Wdg.IsCurrentMixin and AutoIsCurrentMixin; RO.Wdg.SeverityMixin; RO.Wdg.Sound.BellPlay, SoundPlay and NoPlay; RO.Wdg.Toplevel.ToplevelSet; RO.Wdg.WdgPrefs.WdgPrefs.
-   Fixed nonfunctional assert statements (assert (cond) -\> assert cond) in:
    -   RO.Alg.OrderedDict test code
    -   RO.PgSQLUtil.insertRow
    -   RO.SeqUtil test code
    -   RO.StringUtil.splitDMSStr

### 2005-05-24

-   RO.CnvUtil: added StrCnvNoCase.
-   RO.Comm.FTPGet: modified to not check for "file exists" until download starts; the old behavior made error checking too messy.
-   RO.DS9: added doRaise argument to xpaget, xpaset and DS9Win; the default is False so the default behavior has changed.
-   RO.InputCont.BasicFmt: removed the obsolete omitHidden argument that was being ignored. Use blankIfDisabled, instead, or write your own format function.
-   RO.Wdg.Checkbutton: bug fix: setBool ignored isCurrent and severity.
-   Ro.Wdg.Entry: improved the default appearance and behavior of read-only widgets. The insertion cursor is now hidden and there is no longer any special highlighting to indicate that the widget has focus.

### 2005-04-26

-   RO.Alg: added ReverseOrderedDict.
-   RO.Wdg.FTPLogWdg: added support for callbacks to getFile.
-   RO.Wdg.GrayImageDispWdg (still in progress but now quite usable). Major improvements! Too extensive to list here; see the doc string.
-   RO.Wdg.RadiobuttonSet: added support for bitmaps.
-   Added directory RO.Wdg.Resources to contain bitmaps used by RO.Wdg.GrayImageDispWdg. Since these are not python files you may find you have to do some extra steps to package executables that use the RO package.
-   RO.procFiles:
    -   Continue on error; report traceback unless RuntimeError.
    -   Removed use of (deprecated) xreadlines in docs.
    -   bug fix: was setting outPath to "" instead of outDir if outFile="".

-   RO.Astro.Cnv.CoordConv: bug fix: conversions requiring a App Topo\<-\>Observed step were broken (thanks to Emmanouil Angelakis for the report).
-   RO.KeyVariable: bug fix: in an error occurred early in instantiation, formatting the exception message failed because there was no self.actor.

### 2005-01-28

-   RO.Wdg: added isCurrent and severity support, as implemented in RO.Wdg.Label, to a number of additional widgets.
    -   Added RO.Wdg.IsCurrentMixin, a set of mixin classes that allow widgets to have an isCurrent flag and display a suitable background color when not current. AutoIsCurrentMixin also allows input widgets to automatically display not-current when their value is not the default value (indicating that the user has changed something).
    -   Added RO.Wdg.SeverityMixin, a set of mixin classes that allow widgets to have a state (one of RO.Constants.sevNormal, sevWarning or sevError) and display a suitable foreground color.
    -   Enhanced the following classes to use these new mixin classes, including autoIsCurrent support where it makes sense (all but Label):
        -   RO.Wdg.Checkbutton
        -   RO.Wdg.Entry
        -   RO.Wdg.Label (no new functionality, but see incompatible changes below)
        -   RO.Wdg.OptionMenu

    -   This change produced the following incompatible changes:
        -   RO.Constants.st\_Normal, st\_Warning and st\_Error renamed to sevNormal, sevWarning and sevError.
        -   RO.Wdg.Label.set() now uses the argument "severity" instead of "state", and setState() was renamed to setSeverity().
        -   RO.Wdg.StatusBar.setMsg() now uses the argument "severity" instead of "level".

-   RO.Wdg.ModalDialogBase major overhaul:
    -   Combined the apply and validate methods into setResult.
    -   The buttons method now receives the button's master as an argument. Buttons now have their own frame so you can pack or grid them as you prefer.
    -   The buttons method is now called before the body method. Also, the default buttons (OK and Cancel) are now RO.Wdg.Buttons. These changes allow one to add help text to the default buttons in the body method (by setting their helpText attribute).
    -   Modified to restore original focus and to generally work more like the example in Welch's Practical Programming in Tcl and Tk.

-   RO.ScriptRunner: added a basic debug mode which prints messages as the script runs and prevents commands from going out over the network.
-   RO.Wdg.WdgPrefs: added two new prefs to prefDict: "Active Background Color" and "Bad Active Background". These are automatically computed from "Background Color" and "Bad Background"; they should not be set by users.
-   RO.Astro.Cnv.coordConv and RO.Astro.Sph.coordConv bug fix: mis-computing proper motion.
-   RO.Wdg.GrayImageViewer bug fix; was sorting the input data.

### 2004-12-13

-   RO.DS9 bug fix: the 2004-12-01 version was missing the code that waited for DS9 to launch.
-   RO.Wdg.GrayImageDispWdg enhanced, but still very preliminary.
-   RO.InputCont overhauled:
    -   Made ContList a subclass of WdgCont to clean up the code.
    -   WdgCont modified to be like ContList in the following ways:
        -   restoreDefault and setValueDict now make just one callback,instead of one callback per input container.
        -   Added removeCallback.

    -   Renamed doEnable to setEnable to match RO.Wdg widgets.
    -   Eliminated formatNow argument (it was not being used and was broken).

-   RO.Wdg.InputContFrame: added removeCallback; added callNow argument to addCallback.
-   RO.Wdg.OptionButton: renamed doEnable to setEnable to match RO.Wdg widgets.
-   RO.Wdg.RadioButtonSet: renamed doEnable to setEnable to match RO.Wdg widgets.

### 2004-12-01

-   RO.DS9
    -   Bug fix in xpaset: if data does not end in \\n, an \\n is appended. This fixes an incompatily with older versions. Warning: dataFunc must supply a final \\n if needed; fortunately when sending array data (the main use for which dataFunc was envisioned), a final \\n does not appear to be needed.
    -   Modified to use the subprocess module (one is supplied from RO.Future if your python is too old to have one).

-   RO.Future.subprocess added, so one can safely use subprocess with older versions of Python.
-   RO.Wdg.GrayImageDispWdg added: a preliminary implementation of a grayscale image viewer. It is not yet imported into RO.Wdg (that will be done once it is released).
-   RO.Wdg.OptionMenu: rearranged a few methods into alphabetical order.
-   RO.Wdg.ScrolledWdg: corrected a doc string error.
-   RO.Wdg.StatusConfigGridder: ConfigCat is now a class constant.

### 2004-11-19

-   Bug fix in RO.Comm.GetFile: was downloading binary files as text files. Fixed by explicitly sending TYPE I or TYPE A before any transfer.

### 2004-11-18

-   RO.Comm.GetFile renamed to RO.Comm.FTPGet; the UI changed because I started using ftplib instead of urllib to avoid a [bug in urllib](http://sourceforge.net/tracker/index.php?func=detail&aid=1067702&group_id=5470&atid=105470), and so only ftp is now supported.
-   RO.Wdg.Checkbutton: more sensible defaults; if showValue true then defaults to indicatoron false. If indicatoron false then defaults to padx = 5, pady = 2.
-   RO.Wdg.FTPLogWdg: getFile arguments overhauled to match the changes in RO.Comm.GetFile -\> RO.Comm.FTPGet mentioned above.
-   RO.Wdg.Label: renamed method \_setStatus to setStatus (it is a useful public method).

### 2004-11-04

-   Improved RO.DS9 as follows:
    -   Improved Mac compatibility (formerly required ds9 to be on the \$PATH. Now DS9 first looks for ds9.app in \~/Applications and /Applications, then looks on the \$PATH. Note: this means MacOS X users cannot put ds9.app "just anywhere" unless they also make a link from somewhere on their path to ds9.app/ds9.
    -   Added Windows compatibility (but showArray is broken, probably due to a bug in ds9 3.0.3).
    -   Changed order of indices for 3-d images from (y,x,z) to (z,y,x).
    -   loadFITSFile no longer tests the file name's extension.
    -   Eliminated showBinFile because I could not get it to work; this seems to be an bug or documentation bug in ds9
    -   Bug fix: could only communicate with one ds9; fixed by specifying port=0 when opening ds9.

-   RO.Wdg.PatchedCanvas: the corrections applied by this module are no longer needed and have been disabled. This module now issues a deprecation warning when used, and really doesn't do anything else. Please use Tkinter.Canvas instead.

### 2004-10-13

-   New modules:
    -   RO.Comm.BrowseURL: opens a URL in the user's default web browser. The launching is done in a background thread.
    -   RO.Constants: centralize widely used RO.Wdg constants. includes state constants have a prefix st\_: st\_Normal, st\_Warning, st\_Error.
    -   RO.ScriptRunner and RO.Wdg.ScriptWdg: executes python scripts that can simply ask to wait for things to happen without tying up the event loop. This saves the script author from having to explicitly worry about asynchronous programming and writing a tangle of callback funcions. This has proven so useful that my application user interface now makes heavy use of it internally.
    -   RO.Wdg.Text added to simplify read-only and contextual menu support.
    -   RO.Wdg.TkUtil: implements colorOK and getWindowingSystem.

-   Other changes:
    -   RO.Comm.TkSocket now works at the tcl level using fileevents and tcl sockets. This fixes a Windows incompatibility.
    -   RO.CnvUtil: added asBoolOrNone
    -   RO.InputCont.ContList: the callback gets the entire ContList, not just the changed container(s), and only one callback is issued for setValueDict and restoreDefault, rather than one callback per container.
    -   RO.KeyDispatcher: many improvements, including: Pending commands are aborted when disconnected. Improved the multitasking while refreshing variables and checking for command timouts. Added \_replyCmdVar method to unify the sending of replies to command variables. No longer issues regular KeyVariable updates while disconnected.
    -   RO.Prefs.PrefVar: DirectoryPrefVar and FilePrefVar modified to have no text entry field. This solves a focus infinite loop issue: if the user typed in an invalid value and then tried to use Choose..., the dialog box would never get focus because the edit field would take it back. This left the user no choice but to close the dialog box.
    -   RO.Wdg changes:
        -   The contextual menu for editable RO.Wdg widgets now includes Cut, Copy, Clear, Paste and Select All (read-only widgets only have Copy).
        -   RO.Wdg.CmdReplyWdg: added support for the command message callback to report an error. Renamed event callbacks with leading \_ to indicate they are internal functions. Deleted the old and redundant method showCmd.
        -   RO.Wdg.CtxMenu changes:
            -   Renamed AddCtxMenu to addCtxMenu, since it is a function.
            -   Changed ctxShowHelp so that if a file: URL with an anchor cannot be loaded, it tries the same URL with the anchor stripped. This works around a limitation in MacOS X and possibly other platforms. (Note: in some earlier versions of MacOS X the anchor was silently ignored, but in 10.3.3 the file is not found.)
            -   CtxMenu no longer checks if the widget already has a contextual menu. This was done to allow RO.Wdg.StatusBar to inherit from CtxMenuMixin.
            -   Help url base handling moved to new RO.Wdg.Constants module.

        -   RO.Wdg.Entry:
            -   DMSEntry: added unitsSuffix (for velocity).
            -   Removed DirectoryEntry and FileEntry. Dir and file preferences no longer use entry widgets (see RO.Prefs item below), so they are no longer useful.

        -   Renamed RO.Wdg.ScriptWindow to RO.Wdg.PythonWdg to better reflect what it does and to avoid confusion with the new RO.ScriptRunner and RO.Wdg.ScriptWdg modules. Also modified to add a contextual menu.
        -   RO.Wdg.StatusBar changes:
            -   No longer shows informational messages while executing commands. Just showns warnings, errors and completion. This was done to make the display easier to read.
            -   Added a helpText argument. Warning: if specified, this prevents the status bar from trying to show help and entry errors for other widgets in the same toplevel. helpText is typically only specified if you have more than one status bar in a toplevel, in which case one status bar should show help (as usual) and the others should have helpText strings (and thus not show help).
            -   Inherits from RO.Wdg.CtxMenu, making it easier to customize its contextual menu.
            -   Message levels documented to use RO.Wdg.st\_Normal, st\_Warning and st\_Error constants. The numerical values have not changed, so old code will still work.

        -   Renamed RO.Wdg.PythonTk to RO.Wdg.PythonTk for the same reason.
        -   RO.Wdg.Toplevel closeMode constants now have prefix tl\_: tl\_CloseDestroys, tl\_CloseWithdraws, tl\_CloseDisabled
        -   RO.Wdg.WdgPrefs: handles internal RO.Wdg prefs. This combines code that was formerly in RO.Wdg.Label and RO.Wdg.CxtMenu.

-   Bug fixes:
    -   RO.AddCallback: used sys and traceback for error reporting but did not import them.
    -   RO.Comm.TkSocket: fixed documentation for setReadCallback.
    -   RO.Comm.TCPConnection: fixed documentation for addReadCallback and addStateCallback.
    -   RO.Entry.DMSEntry: units for relative dms fields had ' and " swapped.
    -   RO.KeyVariable: major overhaul, including renaming KeyVar to CmdVar, adding abort capability and adding refreshOptional argument to KeyVarFactory.
    -   RO.Wdg.RadiobuttonSet fixes:
        -   set and setDefault could reject valid values and set invalid values because they were checking the new value against textList (the list of button names) not valueList (the list of button values).
        -   The module was using importing RO.AddCallback but not importing it.

    -   RO.Wdg.Toplevel fixes:
        -   If wdgFunc fails, Toplevel propogates the error. As a result, ToplevelSet.createToplevel no longer creates an erroneous entry to a nonexistent toplevel if wdgFunc fails.
        -   Toplevels that were distroyed were not handled well. Now getToplevel returns None if a toplevel has been destroyed (or does not exist). Also, a name can be reused if the old toplevel has been destroyed.

### 2004-05-21

-   Overhauled DS9 so it can talk to multiple copies (e.g. windows) by name. Added the ability to launch copies of ds9 automatically as needed. Added xpaget.
-   Fixed the following bugs (most found by pychecker):
    -   RO.Comm.GetFile and RO.Wdg.StatusBar: used sys.stderr to report some errors but did not import sys.
    -   RO.SeqUtil: flatten was called flattenList in a few places, breaking the flatten function.
    -   RO.Wdg.CmdReplyWdg: did not create self.cmdText if helpURL not supplied.
    -   RO.Wdg.Toplevel.ToplevelSet: referred to defGeomFixDict instead of defGeomVisDict

### 2004-04-30

-   Added xpaset to DS9. This can be used to display regions, etc.

### 2004-04-21

-   Fixed some bugs in DS9.showArray (x and y axes sizes were swapped and it failed for any integral type except Int32) and made it more flexible (it will now accept any type of array so long as the data is in range of Int32).

### 2004-04-16

-   Added the DS9 module for displaying images in the ds9 image viewer.

### 2004-02-06

-   Combined RO.OS.walkDirs and RO.OS.expandPathList into RO.OS.findFiles.
-   Modified RO.procFiles to take advantage of RO.OS.findFiles. Arguments have changed.
-   Fixed a bug in RO.procFiles that caused specifying an output file to fail.

### 2004-02-05

-   Added functions to RO.OS including getPrefsDir.
-   Modified RO.KeyDispatcher.logMsg to make it easier to use; the changes are not backwards compatible.
-   Fixed a bug in RO.Prefs.DirectoryPrefVar that prevented the Choose... button from working.

<!-- -->

    Russell Owen
    University of Washington
    PO Box 351580
    Seattle, WA 98195-1580
    rowen u washington edu
         @ .          .
