# Notes for deploying verisart's tweaked changes

This fork contains a tweak to allow rows to appear larger when images are included.

1. Follow instructions in `developers-guide.md` to setup all prerequisites
2. Build everything and push to docker hub

        ./bin/build
        cp target/uberjar/metabase.jar bin/docker/
        cd bin/docker
        docker login johnverisart
        docker build -t johnverisart/metabase-verisart:v0.35.4-verisart3 .
        docker push johnverisart/metabase-verisart:v0.35.4-verisart3

3. Create a new Elastic Beanstalk App
4. Use Docker app type
5. Use ELB.zip for the software 
