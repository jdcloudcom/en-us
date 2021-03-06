# Metering and Billing

[How OSS is billed? ](Billing#user-content-1)

[Does OSS has a free quota? ](Billing#user-content-2)

[Why is it in arrears (deducted) within the free quota? ](Billing#user-content-3)

[Is the traffic generated by accessing OSS via Intranet free? ](Billing#user-content-4)

[How to view a bill? ](Billing#user-content-5)

[Can the OSS Console access an object and download an object after being stopped due to arrearage? ](Billing#user-content-6)

[When will OSS release resources after being stopped due to arrearage? ](Billing#user-content-7)

[How to stop the billing by OSS? ](Billing#user-content-8)

[How to search surplus of a resource package (pay-in-advance resource package, free quota)? ](Billing#user-content-9)

[How to cancel a resource package? ](Billing#user-content-10)

------

<div id="user-content-1"></div>

#### How OSS is billed?

The costs of OSS are composed of five parts: Storage cost, traffic cost, request cost, data retrieval cost, cloud data processing cost;

Adopt the quantity-based pay-as-you-go billing mode, which pushes the bill on a daily basis according to the actual consumption of user and collect charge for the previous day as per the bill per day;

For information on OSS billing items, billing rules and the like, please refer to [Billing Rules](https://docs.jdcloud.com/object-storage-service/billing-rules).

<div id="user-content-2"></div>

#### Does OSS have a free quota?

We provide OSS users with certain standard storage capacity and free quota of standard storage requests. The free quota will be distributed in the form of resource package. When the OSS of JD Cloud & AI is subscribed by the user, the system will automatically distribute the free quota to the user account. A resource package will be distributed to each normal user account per month. For details, please refer to [Free Quota](https://docs.jdcloud.com/object-storage-service/free-tier-for-oss).

<div id="user-content-3"></div>

#### Why is it in arrears (deducted) within the free quota?

A resource package containing free quota can be used to deduct part of the costs incurred during your use of OSS, but it cannot used to deduct all of the costs. So, the reasons for arrearage (deduction) within the free quota may be:

1. Other charging items: The OSS costs consist of storage cost, traffic cost, request cost, data retrieval cost, and cloud data processing cost. At present, the OSS free quota can only provide standard storage capacity and standard storage requests with certain quota, which can only be used to deduct the costs for standard storage type of storage and requests. Other billing items: Costs such as traffic cost, data retrieval cost, and cloud data processing cost are billed by quantity.
2. Cost for using resources exceeding the quota. For example, if you have 10GB free standard storage capacity and the actual storage exceeds the free quota 10GB, then the excessive part will be billed by storage.

Check consumption details of your bucket. For details, please refer to [View Bill](https://docs.jdcloud.com/object-storage-service/check-bill)

<div id="user-content-4"></div>

#### Is the traffic generated by accessing OSS via Intranet free?

Traffic generated by accessing OSS via Intranet is free; traffic generated by downloading data from OSS to local end via Internet and traffic generated by downloading OSS data via CDN are billed as per fixed unit price.

<div id="user-content-5"></div>

#### How to view a bill?

You can view the information of costs incurred by using OSS in your account through the Console Cost Center. For detailed search method, please refer to [View Bill](https://docs.jdcloud.com/object-storage-service/check-bill).

<div id="user-content-6"></div>

#### Can the OSS Console access an object and download an object after being stopped due to arrearage?

You cannot conduct any operation with OSS after it is stopped due to arrearage. The OSS will automatically stop when the time of arrearage exceeds 24 hours and your data can be continually kept for 60 days. During this period, if your account balances after renewal are not greater than or equal to 0, the data will be destroyed. For more information related to arrearage, please refer to the arrearage rules in [Billing Overview](https://docs.jdcloud.com/object-storage-service/billing-overview).

<div id="user-content-7"></div>

#### When will OSS release resources after being stopped due to arrearage?

If you do not make up the arrears within 60 days, you will be regarded as giving up OSS; your bucket will be reclaimed; the data in the bucket will be cleared and cannot be recovered. If you recharge to make up the arrears within 60 days from the begin date of your arrearage, the service will automatically enabled for use.

<div id="user-content-8"></div>

#### How to stop the billing by OSS?

The stopping service by one-click may affect businesses of customers, so OSS doesn't provide this function at the moment.

- If you do not want to use OSS any more, you can delete all objects under the bucket and then delete the bucket, so there will not be deduction in the next billing period (OSS is billed by usage and one bill is issued each day. We recommend you automatically delete objects in batch through [Set Object Life Cycle](https://docs.jdcloud.com/object-storage-service/lifecycle).
- If you don't need to use data on OSS for a long time (more than 30 days) and you don't want to delete the data, we recommend you convert the standard storage to infrequent access storage or archival storage, which can save you about 30%~80% costs. For details, please refer to [Storage Type Introduction](https://docs.jdcloud.com/object-storage-service/storageclass-overview) and [Price Overview](https://docs.jdcloud.com/object-storage-service/price-overview).

<div id="user-content-9"></div>

#### How to search surplus of a resource package (pay-in-advance resource package, free quota)?

Please log in and access [Resource Package Overview](https://uc.jdcloud.com/account/accesskey) of the Management Console to view details.

<div id="user-content-10"></div>

#### How to cancel a resource package?

If you accidentally purchase a wrong resource package, for example, choosing the wrong effective region, period of validity (or purchase duration), specification, etc., you can contact the after-sales technicians to cancel the purchased resource package.

Applicable condition: You can apply for cancellation when your resource package is unused.
