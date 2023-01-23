
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

```
name: CICD

on : push

jobs:
  job1:
    runs-on: ubuntu-latest
    steps:
      - name: checkout of repo
        uses: actions/checkout@v2

      - name: runing the python code
        run : python hello.py

  job2:
    needs: [job1]
    runs-on: ubuntu-latest
    env:
      ARTIFACT_NAME: python-script-
    steps:
      - name: checkout of repo
        uses: actions/checkout@v2
      
      - name: artifact creation
        uses: actions/upload-artifact@v2
        with:
          name: ${{ env.ARTIFACT_NAME }}
          path: ./hello.py
```

Contains 2 jobs: 

job1- Checkout the repository and run python script.

job2- Dependency on job1, checkout the repository and create an artifact.
                 
