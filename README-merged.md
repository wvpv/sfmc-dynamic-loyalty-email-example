# SFMC-DYNAMIC-LOYALTY-EMAIL-EXAMPLE

# Purpose

Create a simple architecture for a dynamic, modular email template in Salesforce Marketing Cloud.

# Steps to use

1. Review architecture/mapping image - [email-sample-mapping.png](https://bitbucket.org/wvpv/sfmc-dynamic-loyalty-email-example/raw/3fcdb68894d1c38238f8c7ed581bcdd1fe59027d/email-sample-mapping.png)
2. Create required Data Extensions

    - **LoyaltySubscribers** - Your primary sending and preview audience

        ```
        SubscriberKey, Text(254)
        EmailAddress, EmailAddress
        FirstName, Text(50)
        DiscountPct, Decimal(4,2)
        ReferralCode, Text(36)
        ReferralLink, Text(300)
        ```

    - **LoyaltySubscribersDemographic** - Demographic data related to each Loyalty Subscriber

        ```
        SubscriberKey, Text(254)
        Language, Text(15)
        ```

    - **LoyaltyReferrals** - Subscribers referred by Loyalty Subscribers

        ```
        SubscriberKey, Text(254)
        ReferralSubscriberKey, Text(254)
        ReferralName, Text(100)
        ReferralDate, Date
        ```

3. Upload sample data into each Data Extension

    - **LoyaltySubscribers** - `example-LoyaltySubscribers.csv`
    - **LoyaltySubscribersDemographic** - `example-LoyaltySubscriberDemographics.csv`
    - **LoyaltyReferrals** - `example-LoyaltyReferrals.csv`

4. Create Blocks in Content Builder using the following HTML files

    - Template - `example-template.html`
        + Name: `Example-Template`
        + External Key: `Example-Template`
    - Init - `example-init.html`
        + Block type: `Code`
        + Name: `Example-Init`
        + External Key: `Example-Init`
    - Header - `example-header.html`
        + Block type: `HTML`
        + Name: `Example-Header`
        + External Key: `Example-Header`
    - Body - `example-body.html`
        + Block type: `HTML`
        + Name: `Example-Body`
        + External Key: `Example-Body`
    - Footer - `example-footer.html`
        + Block type: `HTML`
        + Name: `Example-Footer`
        + External Key: `Example-Footer`

5. Create a new email using the Example Template
    - Drag each saved element to email as indicated in mapping diagram
6. Preview email against `LoyaltySubscribers` data extension
7. If you're pleased with the results, set the `@debug` value to `0` in the init block.