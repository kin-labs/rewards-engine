# **KRE 4.0 PROPOSAL**

The purpose of this document is to propose a complete new set of KRE rules. 

## Proposed by:  Freedom-Kin

## Abstract:
Before we can speak of a Kin **Ecosystem** we must first build a Kin **Economy** and to do so this proposal aims to go **back to  basic economics**. An ecosystem must be self-sustaining. If not then it is nothing more than an aquarium. As long as you feed your fish, maintain the temperature and circulate the water, the ecosystem will stay alive. Until now KRE has kept apps 'alive', but we need to think bigger. Apps should be able to stand on their own two feet and the KRE should help with that.

We aim for:
1. Keeping inflation under control
2. A simple and easy to understand KRE
3. More income for developers
4. Fair rewarding system
5. A system that is hard to game
6. A system that is sustainable in the long term
7. A system that is attractive to larger apps
8. Equal opportunities for all developers.


So let's start with some concepts that we will be using here.

## The Kin Economy
The Kin Economy consists of all apps and users that use Kin. 

## Economic Activity
You can have a street full of shops, all loaded with items, but if the street is empty and there are no buyers,  there is no economic activity.
Economic Activity it is the **FLOW OF MONEY** (Kin) that users send through all those apps. Without this flow of money there is no economy.

## The value of Kin
Hopefully someday in the future, when Kin is accepted everywhere as a means of payment, Kin may be a value in itself. Until then, everyone will express the value in fiat (USD/EUR). Adding value to the Kin Economy will, for the time being,  be measured in fiat. Unfortunately, it is what it is.

## A meaningful SPEND
If app X let you SPEND 1000 Kin as a condition for you to EARN 1100 Kin, then what is the meaning of this SPEND?  It's a symbolic SPEND. It's just a 100 Kin give away.

Within this proposal, the question of what a meaningful SPEND is will solve itself.

## Inflation
Inflation is the increase of money supply (Kin) without the underlying values increasing proportionally. 

A common mistake is to think that inflation only occurs when products become more expensive. However, rising prices is the **result** of inflation, not the **cause**.
Central Banks would like us to believe that. This way they can print a lot of money. The consequences often come much later and only then they call it inflation. Actual inflation is any dollar printed that has no real value to count for in return.


## The Kin Foundation's funds
The 6T Kin allocated to the KF is considered in this proposal as reserved tax money. This makes this fund public money and must be spend responsibly as such. Whenever a portion of this is spend, the community pays for it in the form of inflation. After all, more Kin comes into circulation.

As long as this release ensures that the value of the Kin economy increases, this is not a bad thing. It's tax money well spent.
When a government spends taxpayers' money building roads, this expenditure increases the value of the economy. Everyone can use those roads to function better within that economy. It is money well spent.

Compare this to a government that simply gives money away. More money comes into circulation without any economic added value being created.
This is the definition of inflation.

So with every release of the funds, we ask the question: How will this increase the value of the Kin economy?
If it doesn't, we may have to ask ourselves whether this is a smart spend.
Nothing is exclusively black or white, but it can serve as a rule of thumb.

## The KRE
In this proposal, the KRE is seen as a subsidy that is given for a specific purpose.  That goal can be, for example, to support a startup app or to reward a desired behavior, as long as it serves the growth of the Kin economy.
As the Kin economy matures this basic rule can increasingly be deviated from, but for now we must do everything we can to get a healthy economy. For now it means back to basics.


## What is the purpose of this KRE 4.0 version?
The goal is to go back to the basics of economic thinking.
We try to achieve the following:

1. KRE must ensure growth of the Kin economy.
2. KRE must aid new apps to get through the startup phase.
3. KRE should be an incentive for apps to stay in the Kin economy.
4. KRE rules should be simple to understand.


## What makes this proposal different?
To begin with, please forget everything about the Active User Balance (AUB) as if it doesn't exist.

**Why?**

