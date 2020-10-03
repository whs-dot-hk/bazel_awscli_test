```sh
bazel test //:awscli_v1_test
bazel test //:awscli_v2_test
```

```sh
docker_run_flags=-v$(pwd)/credentials:/my_aws_credentials\ -eAWS_SHARED_CREDENTIALS_FILE=/my_aws_credentials
```

```sh
docker pull amazon/aws-cli:2.0.54
docker run -it --entrypoint= $docker_run_flags amazon/aws-cli:2.0.54 aws sts get-caller-identity
```

```sh
(
version=v1
bazel run //:awscli_${version}_wrapper
docker run -it $docker_run_flags bazel:awscli_${version}_wrapper aws sts get-caller-identity
)
```

```sh
(
version=v2
bazel run //:awscli_${version}_wrapper
docker run -it $docker_run_flags bazel:awscli_${version}_wrapper aws sts get-caller-identity
)
```

```sh
unset docker_run_flags
```
