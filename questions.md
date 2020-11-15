## Conceptual Exercise

**How is the logged in user being kept track of?**
Stored in sessions with CURR_USER_KEY = "curr_user"

**What is Flask’s g object?**
 It is a global namespace for holding any data you want during a single app context / one request response cycle. If you used a normal global variable, one request might modify the global variable and interfere with another request that happens to be executing simultaneously. To avoid that, Flask provides this g object to which you can attach such variables. Each request gets a different g object, so simultaneous requests can't interfere with each other, but you still have the same convenience as a global variable.

**What is the purpose of add_user_to_g?**
This sets the g object (g.user) to the user key if the user's key is in session.  It does this before each request (@app.before_request) since the g object only works for one request/response cycle.

**What does @app.before_request mean?**
Decorator that allows us to create a function that will run before each request.
