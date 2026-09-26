[comment]: # (Movie maker module help)
[version]: # (0.5)

# MovieMaker
[tag moviemaker]: # (moviemaker)

The `moviemaker` module provides a MovieMaker class that simplifies the creation of movies from a sequence of frames with morpho.

To use the module, use import as usual:

    import moviemaker

Create a `MovieMaker` object with a filename for the movie. You don't need to supply an extension.

    var mm = MovieMaker("arrow")

You can choose an optional framerate:

    var mm = MovieMaker("arrow", framerate=24)

A `Camera` from the `povray` module sets the view for every frame. Omit it to use the default camera (2048×1536, looking at the origin from `Matrix([0,0,5])`).

    var cam = Camera(width=640, height=480)
    var mm = MovieMaker("arrow", camera=cam)

You then create the movie frame by frame. Each frame requires a `Graphics` or `Scene` object. MovieMaker renders the frame immediately.

    mm.frame(graphics)

Lighting comes from the graphic, unless `camera.light` is set. Set graphic lights with `setLights` or `addLight` before rendering:

    graphics.setLights("threepoint")
    graphics.addLight(Matrix([10,10,10]))
    mm.frame(graphics)

You can override the camera or the lights for a single frame. `lights` accepts the same values as `Graphics.setLights`: a named rig (`"neutral"`, `"threepoint"`, or `"off"`), a `Light`, a 3-vector, or a list of those.

    mm.frame(graphics, camera=cam, lights=lt)

`shadowless` and `transparent` are passed through to POV-Ray:

    mm.frame(graphics, shadowless=true, transparent=true)

Once you've generated each frame, call

    mm.make()

to create the movie. Then use

    mm.clean()

to delete all the individual frames.
