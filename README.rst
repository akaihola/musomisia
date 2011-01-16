=============================================================
 Musomisia -- keyboard-centric tools for Linux desktop users
=============================================================

mcgr
====

Mcgr[1]_ provides hot-key access for

 * launching applications

 * focusing running applications

 * window layout management.

Once run, the `mcgr` script accepts the followig commands through the
`/tmp/mcgr.fifo` FIFO:

goto-or-run <WM_CLASS> <commandline>
------------------------------------

If a window with a matching `WM_CLASS` is found, it receives the focus.  If the
window is not on the current workspace, the correct workspace is activated
first.  If a matching window already has focus, the next window with the same
`WM_CLASS` is focused instead.  Multiple successive calls with the same
`WM_CLASS` loop over all matching windows.

If no window with a matching `WM_CLASS` is found, the command line is run
instead.

Example:

    echo "goto-or-run Firefox firefox -P profilename" >>/tmp/mcgr.fifo

In GNOME key bindings use e.g.:

    sh -c "[ -p /tmp/mcgr.fifo ] && echo Firefox firefox -P profilename >>/tmp/mcgr.fifo" 

.. [1] originally named for "MetaCity Go to or Run", now works with other window
   managers as well)
