# GlPortal for Visual Studio 2017
Are you on another platform or do you want to use mingw for building then have a look at how to [build GlPortal on Mac or Linux](https://github.com/GlPortal/glPortal/blob/master/COMPILE.md).

To see these instructions in action look at the [video guide](https://www.youtube.com/watch?v=uG2y1zHDk-k&feature=youtu.be).

    Make sure to set each VS solution to Debug/x64 before compiling

This is a first draft. But it's quite easy to build, just somewhat annoying to use cmake-gui for nearly every dependency and to have to drag and drop it into Visual Studio to build it, then copy the dlls, fix the /MTT setting for the 3 Bullet projects.

I have little CMake experience, probably it can be simplified and configured with a CMake script, so nearly no user interaction is needed anymore.

Since every dependency is build in "Debug" mode, the game can barely reach 20 fps so far. Didn't configure it for Release yet.

Just as reminder, if you are about to regenerate the solution by hand: Since Visual Studio doesn't support same file names in subfolders, we have to fix it manually in the solution:
 - Right-click on RadixEngine/source/simulation/Player.cpp
 - C/C++ -> output files -> object file name: set it to: $(IntDir)simulation\
 
The CMake generated Bullet solution is by default Multithreaded-Debug, but it needs to be Multithreaded-Debug-DLL, for these three projects: BulletCollision, BulletDynamics, LinearMath
 
Not automatic yet: once everything is built, copy these dlls into VS2017\GlPortal\x64\Debug:

	assimp\build\code\Debug\assimp-vc140-mt.dll
	FreeImage\x64\Debug\FreeImaged.dll
	SDL2\build\Debug\SDL2d.dll
	SDL2_mixer\VisualC\external\lib\x64\libFLAC-8.dll
	SDL2_mixer\VisualC\external\lib\x64\libmodplug-1.dll
	SDL2_mixer\VisualC\external\lib\x64\libmpg123-0.dll
	SDL2_mixer\VisualC\external\lib\x64\libogg-0.dll
	SDL2_mixer\VisualC\external\lib\x64\libvorbis-0.dll
	SDL2_mixer\VisualC\external\lib\x64\libvorbisfile-3.dll
	SDL2_mixer\VisualC\x64\Debug\SDL2_mixer.dll
	tinyxml2\build\Debug\tinyxml2d.dll

## Todo:
 - Ground work is done and proven to be working, slowly swap stuff out to be done by CMake
 - Currently only the Debug configurations are configured, repeat it with Release configurations... or rather generate Solution now via CMake
