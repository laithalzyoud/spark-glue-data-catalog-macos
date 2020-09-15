# spark-glue-data-catalog-macos

This project builds Apache Spark in way it is compatible with AWS Glue Data Catalog on macOS.

It was mostly inspired by awslabs' Github project [awslabs/aws-glue-data-catalog-client-for-apache-hive-metastore][1] and its various issues and user feedbacks.

⚠️ this is neither official, nor officially supported: use at your own risks!

## Usage prerequisites

### AWS credentials

You must provide AWS credentials via environment variables in `/conf/spark-env.sh` for spark to be able to access AWS APIs: `AWS_ACCESS_KEY_ID`, `AWS_SECRET_ACCESS_KEY` and `AWS_DEFAULT_REGION`.

## Dependencies

To build spark with glue locally using the provided script, you should have the following installed:
1. git -> `brew install git`
2. wget -> `brew install wget`
3. JDK8 -> https://www.oracle.com/java/technologies/javase/javase-jdk8-downloads.html and don't forget to add `export JAVA_HOME=/Library/Java/JavaVirtualMachines/jdk1.8.0_261.jdk/Contents/Home` to your bash/zsh profile in `~/.bash_profile` or `~/.zprofile` and confirm with `java -version`
4. Maven:
  * `cd ~ && wget https://downloads.apache.org/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz && tar -xvf apache-maven-3.6.3-bin.tar.gz && sudo mv apache-maven-3.6.3 /opt/maven`
  * Add the following to your bash/zsh profile in `~/.bash_profile` or `~/.zprofile`:
    ``` 
    export M2_HOME=/opt/maven
    export PATH=$M2_HOME/bin:$PATH
    ```
  * `source ~/.bash_profile`
  * Verify with `mvn -version`
5. gnu-sed -> `brew install gnu-sed`

### Build spark-glue-data-catalog locally

To build spark with glue support run `./build-spark.sh`

## References

- [Source code for the AWS Glue Data Catalog client for Apache Hive Metastore is now available for download](https://aws.amazon.com/about-aws/whats-new/2019/02/source-code-for-the-aws-glue-data-catalog-client-for-apache-hive-metatore-is-now-available-for-download/) - Feb 4, 2019 announcement
- [Using the AWS Glue Data Catalog as the Metastore for Hive](https://docs.aws.amazon.com/emr/latest/ReleaseGuide/emr-hive-metastore-glue.html) documentation
- Github's [awslabs/aws-glue-data-catalog-client-for-apache-hive-metastore][1] project

[1]: https://github.com/awslabs/aws-glue-data-catalog-client-for-apache-hive-metastore
