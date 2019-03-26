# Interview task/assignment: speed up a simple path tracer

This project contains a simple triangle mesh path tracer implemented in C++.
It's a command line application that takes screen size & input .OBJ data file parameters,
renders it using "path tracing" algorithm and produces `output.png` result file.

Here are some images that the program can produce with the data files present under `data/` directory:

![result1](/result3Suzanne.png?raw=true "Suzanne")
![result2](/result5Sponza.png?raw=true "Sponza")

## The Task

Current program is slow. *Really slow*. Rendering that monkey head model ("Suzanne") at a lowly 640x360 resolution,
4 samples per pixel, takes **one minute** on my PC! Rendering the other image ("Sponza") at the same resolution takes **half an hour**.

Your task then is, of course, to make the program faster :)

I know for sure that it is possible to make it faster by about a *hundred times* -- e.g. I got Suzanne from a minute down to 0.2 seconds,
and Sponza from half an hour down to about 8 seconds. It might be possible to make it even faster, but I did not quite go there.

Now, **your task is to make it run as fast as you can**. I'm not asking for a "hundred times", but something like "**at least ten times faster**"
is what you should aim for.

It's entirely your choice how you will do it. Better algorithms? More efficient math? Better data layout? Multi-threading? SIMD?
Rewrite in assembly? Rewrite as a compute shader / CUDA / OpenCL? Rewrite for NVIDIA RTX? All of these? You pick :) Some of what I listed
here is "certainly overkill" and not needed; achieving a 10x faster performance is entirely possible using relatively simple means.

Go!


## About the code

I made it work on Windows (Visual Studio 2017) and Mac (Xcode 10); the project files for them are respectively in
`projects/VisualStudio/TrimeshTracer.sln` and `projects/Xcode/TrimeshTracer.xcodeproj`. If you have any trouble building or running it,
ask me!

The application accepts four command line arguments as input: `<width> <height> <spp> <datafile>`:

* `width` is image width in pixels,
* `height` is image height in pixels,
* `spp` is "samples per pixel"; kind of like "anti-aliasing level",
* `datafile` is path to a mesh to render; in Wavefront .OBJ format.

I added some example meshes under `data/` folder; initially I suggest starting with e.g. `data/cube.obj` which is just a simple
cube. I do *not* recommend trying to run the non-optimized version of the program on for example the Sponza model - it contains 66k
triangles and will run *very very slow*.

The code itself is fairly simple C++ code, and I tried to comment it extensively. No previous experience with ray-tracers
or path-tracers should be required.

If you *do* want to read up on what this "path tracing" thing is *(and maybe even get some ideas how to make it faster? who knows)*,
I can recommend "Ray Tracing in a Weekend", "Ray Tracing: The Next Week" and "Ray Tracing: the Rest of Your Life" minibook series,
which have been recently [made free here](http://www.realtimerendering.com/raytracing/).

Overall I would recommend making a clone of this project on github and using "actual version control" workflow to make your changes.
If you don't like git or version control, that's fine; I can accept submissions in zip or dropbox or google drive (or whatever) form.
As long as I can see the code and try it out.

Your optimized program should produce same looking images as the original one, just *do it faster*.
