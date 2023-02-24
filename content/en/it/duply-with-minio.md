---
title: Duply with MinIO
---

## MinIO Configuration
Step 1: Create bucket without versioning and locking. Quota is also not needed.

Step 2: Create "read only policy" for backup account. Replace BUCKET-NAME with
your bucket name from step 2.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:GetBucketLocation",
                "s3:GetObject",
                "s3:ListBucket",
                "s3:PutObject"
            ],
            "Resource": [
                "arn:aws:s3:::BUCKET-NAME/*"
            ]
        }
    ]
}
```

Step 3: Create user. Same name as BUCKET-NAME. Assign an password and the policy from step 2.

## Create GnuPG Key for Encryption
- `gpg --expert --full-generate-key`
- use your password manager to generate a passphrase so you have it for the last step
- select "ECC (sign and encrypt)" (which is the default) for kind of key
- select "Curve 25519" (which is the default) for elliptic curve
- select "0" for "key does not expire"
- Real Name: "Duply Backup BUCKET-NAME"
- Mail: none
- Comment: none
- provide passphrase from first step

## Install and Config of Duply
- Mac: `brew install duply`
- execute `duply BUCKET-NAME create`
- edit exclude
- edit conf

```
GPG_KEY='KEY-FINGERPRINT'
GPG_PW='KEY-PASSPHRASE'
GPG_OPTS='--pinentry-mode loopback --no-throw-keyids'
TARGET='boto3+s3:///BUCKET-NAME/'
SOURCE='/'
export AWS_ACCESS_KEY_ID='BUCKET-NAME'
export AWS_SECRET_ACCESS_KEY='MINIO-USER-PASSWORD'
MAX_FULL_BACKUPS=12
MAX_FULLS_WITH_INCRS=6
MAX_FULLBKP_AGE=1M
DUPL_PARAMS="$DUPL_PARAMS --full-if-older-than $MAX_FULLBKP_AGE "
DUPL_PARAMS="$DUPL_PARAMS --s3-endpoint-url https://s3.MINIO-URL"
```

- add `ulimit -n 1024` to `.bash_profile`
- edit `.gnupg/gpg-agent.conf` and add `allow-loopback-pinentry`

## Backup
- copy revoke key `cp ~/.gnupg/openpgp-revocs.d/FINGERPRINT.rev ???`
- fix group
- zip or tgz and backup
