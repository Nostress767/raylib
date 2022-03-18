cf=/c /utf-8 /F10000000 /nologo /O2 /W3 /MD /DPLATFORM_DESKTOP /DSTBI_NO_SIMD /D_CRT_SECURE_NO_WARNINGS /DMA_NO_WASAPI /DGRAPHICS_API_OPENGL_33

webcf=-std=gnu99 -Os -Wall -D_DEFAULT_SOURCE -Wno-missing-braces -Werror=pointer-arith -fno-strict-aliasing
webi=-I. -Iexternal/glfw/include -Iexternal/glfw/deps/mingw
graphics=-DGRAPHICS_API_OPENGL_ES2

arflags=/nologo /out:raylib.lib
modules=rglfw.obj rtextures.obj utils.obj rshapes.obj rtext.obj rmodels.obj raudio.obj

raylib.lib: rcore.obj $(modules)
	lib $(arflags) rcore.obj $(modules)

web:
	setlocal
	call C:\emsdk\emsdk_env.bat
	emcc -c rcore.c $(webcf) $(webi) -DPLATFORM_WEB $(graphics)
	emcc -c rshapes.c $(webcf) $(webi) -DPLATFORM_WEB $(graphics)
	emcc -c rtextures.c $(webcf) $(webi) -DPLATFORM_WEB $(graphics)
	emcc -c rtext.c $(webcf) $(webi) -DPLATFORM_WEB $(graphics)
	emcc -c rmodels.c $(webcf) $(webi) -DPLATFORM_WEB $(graphics)
	emcc -c raudio.c $(webcf) $(webi) -DPLATFORM_WEB
	emcc -c utils.c $(webcf) $(webi) -DPLATFORM_WEB
	emar rcs raylib.a rcore.o rshapes.o rtextures.o rtext.o rmodels.o raudio.o utils.o
	endlocal

rcore.obj:
	cl $(cf) /I.\external\glfw\include $*.c

$(modules):
	cl $(cf) $*.c


clean:
	del rcore.obj $(modules) raylib.lib libraylib.a

