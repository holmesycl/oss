# Overview

By default, the billing method is pay-as-you-go after you activate OSS. For some billing items, you can purchase resource plans \(subscription\) to further minimize OSS costs. Subscription allows you to use resources only after you purchase resource plans. Resource plans are used to deduct fees incurred by resource usage. If the resources you use exceed the quotas of the resource plans, the additional resources are charged on a pay-as-you-go basis.

## Deduction rules of resource plans

The following table lists the resource plans supported by OSS and corresponding deduction rules of resource plans. A check sign \(√\) indicates that the corresponding operation applies to the resource plan. A cross sign \(×\) indicates that the corresponding operation does not apply to the resource plan.

|Resource plan|Deductible fee|Upgrade|Renew|Purchase multiple resource plans|
|-------------|--------------|-------|-----|--------------------------------|
|Standard locally redundant storage \(LRS\) plan|Fees for storage usage of Standard LRS: the fees incurred when you store Standard LRS objects in a bucket.|√|√|×|
|IA LRS plan|Fees for storage usage of IA LRS: the fees incurred when you store IA LRS objects in a bucket.|√|√|×|
|Storage capacity unit \(SCU\)|If you purchase an SCU that is in the same region as an OSS bucket, the SCU can be used to deduct the following fees: -   Fees for storage usage of Standard LRS
-   Fees for storage usage of Standard zone-redundant storage \(ZRS\)
-   Fees for storage usage of IA LRS
-   Fees for storage usage of IA ZRS
-   Fees for storage usage of Archive LRS
-   Fees for storage usage of ECS snapshots

**Note:**

-   If an OSS storage plan and an SCU are in the same region at the same time, the OSS storage plan is used to deduct the storage fees. If the storage plan is insufficient, the SCU can be used to deduct fees. For more information, see [Overview](/intl.en-US/Block Storage/Storage capacity units/Overview.md).
-   SCUs does not apply to the operations in this topic such as purchase, renewal, and upgrade. For more information, see [Create an SCU](/intl.en-US/Block Storage/Storage capacity units/Create an SCU.md).

|×|×|√|
|Downstream data transfer plan|Fees for outbound traffic over the Internet: the fees incurred when you browse or download data from OSS over the Internet.|×|√|√|

**Note:**

-   Billing items to which resource plans do not apply such as data processing, cross-region replication \(CRR\) traffic, requests, and object tagging, are charged on a pay-as-you-go basis.
-   For more information about billing items and methods, see [Overview](/intl.en-US/Pricing/Billing items and methods/Overview.md).
-   For more information about specifications and prices of resource plans, see[OSS Resource Plan](https://common-buy-intl.alibabacloud.com/?spm=5176.8465980.bucket-list.2.11df6765PslE4M&commodityCode=oss_bag_intl#/buy).

## Purchase resource plans

1.  Log on to the[OSS Resource Plan](https://common-buy-intl.alibabacloud.com/?spm=5176.8465980.bucket-list.2.11df6765PslE4M&commodityCode=oss_bag_intl#/buy) page.

2.  On the buy page, set parameters such as Plan Type, Region, Capacity, and Validity Period. Click **Buy Now**.

3.  Follow the purchase procedure to complete the payment.


## Upgrade resource plans

OSS allows you to upgrade resource plans. For more information, see [Upgrade resource plans](/intl.en-US/Pricing/Billing methods/Subscription/Upgrade resource plans.md).

## Renew resource plans

You can renew resource plans that are about to expire to prolong the subscription periods. For more information, see [Renew resource plans](/intl.en-US/Pricing/Billing methods/Subscription/Renew resource plans.md).

## Example of resource plans

A user purchasesa nationwide Standard LRS resource plan of 500 GB and a mainland China downstream data transfer plan of 100 GB.The resource usage in June includes:

-   China \(Hangzhou\)
    -   300 GB of Standard LRS objects
    -   110 GB of outbound traffic over the Internet
    -   100,000 API requests
-   China \(Shanghai\)
    -   200 GB of Standard ZRS objects that are stored
    -   100 GB of Standard LRS objects that are stored

The following table lists the usage details of resource plans.

|Region|Billing item|Usage|Deductible resource plan|Pay-as-you-go|
|------|------------|-----|------------------------|-------------|
|China \(Hangzhou\)|Storage usage of Standard LRS|300 GB|Standard LRS plan of 500 GB|None|
|Outbound traffic over the Internet|110 GB|Downstream data transfer plan of 100 GB to deduct traffic fees of 100 GB|10 GB|
|API requests|100,000|None|100,000|
|China \(Shanghai\)|Storage usage of Standard ZRS|200 GB|None **Note:** You cannot use the Standard LRS plan to deduct fees for storage usage of Standard ZRS.

|200 GB|
|Storage usage of Standard LRS|100 GB|Standard LRS plan of 500 GB|None|

## FAQ

-   When does a resource plan take effect?

    The resource plan takes effect immediately after the payment. However, overdue payments before you purchase the resource plan cannot be completed using the resource plan.

-   What do I do after the resource plan expires?

    If you fail to renew a resource plan after the resource plan expires, the additional resources are charged on a pay-as-you-go basis.

-   Can I request a refund for a resource plan?

    Yes, you can request a refund for a resource plan. For more information, see [How do I cancel resource plans?](/intl.en-US/Pricing/FAQ/How do I cancel resource plans?.md).

-   What do I do if the quota of the resource plan is exceeded?

    If the resources you use exceed the quota of the resource plan, the additional resources are charged on a pay-as-you-go basis.

-   Can I purchase multiple resource plans?
    -   No, you cannot purchase multiple storage plans.

        No, you cannot purchase multiple storage plans. Storage plans in the same region can be purchased only once in the same period of time. If you require a storage plan with a higher specification or longer duration, you can [upgrade](#section_nnt_zug_lsv) or [renew](#section_axy_bot_o4m) the existing storage plan.

    -   You can purchase and renew multiple downstream data transfer plans, but cannot upgrade the purchased plans.

