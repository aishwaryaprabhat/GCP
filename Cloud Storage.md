# Cloud Storage

## Overview
- Create buckets to store data
- Buckets are globally unique
        - Name (globally unique)
        - Location
        - Storage Class

### Storage Classes
- Multi-regional - frequent access from anywhere in the world
- Regional - frequent access from specific region
- Nearline - accessed once a month at max
- Coldline - accessed once a year at max


## Multi-regional
- Most expensive
- Frequently accessed hot objects such as serving website content, interactive workloads or mobile and gaming applications
- Highest availability of the storage classes
- Geo-redundant - Cloud storage stores your data redundantly in at least two regions separated by at least 100 miles within the multi-regional location of the bucket

## Regional Storage
- Appropriate for storing data that is used by Compute Engine instances
- Better performance for data-intensive computations as opposed to storing your data in a multi-regional location

## Nearline Storage
- Slightly lower availability
- 30-day minimum storage duration
- Data you plan to read or modify on average once a month or less
- There are access charges

## Coldline Storage
- Unlike other cold storage services, same throughput and latency (not slower than other options)
- Data access costs
- 90 day minimum storage duration
- High per operation costs
- Infrequently accessed data such as legal or regulatory data


## Working with Storage
- XML and JSON APIs
- CLI (gsutil)
- GCP console
- Client SDK

## Domain-Names Buckets
- Cloud storage considers bucket names that contain dots to be domain names
- MUst be syntatically valid DNS names
- Must be a valid domain name

## Review

1) What are the 4 classes of storage buckets?
