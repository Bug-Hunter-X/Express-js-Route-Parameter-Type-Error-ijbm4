# Express.js Route Parameter Type Error

This repository demonstrates a common error in Express.js route handling: failure to handle cases where route parameters are of the incorrect type.  Specifically, this example focuses on a scenario where an integer ID is expected but a non-numeric value is provided.

## Bug Description:

The provided code attempts to retrieve a user based on their ID, which is passed as a route parameter.  However, it lacks error handling for non-numeric IDs.  If a non-numeric ID is passed, `parseInt(userId)` will return `NaN`, causing the `.find()` method to fail silently or potentially throw an error, leading to unexpected behavior such as a 500 Internal Server Error instead of a more informative 404 Not Found.

## Solution:

The solution demonstrates proper error handling by explicitly checking if the parsed `userId` is a number using `isNaN()`. If it's not a number, a 400 Bad Request error is returned.  If no user is found with the given ID, a 404 Not Found error is returned.