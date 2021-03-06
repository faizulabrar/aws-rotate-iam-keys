# aws-rotate-iam-keys
Rotate your IAM Keys to be in compliance with security best practices. AWS talks about rotating your keys every 30, 45, or 90 days. But who has the time to make their own script and remember to do that? I did. And security is easier when its less than 3 lines that you need to copy + paste to be secure. Now it's easy to rotate your IAM credentials nightly and wake up with more security than the day before.

## Installation
AWS Rotate IAM Keys is supported by all major platforms.

### Ubuntu

```
sudo add-apt-repository ppa:rhyeal/aws-rotate-iam-keys
sudo apt-get update
sudo apt-get install aws-rotate-iam-keys
```

### MacOS

```
brew tap rhyeal/aws-rotate-iam-keys https://github.com/rhyeal/aws-rotate-iam-keys
brew install aws-rotate-iam-keys
```
Requires [Homebrew](https://brew.sh/) to install. I am hoping to be included in Homebrew Core soon!

***IMPORTANT:*** You must install your own cron job for automated key rotation. [Instructions here](https://github.com/rhyeal/aws-rotate-iam-keys#macos-1) or scroll down to `Additional Cron Instructions` below.

### Other Linux

```
wget
deb -i
```

### Windows

[Click here](#) to download the executable installer.

## Features

AWS Rotate IAM Keys is simple and powerful. There aren't too many features other than rotating keys for a single profile or multiple profiles. The power comes from multiple cron jobs daily that can rotate multiple sets of keys automatically.

### Improvements / Issues

* Currently, AWS Rotate IAM Keys will only work with a single computer. Rotating keys on a desktop and a laptop for the same IAM user will lead to invalid keys.
* AWS Rotate IAM Keys takes an opinionated view that you should only have 1 active key at a time. It might not work with IAM users that have 2 keys active at a time.

## Documentation

To rotate your default profile manually:

```
$ aws-rotate-iam-keys
Making new access key
Updating profile: default
Made new key AKIAIOSFODNN7EXAMPLE
Key rotated
```

To rotate a specific profile in your `~/.aws/credentials` file:

```
$ aws-rotate-iam-keys --profile myProfile
$ aws-rotate-iam-keys -p myProfile
```

To rotate multiple profiles *with the same key*:

```
$ aws-rotate-iam-keys --profiles myProfile,myOtherProfile
```

The result of the above script is that both `myProfile` and `myOtherProfile` will have the **same access and secret keys** in your `~/.aws/credentials` file.

To rotate multiple profiles with their own keys:

```
$ aws-rotate-iam-keys --profile myProfile
$ aws-rotate-iam-keys --profile myOtherProfile
```

The result of the above script is that `myProfile` and `myOtherProfile` will have **different** access and secret keys in your `~/.aws/credentials` file.

## Additional Cron Instructions
For some operating systems, you need to install your own cron schedule. This is
due to the fact that some operating systems do not allow installed programs
via the package managers selected to create their own cron schedules.

### MacOS

MacOS does not allow programs to modify the crontab when installing via Homebrew. Unfortunately, this means that MacOS users will need to copy/paste a cron job into their crontab. Here's how to do that:



### Windows

## On the Web!
Visit us on the web at [aws-rotate-iam-keys.com](https://aws-rotate-iam-keys.com) for full installation instructions
in a snazzy single-page UI. It's basically this README with some colors.
