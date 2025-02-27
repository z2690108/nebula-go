# nebula-go

[![Go Reference](https://pkg.go.dev/badge/github.com/vesoft-inc/nebula-go/v3.svg)](https://pkg.go.dev/github.com/vesoft-inc/nebula-go/v3)
![functional tests](https://github.com/vesoft-inc/nebula-go/actions/workflows/test.yaml/badge.svg)
[![codecov](https://codecov.io/gh/vesoft-inc/nebula-go/branch/master/graph/badge.svg?token=dzUo5KdSux)](https://codecov.io/gh/vesoft-inc/nebula-go)

**IMPORTANT: Code of Nebula go client has been transferred from [nebula-clients](https://github.com/vesoft-inc/nebula-clients) to this repository(nebula-go), and new releases in the future will be published in this repository.
Please update your go.mod and imports correspondingly.**

Official Nebula Go client which communicates with the server using [fbthrift](https://github.com/facebook/fbthrift/). Currently the latest stable release is **[v3.3.0](https://github.com/vesoft-inc/nebula-go/tree/release-v3.3)**

The code in **master branch** will be updated to accommodate the nightly changes made in NebulaGraph.
To Use the console with a stable release of NebulaGraph, please check the branches and use the corresponding version.

| Client version | Nebula Service Version|
|:--------------:|:-------------------:|
|   **[v1.0.0](https://github.com/vesoft-inc/nebula-go/tree/v1.0)**              |       1.x.x         |
|   **[v2.0.0-ga](https://github.com/vesoft-inc/nebula-go/tree/v2.0.0-ga)**      |       2.0.0-ga, 2.0.1    |
|   **[v2.5.1](https://github.com/vesoft-inc/nebula-go/tree/v2.5.1)**      |       2.5.0    |
|   **[v2.6.0](https://github.com/vesoft-inc/nebula-go/tree/v2.6.0)**      |       2.6.0    |
|   **[v3.0.0](https://github.com/vesoft-inc/nebula-go/tree/v3.0.0)**      |       3.0.0    |
|   **[v3.1.x](https://github.com/vesoft-inc/nebula-go/tree/v3.1.0)**      |       3.1.x    |
|   **[v3.2.x](https://github.com/vesoft-inc/nebula-go/tree/v3.2.0)**      |       3.1.x-3.2.x    |
|   **[v3.3.x](https://github.com/vesoft-inc/nebula-go/tree/v3.3.0)**      |       3.1.x-3.3.x    |
|   **[master](https://github.com/vesoft-inc/nebula-go/tree/master)**     |       3.x-nightly |

Please be careful not to modify the files in the nebula directory, these codes were all generated by fbthrift.

**NOTE** Installing Nebula Go v2.5.0 could cause **checksum mismatch**, use v2.5.1 instead.

## Install & Update

```shell
$ go get -u -v github.com/vesoft-inc/nebula-go/v3@master
```

You can specify the version of Nebula-go by substituting `<tag>` in `$ go get -u -v github.com/vesoft-inc/nebula-go@<tag>`.
For example:

  for v3: `$ go get -u -v github.com/vesoft-inc/nebula-go/v3@v3.3.0`

  for v2: `$ go get -u -v github.com/vesoft-inc/nebula-go/v2@v2.6.0`

**Note**: You will get a message like this if you don't specify a tag:

> ```shell
> $ go get -u -v github.com/vesoft-inc/nebula-go/v2@master
> go: github.com/vesoft-inc/nebula-go/v2 master => v2.0.0-20210506025434-97d4168c5c4d
> ```
>
> Here the `20210506025434-97d4168c5c4d` is a version tag auto-generated by Github using commit date and SHA.
> This should match the latest commit in the master branch.

## Usage example

[Simple Code Example](https://github.com/vesoft-inc/nebula-go/tree/master/basic_example/graph_client_basic_example.go)

[Code Example with Gorountines](https://github.com/vesoft-inc/nebula-go/tree/master/gorountines_example/graph_client_goroutines_example.go)

[Session Pool Example](https://github.com/vesoft-inc/nebula-go/blob/master/session_pool_example/session_pool_example.go)

There are some limitations while using the session pool:
1. There MUST be an existing space in the DB before initializing the session pool.
2. Each session pool is corresponding to a single USER and a single Space. This is to ensure that the user's access control is consistent. i.g. The same user may have different access privileges in different spaces. If you need to run queries in different spaces, you may have multiple session pools.
3. Every time when sessinPool.execute() is called, the session will execute the query in the space set in the session pool config.
4. Commands that alter passwords or drop users should NOT be executed via session pool.

## Licensing

**Nebula GO** is under [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0) license, so you can freely download, modify, and deploy the source code to meet your needs. You can also freely deploy **Nebula GO** as a back-end service to support your SaaS deployment.
