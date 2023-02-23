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

You then create the movie frame by frame. Each frame requires a graphics object. MovieMaker renders the frame immediately.

    mm.frame(graphics)

You can optionally supply a `Camera` object that contains view information, and a `List` giving the positions of lights:

    mm.frame(graphics, camera=cam, lights=lt)

Once you've generated each frame, call 

    mm.make() 

to create the movie. Then use

    mm.clean() 

to delete all the individual frames. 
