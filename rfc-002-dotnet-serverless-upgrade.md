# Plan to upgrade to .NET 8

## Summary

All our .NET codebases on AWS Lambda run .NET v6 or earlier, which is unsupported. After March 2025 we won't be able to modify or recovery any of these services, so there's a big risk if we don't upgrade urgently. Upgrading .NET depends on us _also_ upgrading or migrating away from Serverless Framework, which carries a new cost.

We think a hybrid approach set out below allows us to manage the risk while minimising cost and giving us the opportunity to ensure we're using the best tools available to us.

## Problem

Currently all our services built with .NET are running version 6 or lower.

- .NET 6 went out of support [on the 12th of November](https://dotnet.microsoft.com/en-us/platform/support/policy/dotnet-core).  
- [AWS will deprecate .NET 6 on the 20th of December (2024)](https://docs.aws.amazon.com/lambda/latest/dg/lambda-runtimes.html), blocking new Lambda creation from February 28th and updates from March 31st 2025.  
- Serverless v3 doesn't support the `dotnet8` runtime[^1].  
- We can't currently upgrade to Serverless v4 because there's a licensing change which would require us to pay (though it's not clear how much it would actually cost us)[^2]. Aside from the fact that there won't be any further .NET 6 security updates, I think this means that we have until the end of February before we're unable to recover **any** of our serverless .NET deployments, and until the end of March before we're unable to make any changes to them.Does that sound right, or have I missed something key

Upgrading to .NET 8 is blocked by our use of Serverless Framework without a paid plan. There are a few options available to resolve this

## Serverless Framework options

1. Upgrade to Serverless Framework 4 and begin paying. This is a "pay as you go" service based on the number of lambda instances (i.e. lambdas per region per stage). This is the most straightforward option, however it's difficult to get an accurate total cost for all of Hackney without assessing every service individually.

2. Migrate away from Serverless Framework to a free development framework such as [AWS Serverless Application Model](https://docs.aws.amazon.com/serverless-application-model/) or [LocalStack](https://www.localstack.cloud/)[^3].

3. Migrate from Serverless Framework to a barebones Infrastructure as Code deployment model without a development framework (e.g. only Terraform). This isn't likely to be a viable route for our actively developed services, but might be suitable for older ones we update infrequently.

## Proposal

In order to focus our efforts on the .NET 8 upgrade, we need to minimise the effort we spend on Serverless Framework and it's alternatives. It's imperative that we make a start on the upgrade soon in order to have enough time  to work through dependency upgrades and challenges before AWS blocks updates to .NET 6 lambdas for _at least_ the critical services. However this is also an opportunity to investigate alternatives in a controlled way.

To balance these we'll take a hybrid approach to upgrades:

- For all critical systems we will upgrade to Serverless v4 on the pay as you go model and prioritise .NET 8 upgrades across all our engineering teams, with the support of Product and Delivery.

- In parallel, we'll trial migrating one actively developed system to Terraform with LocalStack to evaluate a free & open source alternative to Serverless.
  > ℹ️ If there are other options we're excited to explore, add them here!

- Once critical systems are upgraded, we will make a decision for non-critical systems based on the tested alternative and projected costs. If the strategic decision is to migrate away from Serverless Framework, we would aim to complete this for the critical services (to align everything on a single stack) before the end of 2025.

We believe this approach minimises the initial costs while unblocking the .NET 8 upgrade _and_ sets a path to make a stratetic decision early in 2025. It allows temporary fragmentation of approaches while we evaluate the best option – this sounds like a downside but it enables us to significantly reduce the short-term risk without committing to unknown long-term costs.

## Footnotes

[^1]: Because it was touted as [a new feature in v4](https://github.com/serverless/serverless?tab=readme-ov-file#new-features-in-v4) and doesn't appear in the [v3 changelog](https://github.com/serverless/serverless/blob/v3/CHANGELOG.md).

[^2]: [Serverless Framework pricing page](https://www.serverless.com/pricing) describes a per-instance cost with per-invocation costs if we start using Serverless Dashboard. We don't have good data on either instance of invocation counts across our AWS accounts, as there are many other lambdas aside from Serverless-managed ones.

[^3]: LocalStack has an open-source community version and [paid subscription tiers](https://www.localstack.cloud/pricing). We can use the free version, though it lacks some AWS services.
