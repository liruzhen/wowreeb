# wowreeb
An intelligent, versatile, and multi-versioned World of Warcraft launcher

This application was made to have a reliable and efficient way to launch different versions of World of Warcraft without having to manually edit files.  It is configured in XML, and is lightweight enough to be loaded by Windows upon login.  It will create a system tray icon which will display a menu showing the different options defined in the configuration file.  An example configuration file is included.

## Configuration

Included in the source as well as binary tarballs is an `example_config.xml` file.  Use this as a guide for configuring wowreeb for your system.  It must be renamed to `config.xml` in order for wowreeb to find it.  Explanations for the various settings are included in comments in the example configuration file.

## New In Version 2.0

Now includes 64 bit support and the option to clear client cache before launch

## Technical Information

This application is written in C++.  It includes a 32 bit and 64 bit executable and DLL.  The project depends on hadesmem (https://github.com/RaptorFactor/hadesmem).  When the helper DLL is loaded by a newly launched World of Warcraft process, it will adjust the environment in the manner requested by the launcher.  This includes setting the name of the authentication server and optionally adjusting the graphics engine field-of-view (FoV) value.

## Security

Though the included helper DLL (wowreeb32.dll or wowreeb64.dll) is injected into the World of Warcraft process, it will eject itself once its initialization is complete.  Therefore the DLL itself should not be detectable by Warden.

**HOWEVER** if your configuration file defines a change to the FoV value, this change **is detectable** by Warden.  No reasonable server developer would bother to detect this, but use at your own risk!

It is also theoretically possible that the loading and unloading of the helper DLL does leave some residual footprint even after it is unloaded, and that that footprint may be detectable by Warden.  Again, nothing about this launcher would qualify as a 'hack' or an 'exploit', therefore it should be safe to use anywhere.

**TLDR**  Use at your own risk!