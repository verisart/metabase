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

1. Go to the RDS instance here https://eu-west-2.console.aws.amazon.com/rds/home?region=eu-west-2#database:id=aafomld8q6eu5l;is-cluster=false
   and create a new manual DB snapshot
2. In GitHub, merge into this branch from the original project's main branch
3. Update the version number in `Dockerrun.aws.json` (keep `-verisart` in)
4. In this directory, run `zip ELB.zip Dockerrun.aws.json`
5. Edit the above instructions to reflect the new version
6. Go to the Elastic Beanstalk app here https://eu-west-2.console.aws.amazon.com/elasticbeanstalk/home?region=eu-west-2#/environment/dashboard?applicationName=metabase-verisart2&environmentId=e-vcyazaip3j
7. Click Upload and Deploy
8. Use the `ELB.zip` from this directory
