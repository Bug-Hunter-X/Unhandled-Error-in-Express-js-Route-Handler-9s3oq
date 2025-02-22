# Unhandled Error in Express.js Route Handler

This repository demonstrates a common error in Express.js route handlers: insufficient error handling for invalid input and missing 404 responses.

## Bug

The `bug.js` file contains an Express.js route handler that fetches a user by ID.  It has two crucial flaws:

1. **Missing input validation:** It doesn't check if the `userId` is a valid number.  If a non-numeric ID is provided, `parseInt(userId)` will return `NaN`, leading to a `user` value of `undefined` and potentially unexpected behavior.
2. **Missing 404 response:** If a user with the given ID doesn't exist, it sends a simple 'User not found' string instead of a proper 404 Not Found HTTP status code.  This is crucial for client applications to handle the error gracefully.

## Solution

The `bugSolution.js` file shows the corrected route handler. It addresses both issues:

1. **Input validation:** It now checks if `userId` is a valid number. If not, it sends a 400 Bad Request response.
2. **Proper 404 response:** If the user is not found, it sends a 404 Not Found response with a JSON message.

This improved handler ensures better robustness and a more user-friendly experience.