## How to apply automated unit testing and continuous integration to a simple JavaScript project

### What is automated testing?
Automated Testing is that testing where tests are run without human intervention.

### What is Continuous Integration?
Continuous Integration is the practice of integration of code change into single codebase countinuously.

Lets make pipeline for software development

- file changes
- trigger an automated testing
- release to production

These can be done by the help of continuous integration.

Lets get into Github actions as CI/CD service

For CI/CD service, there need to be configured with a YAML file which takes:

- name of the pipeline or workflow
- list of jobs
- list of steps for every job

Github search config file under ./github/workflows
so lets create javascript.yaml file under ./github/workflows

```yaml
    name: JavaScript workflow
    on: [push]
    jobs:
      test:
        runs-on: ubuntu-latest
        steps:
        - uses: actions/checkout@v1
        - name: Use Node.js 12.x
          uses: actions/setup-node@v1
          with:
            node-version: "12.x"
        - name: npm install, and test
          run: |
            npm install
            npm test
          env:
            CI: true

```

Now commmit and push on github.

You will see running job on github Actions Tab.