In short it comes down to this. Economic Activity is **the FLOW of money** through the economy.  A system based on AUB rewards developers for keeping that money where it is....in the wallets.  Every SPEND the user makes lowers his balance.
That in turn can lower the KRE pay-out, and developers are not crazy.
Rewarding the AUB is killing Economic Activity...it hinders the FLOW of Kin.


## Everything you reward gets bigger
So the idea of this proposal is to basically reward generating SPENDS.
Not the number of SPENDS but the actual net VALUE of SPENDS. 


## What are net SPENDS?
If a user pays for something in the app we call that a SPEND.
The SPEND of the user is in fact the turnover of the developer.
For the purpose of this proposal, we will simply call this turnover SPENDS.
Developers Turnover = SPENDS.

Every business has costs connected to it's turnover like give aways, presents etc.
Apps have them too....we call them EARNS.
A developer can let you EARN a little Kin as an incentive to spend more time in his app or to attract more users. The EARNs for the users are costs for the developer.

His actual net turnover is the **SPENDS minus EARNS**, and is what we here call **net SPENDS**.

By rewarding these net SPENDS the developer is stimulated to generate more SPENDS then EARNS, which makes sense.

There is no economy in the world where a business that makes no money has any long lasting right of existence. What business gives away more money then customers spend?  Subsidizing such a business with public money would only drain the available funds.

However, if a philanthropist would like to do it as a hobby he is probably welcomed, but not with public money.

## Not rewarding EARNS?
Giving away money (Kin) is easy and it should not **need** to be rewarded.
Coming up with good SPEND opportunities is the hard part. It requires being inventive, staying on top of things, adjusting and taking risks.  That should be rewarded.


## KRE Rewards
The goal is to keep the KRE rules as simple as possible.
The numbers and percentage that will be mentioned are of course arbitrary. 
It's about the concept.

The proposal is to reward developers with a percentage of their net SPENDS.
They get 30% KRE reward on their everyday net SPENDS.
This with a maximum of 50,000,000 Kin per day.

It sounds a lot, but if an app would reach that 50,000,000 Kin reward they had a net turnover of  166,666,666 Kin on that given day. That would give the economy a nice push.
The code needed is real simple.

## Definitions and Code
```
Definitions

KRE%               =  percentage apps get rewarded with

Max_KRE            =  Cap on daily reward

Net_Spends         =  SPENDS minus EARNS

KRE_Payout         =  The final payout for app i


CODE

KRE% =  30

Max_KRE =  50,000,000

KRE_Payout = Net_Spends  *  KRE%  / 100

KRE_Payout = MIN( KRE_Payout , Max_KRE )
```

This is basically all the code needed.

Of course the KRE% can be tweaked.
Like in the first year a startup app could get 40%.
We propose that all apps be considered startups for 1 year, at implementation of this proposal, since they all need to adjust to generating SPENDS.

To qualify for KRE, each EARN and SPEND must be a direct transaction on the blockchain. EARNS should not be delayed.

```
Example:
If app X has 25,000,000 Kin in SPENDS, and it let users EARN 5,000,000 Kin, 
than its net SPENDS are 25,000,000 minus 5,000,000  = 20,000,000 Kin.

Its reward would be 20,000,000 x 30% = 6,000,000 Kin
If is was a startup, it would be  20,000,000 x 40% = 8,000,000 Kin (all apps should be considered startups the 1st year)
These rewards are calculated for every single day.

```

## Advantages
01. It is a very simple and easy to implement code.

02. Developers can compete for KRE by generating more SPENDS then EARNS.
This will drive the Kin economy.

03. By deducting the EARNS from the SPENDS all the gaming we have seen in earlier iterations of the KRE will be prevented. 

04. The effect will be that less Kin will be given away for free by developers.
Kin will actually be bought, either on exchanges or with a buy module in the app.

05. This will bring in more actual value in the Kin economy and that must have an effect on the Kin price.

06. KRE funds will no longer be just given away for free without adding value to the Kin economy. It's now public money well spent.

