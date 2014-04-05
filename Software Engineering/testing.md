# Testing

## Philosophy

* Break it into small pieces that are easy to test on their own.
* Tests are specific, code will attempt to be general.
* Reading a program might tell you *what* it does, it might not tell you *why* it does that. Tests can tell you the *why*.
* Tests are often used to check what happens when a program is given unexpected input, either due to user error or malicious attacks, ensuring the program deals with such inputs safely and gracefully.
* Modules are easiest to test when they are small, focused on one concern, not excessively coupled to other parts of the system, and have well-defined APIs and few dependencies.
* Making code more modular reduces the cognitive load of working on any component of it, and helps us work more productively.
* When something is painful to test, this acts as design feedback: maybe the test requires too much elaborate setup before the real work can be done, and this could indicate the module you're testing is too coupled to other concerns.
* The trick is to not let the specifics of the problem cloud your thinking; interacting with a database and receiving messages via a WebSocket are not that different if you ignore what the code 'means' and focus on its 'language-level' properties.

## Do

* Write modular code
* Few hard-coded dependencies
* Separating concerns
* Decoupling components via dependency injection or event systems
* Avoiding global shared state
* Simpler and more explicit