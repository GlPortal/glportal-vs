*glPortal for Visual Studio 2017*


Just as reminder, if you are about to regenerate the solution by hand:

Since Visual Studio doesn't support same file names in subfolders, we have to fix it manually in the solution:

Right-click on RadixEngine/source/simulation/Player.cpp
 - C/C++ -> output files -> object file name: set it to: $(IntDir)simulation\

 
 
The CMake generated Bullet solution is by default Multithreaded-Debug, but it needs to be Multithreaded-Debug-DLL, for these three projects: BulletCollision, BulletDynamics, LinearMath
 
 
 
Not automatically yet: once everything is built, copy these dll's into VS2017\GlPortal\x64\Debug:

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

Todo:
 - Filthiest work is done so far and proven to be working, slowly swap stuff out to be done by CMake
 - Currently only the Debug configurations are configured, repeat it with Release configurations... or rather generate Solution now via CMake