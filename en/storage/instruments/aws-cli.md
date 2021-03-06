# AWS Command Line Interface (AWS CLI)

[AWS CLI](https://aws.amazon.com/cli/) is a command line interface designed for AWS services. To learn [how to run commands](https://docs.aws.amazon.com/cli/latest/reference/), see the official Amazon documentation.

To work with Yandex Object Storage via the AWS CLI, you can use the following sets of commands:

- [s3api](https://docs.aws.amazon.com/cli/latest/reference/s3api/index.html) — commands corresponding to operations in the REST API. Before you start, look through the [list of supported operations](../s3 /api-ref/index.md).
- [s3](https://docs.aws.amazon.com/cli/latest/reference/s3/index.html) — additional commands that make it easier to work with a large number of objects.

## Before you start {#preparations}

{% include [storage-s3-http-api-preps](../_includes_service/storage-s3-http-api-preps.md) %}

## Installation {#installation}

To install the AWS CLI, follow the [instructions](https://docs.aws.amazon.com/cli/latest/userguide/installing.html) on the manufacturer's website.

## Setup {#setup}

To configure the AWS CLI, use the `aws configure` command. The command will request values for the following parameters:

1. `AWS Access Key ID`: enter the ID of the key that you received when generating the static key.

1. `AWS Secret Access Key`: enter the secret key that you received when generating the static key.

1. `Default region name`: enter `us-east-1`.

   {% note info %}

   To work with Yandex Object Storage, always specify the `us-east-1` region. A different value of the region may lead to an authorization error.

   {% endnote %}

1. Leave the other parameter values of the other parameters unchanged.

### Configuration files {#config-files}

The `aws configure` command will result in saving your settings to the following files:

- Your static key to the `.aws/credentials` file in the format:

    ```
    [default]
                aws_access_key_id = id
                aws_secret_access_key = secretKey
    ```

- The default region to the `.aws/config` file in the format:

    ```
    [default]
                region=us-east-1
    ```

## Specifics {#specifics}

When using the AWS CLI to work with Object Storage, keep the following in mind:

- The AWS CLI works with Object Storage like a hierarchical file system and object keys look like a file path.
- When running the `aws` command to work with Object Storage, the `--endpoint-url` parameter is required because the client is configured to work with Amazon servers by default.
- When using macOS, in some cases you need to run the command:

    ```
    export PYTHONPATH=/Library/Python/2.7/site-packages; aws --endpoint-url=https://storage.yandexcloud.net s3 ls
    ```

## Examples of operations {#aws-cli-examples}

### Create a bucket

   ```bash
   aws --endpoint-url=https://storage.yandexcloud.net s3 mb s3://bucket-name
   ```

{% note info %}

When creating a bucket, follow the [naming guidelines](../concepts/bucket.md#naming).

{% endnote %}

### Uploading objects

You can upload objects using one of the following methods:

- Upload all objects from a local directory:

   ```bash
   aws --endpoint-url=https://storage.yandexcloud.net \
       s3 cp --recursive local_files/ s3://bucket-name/path_style_prefix/
   ```
- Upload objects specified in the `--include` filter and skip objects specified in the `--exclude` filter:

   ```bash
   aws --endpoint-url=https://storage.yandexcloud.net \
       s3 cp --recursive --exclude "*" --include "*.log" \
       local_files/ s3://bucket-name/path_style_prefix/
   ```
- Upload objects one by one, running the following command for each object:

   ```bash
   aws --endpoint-url=https://storage.yandexcloud.net \
       s3 cp testfile.txt s3://bucket-name/path_style_prefix/textfile.txt
   ```

### Getting a list of objects

   ```bash
   aws --endpoint-url=https://storage.yandexcloud.net \
       s3 ls --recursive s3://bucket-name
   ```

### Deleting objects

You can delete objects using one of the following methods:

- Delete all objects with the specified prefix:

   ```bash
   aws --endpoint-url=https://storage.yandexcloud.net \
       s3 rm s3://bucket-name/path_style_prefix/ --recursive 
   ```
- Delete objects specified in the `--include` filter and skip objects specified in the `--exclude` filter:

   ```bash
   aws --endpoint-url=https://storage.yandexcloud.net \
       s3 rm s3://bucket-name/path_style_prefix/ --recursive \
       --exclude "*" --include "*.log"
   ```
- Delete objects one by one, running the following command for each object:

   ```bash
   aws --endpoint-url=https://storage.yandexcloud.net \
       s3 rm s3://bucket-name/path_style_prefix/textfile.txt
   ```

### Retrieve an object

   ```bash
   aws --endpoint-url=https://storage.yandexcloud.net \
       s3 cp s3://bucket-name/textfile.txt textfile.txt
   ```

