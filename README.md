# newmanAPIs ⚔️

![How](https://github.com/SalhiFayza/newmanAPIs/assets/60444937/6ae84cf8-a707-437a-aa5e-43aa9129f200)

# Show details 📑:

[How.pdf](https://github.com/SalhiFayza/newmanAPIs/files/13170301/How.pdf)

# Black.yaml

name: Newman
on:
  workflow_dispatch:
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: install report htmlextra
        run: npm install -g newman-reporter-htmlextra
      - name: Run newman
        run: newman run Products.postman_collection.json -e EnvironmentDev.postman_environment.json -g workspace.postman_globals.json -n 5 -r htmlextra
      - uses: actions/upload-artifact@v3
        with:
          name: my-artifact
          path: ./newman
