SUBDIRS = po

bin_SCRIPTS = startxde xde-logout

# Currently these paths are hardcoded.
xsessiondir=$(xsesspath)
xsession_DATA = XDE.desktop

defaultsdir=$(sysconfdir)/xdg/xwm
defaults_DATA = autostart

desktopdir=$(datadir)/applications
desktop_in_files = xde-logout.desktop.in xde-screenlock.desktop.in
desktop_DATA = $(desktop_in_files:.desktop.in=.desktop)
@INTLTOOL_DESKTOP_RULE@

EXTRA_DIST = \
	autostart \
	XDE.desktop.in.in \
	$(desktop_in_files) \
	startxde.in

CLEANFILES = $(bin_SCRIPTS) XDE.desktop $(desktop_DATA)

