# simple test IG

Demonstrate the use of an [IG Builder service](https://github.com/jmandel/fhir-ig-builder), currently deployed to AWS API Gateway + Lambda that can build a IG from a github repo, given:

1) org name
2) repo name
3) core currently assumes the ig JSON file is `ig.json` See example at https://github.com/test-igs/simple

To manually trigger a build:

    curl -X POST "https://2rxzc1u4ji.execute-api.us-east-1.amazonaws.com/prod/publish?org=test-igs&repo=simple"

Or you can set up a github webhook to ping this URL on commit.

In either case, the built site shows up at: http://ig.fhir.org.s3-website-us-east-1.amazonaws.com/test-igs/simple/

(We can alias `ig.fhir.org` to this bucket so the final URL would be http://ig.fhir.org/test-igs/simple/)

Note that currently the build is totally broken, so I just upload the whole dir, including source + qa, for debugging purposes.
