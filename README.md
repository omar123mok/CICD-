
# CI/CD-

A 2 stage/phases CI/CD pipeline.

The workflow triggers the 2 jobs which runs the python script and then creates an artifact of the python script.


## Code

Python script, which prints Hello World.

```python
print("Hello World")
```

Workflow:
#
Event used for Workflow is push.

Contains 2 jobs: 

job1- Checkout the repository and run python script.

job2- Dependency on job1, checkout the repository and create an artifact.
                 
