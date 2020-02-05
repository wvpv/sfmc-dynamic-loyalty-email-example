# SFMC-DYNAMIC-LOYALTY-EMAIL-EXAMPLE

# Purpose

Create a simple architecture for a dynamic, modular email template in Salesforce Marketing Cloud.

# Steps to use

1. Review architecture/mapping image - [email-sample-mapping.png](https://github.com/wvpv/sfmc-dynamic-loyalty-email-example/blob/master/email-sample-mapping.png)
2. Create required Data Extensions

    - **Example-LoyaltySubscriberReferrals** - Subscribers referred by Loyalty Subscribers
        + SubscriberKey, Text(254)
        + ReferralSubscriberKey, Text(254)
        + ReferralName, Text(100)
        + ReferralDate, Date

    - **Example-LoyaltySubscribers** - Your primary sending and preview audience
        + SubscriberKey, Text(254), Primary Key, sendable field
        + EmailAddress, EmailAddress
        + FirstName, Text(50)
        + DiscountPct, Decimal(4,2)
        + ReferralCode, Text(36)
        + ReferralLink, Text(300)

    - **Example-LoyaltySubscribersDemographic** - Demographic data related to each Loyalty Subscriber
        + SubscriberKey, Text(254)
        + Language, Text(15)


3. Upload sample data into each Data Extension

    - **LoyaltySubscribers** - `example-LoyaltySubscribers.csv`
    - **LoyaltySubscribersDemographic** - `example-LoyaltySubscriberDemographics.csv`
    - **LoyaltyReferrals** - `Example-LoyaltySubscriberReferrals.csv`

4. Create Blocks in Content Builder using the following HTML files

    - Template - `example-template.html`
        + Type: `HTML Paste`
        + Name: `Example-Template`
        + Customer Key: `Example-Template`
    - Init - `example-init.html`
        + Type: `Code Snippet`
        + Name: `Example-Init`
        + Customer Key: `Example-Init`
    - Header - `example-header.html`
        + Type: `HTML`
        + Name: `Example-Header`
        + Customer Key: `Example-Header`
    - Body - `example-body.html`
        + Type: `HTML`
        + Name: `Example-Body`
        + Customer Key: `Example-Body`
    - Footer - `example-footer.html`
        + Type: `HTML`
        + Name: `Example-Footer`
        + Customer Key: `Example-Footer`
    - LoyaltyReferrals - `example-loyaltysubscriberreferrals.html`
        + Type: `HTML`
        + Name: `Example-LoyaltySubscriberReferrals`
        + Customer Key: `Example-LoyaltySubscriberReferrals`

5. Create a new email definition

    - Type: `Template`
    - Template: `Example-Template`
    - Drag each saved element to email as indicated in mapping diagram

6. Preview email against `Example-LoyaltySubscribers` data extension
7. If you're satisfied with the results, set the `@debug` value to `0` in the init block.