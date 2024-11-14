# Salesforce SmartStore

One can use Salesforce Mobile SDK and utilise SmartStore to get local storage solution designed especially for offline
usage.
SmartStore provides the primary features of non-relational desktop databases like 
- data segmentation
- indexing
- querying
- along with caching for offline storage.

## What is SmartStore?
- SmartStore is a NoSQL-like, lightweight, encrypted, and secure storage system provided by the Salesforce SDK.
- Primary usage of SmartStore is as a powerful tool for offline data management.
- SmartStore is a robust offline data storage and synchronization solution provided by the Salesforce Mobile SDK.
- It enables mobile apps to operate seamlessly, even when they are offline, by storing data locally on the device and synchronizing it with a remote server when connectivity is restored.

So SmartStore provides
- Data Storage
- Offline Functionality
- Data Synchronization
- Security
- Performance Optimization
- Querying and Filtering
- Conflict Resolution

## What is the underlying database for SmartStore?
SQLite is the underlying database for SmartStore.

## What are SmartStore Soups?
Soups can be thought of as tables. One can define as many as soups as required.
- Soups are logical collections into which SmartStore stores offline data.
- A SmartStore soup represents a single table in the underlying SQLite database, or store.
- Soup typically maps to a standard or custom Salesforce object.
- Soups further contains elements, where each element is a JSON object, kind of mirroring a single database row.


## Prompts
```
Give code example for scenario and explain how to handle scenario for an ios app to download all SalesForce objects and
save on local database when user logs into app so that all data is available for offline usage.
```