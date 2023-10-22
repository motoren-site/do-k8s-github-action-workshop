name: Build and push container to docker repo containers @ DO
on:
  push:
    branches:
      - main
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
    - name: Git Checkout
      uses: actions/checkout@v1

    - name: Login to Digital Ocean Registry
      uses: docker/login-action@v1
      with:
        registry: registry.digitalocean.com
        username: ${{ secrets.DIGITAL_OCEAN_TOKEN }}
        password: ${{ secrets.DIGITAL_OCEAN_TOKEN }}

    - name: Build latest
      run: docker build -t registry.digitalocean.com/containers/YOUR_APP:$(echo $GITHUB_SHA | head -c7) .

    ##Add step for pusing to registry.digitalocean.com/containers
