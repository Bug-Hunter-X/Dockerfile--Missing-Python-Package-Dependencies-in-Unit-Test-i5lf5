# Dockerfile Bug: Missing Python Dependencies

This repository demonstrates a common error in Dockerfiles: forgetting to install necessary Python packages before running tests or applications. The original `Dockerfile` attempts to run unit tests using `unittest`, but fails because the required packages are not installed.

The `Dockerfile_solution` provides a corrected version that includes installing the required packages using `pip install -r requirements.txt`.

## Reproducing the Bug

1.  Clone this repository.
2.  Build the original `Dockerfile` using:  `docker build -t buggy-app .`
3.  Attempt to run the container: `docker run buggy-app` (This will likely fail)
4.  Build the corrected `Dockerfile_solution`: `docker build -t fixed-app -f Dockerfile_solution .`
5.  Run the container: `docker run fixed-app` (This should run the tests successfully, assuming requirements.txt is present)

## Solution

The solution involves adding a `pip install -r requirements.txt` instruction to the `Dockerfile`. Ensure that a `requirements.txt` file lists all the python project dependencies.