# Notes for deploying verisart's tweaked changes

This fork contains a tweak to allow rows to appear larger when images are included.

1. Follow instructions in `developers-guide.md` to setup all prerequisites
2. Build everything and push to docker hub

        ./bin/build
        cp target/uberjar/metabase.jar bin/docker/
        cd bin/docker
        docker login
        docker build -t johnverisart/metabase-verisart:v0.36.3-verisart .
        docker push johnverisart/metabase-verisart:v0.36.3-verisart

3. Create a new Elastic Beanstalk App
4. Use Docker app type
5. Use ELB.zip for the software

## Merging in changes from the original project

1. Merge into this branch from the original project
2. Update the version number in `Dockerrun.aws.json` (keep `-verisart` in)
3. Run `zip ELB.zip Dockerrun.aws.json`
4. Edit the above instructions to reflect the new version
