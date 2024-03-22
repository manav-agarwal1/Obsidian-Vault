[Link](https://see.stanford.edu/materials/icsppcs107/09-Assignment-2-Six-Degrees.pdf)

# `imdb.h`
- constructor = 
	- directory location: constructs imdb instance to layer of top of raw memory and is stored in specified directory. The directory contains the binary file as described in pdf.
- Methods = 
	- `good`: returns true if imdb instance opened without incident.
	- `getCredits`: query given name of actor from credits of movies in db, then return list of credits of movies they appeared in, in second argument.
	- `getCast`: given movie, returns the list of cast in the second argument.
- destructor
***
# `path.h`
- Overload `<<`. It is `friend` function.
- Constructor: Contain only given player and no one else.
- Methods = 
	- `getlenght` = number of movies from actor1 to actor2.
	- `addConnection` = no integrity check.
	- `undoConnection`
	- `getLastPlayer`
	- `reverse`
- `Connection` = struct of movie and player.
- In variables =
	- I only have first actor as the info
	- Rest are stored in connections in a vector
	- 
