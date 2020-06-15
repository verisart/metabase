# Notes for deploying verisart's tweaked changes


1. Follow build instructions in `developers-guide.md`
2. Run `cp target/uberjar/metabase.jar bin/docker/`
3. `cd bin/docker`
4. `docker login johnverisart`
5. `docker build -t johnverisart/metabase-verisart .`
6. `docker push johnverisart/metabase-verisart:latest`
7. Create a new Elastic Beanstalk App
8. Use Docker app type
9. Use ELB.zip for the software 
