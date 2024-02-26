[Link](https://see.stanford.edu/materials/icsppcs107/04-Assignment-1-RSG.pdf)

# Background
- **Grammar** = Template that describes various combinations of words resulting in a valid sentence.
- **Non-Terminal** = You can those placeholders with other sequence.
- **Terminal** = Normal word.
- **Definition** = Non-Terminals + set of possible **productions (or expansions)**.
***
# `definition.h`

- Constructors:
	- Default = For instantiating a nonterminal string ("") with empty productions. Needed as some ***STL containers require elements to have default constructor***.
	- `ifstream` = As long as contents of file are as per description, then it can instantiate based on file contents.
- Methods:
	- `getNonterminal` = Returns constant **immutable reference**(*Reference (pointer), that cannot be used to modify the data it refers to*) to embedded nonterminal.
	- `getRandomProduction` = Returns exactly one expansion based on **definition** and **productions** are chosen at Random.

***
# `production.h`

- Constructors:
	- Default = `vector` needs its elements to have a default constructor, plus the one instantiated with this can be a clone to meaningful one if user assigns it.
	- `ifstream` = reads *terminals* and *non terminals* until a `;` is read and rest data is discarded.
	- `vector<string>` = it can treat provided vector of strings as productions, and encapsulate them as an object. It assigns given `vector` to `phrases`.
- Iterators:
	- `begin`
		- `const`
		- regular
	- `end`
		- `const`
		- regular
***
# `random.h`

- Constructor
	- Default
- Method
	- `getRandomInteger` = [[Uniform Distribution]]
***