07. There are no extra factors for a KRE score, so nothing else can be gamed.

08. Developer rewards do not depend on the performance of other apps.
They know exactly how much they will get.

09. We also solve the problem on how much we should raise the daily available KRE if more and more apps join the economy. This amount will adjust automatically to the number of apps in the economy.

10. If the price of Kin goes up a lot or the total KRE release gets to high we can lower the daily max and or the percentage.
Maybe it can be adjusted every 6 or 12 months.

11. Every developer has the same opportunity as larger apps.
There is no competition needed for the KRE.

12. Since there is no AUB to defend there is no reason for an app to be an island in the system and hinder tourism.

13. Additional benefit is that if we keep the KRE % lower than the taxes developers  have to pay to local governments it is not interesting for anyone to artificially raise their SPENDS with all kinds of tricks. If they do than they pay more taxes than they get from the KRE.

## What if my app doesn't generate any SPENDS?
Apps that don't generate spends can't compete for the KRE.
However, such an app might have value for the Kin Community.
Think of a Wallet, Buy module or Tipping app, which might generate no SPENDS but is VERY useful for the community. 

I suggest that for those apps a second fund will be created.
Apps can apply for a grant and a periodical amount of Kin for maintenance.
It will be evaluated on a case by case base.

## Why is this the smart thing to do?
Suppose you let wallets have part of the KRE and it turns out to be very lucrative.  In no time we will see many wallets arise and we get the same as with staking.  Developers will start making wallets...if they don't, they can't compete, and again we have a race to the bottom.

In fact, if wallets are covered by the KRE it would mean that every withdrawal must be seen as a SPEND, which it clearly is not. 

By evaluating them on a case by case basis you can say okay, we now have enough of this kind of apps. We are no longer subsidizing new ones with public money. 

The KRE is standard for apps that give the economy a push forward.
Sales (spends) have that effect but many apps don't have them.  They might be fun but if they are not funny enough for users to be willing to pay for it, then they don't push the economy forward.  So, let the KRE be used for what it is intended for and let the secondary fund take care of the rest.
 

## How will a system based upon net SPENDS help grow the Kin Economy?

**Basic economics**

01. By rewarding developers to generate more SPENDS then EARNS **Kin starts to flow** through the economy.  KRE will still be increasing the circling supply of Kin, but now it will actually do what it's supposed to do, creating **Economic Activity**.
Demand will become larger because less free Kin will be given away by apps. 


02. Users will actually have to **buy Kin**, either on exchanges or in-app at buy modules.

03. Now the benefits of the **buy module** will be fully utilized.
The user base will grow because they don't have to first go to exchanges to get Kin, which can be a very scary thing to do, but they can buy Kin right in the app where they want to spend it.

04. Apps are benefiting from **two sources of income**, their own generated SPENDS **and** the KRE reward. 

05. Since developers have **no need to protect the AUB** from getting lower, they can come up with meaningful SPENDS.    

06. No more need for 3 mandatory SPENDS per 30 days.

07. No need for the developer to limit withdrawals to just one day a month. 

08. No need to lock up user balances to e.g. 100,000 Kin.

09. No need to hinder tourism because they don't need to protect their AUB.
 
10. No more irritation of users which leads to a **better user experience.** 

11. It will save the Kin Foundation a lot of unnecessary transaction fees if there is no need for 3 mandatory spends. 

12. It's an easy to understand system. Just make a profit like you would in a regular business and get an extra bonus from the KRE.

13. Users will still be able to EARN some Kin, but maybe not as much as before.
The benefit is that **we will get inflation under control**. The price of Kin will go up and that is good for developers, investors and users. 

14. More **meaningful SPEND opportunities** lead to more USERS, leads to more $$ value, leads to more profit for developers, leads to bigger and more apps.
The Kin Economy will grow.  Large apps with millions of users might get interested in joining and the snowball gets bigger.

The Kin Economy will eventually become a **self-sustaining ecosystem**.

