**KRE 4.0 PROPOSAL**

This proposal will be completely different from what we have seen from previous KRE versions.

The aim of this paper is to make it so that everyone can understand it. All concepts will be explained, possibly with examples. That makes it a little longer to read, but that is the price for transparency.

There have been several versions of the KRE. The former were based on rewarding the number of transactions and the latter mainly on rewarding the height of balances in user wallets.

This proposal aims to go back to the basics of economics. So let&#39;s start with some concepts that we will use here.

**The Kin Economy**

The Kin Economy consists of all apps and users that use Kin.

**Economic Activity.**

You can have a street full of shops, all full of items, but if the street is empty, no buyers, there is no economic activity.

Economic Activity it is the _flow of money_ (Kin) that users send through all those apps. Without this flow of money there is no economy.

**The value of Kin.**

Hopefully someday in the future, when Kin is accepted everywhere as a means of payment, Kin may be a value in itself. Until then, everyone will express the value in fiat (USD/EUR). Adding value to the Kin Economy will, for the time being, be measured in fiat. Unfortunately, it is what it is.

**A meaningful SPEND.**

If app X let you SPEND 1000 Kin in order for you to EARN 1100 Kin, then what is the meaning of this SPEND? It&#39;s a symbolic SPEND. It&#39;s just a 100 Kin give away.

Within this proposal, the question of what a meaningful SPEND is will solve itself.

**Inflation**

Inflation is the increase of money supply (Kin) without the underlying values increasing proportionally.

A common mistake is to think that inflation only occurs when products become more expensive. However, the increase of prices is the result of inflation, not the cause.

Central Banks would like us to believe that. This way they can print a lot of money. The consequences often come much later and only then they call it inflation. Actual inflation is any dollar printed that has no real value to count for in return.

**The Kin Foundation&#39;s funds**

The 6T Kin allocated to the KF is considered in this proposal as reserved tax money. This makes this fund public money and must be spend responsibly as

such. Whenever a portion of this is spend, the community pays for it in the form of inflation. After all, more Kin comes into circulation.

As long as this release ensures that the value of the Kin economy increases, this is not a bad thing. It&#39;s tax money well spent.

When a government spends taxpayers&#39; money building roads, this expenditure increases the value of the economy. Everyone can use those roads to function better within that economy. It is money well spent.

Compare this to a government that simply gives money away. More money comes into circulation without any economic added value being created. This is the definition of inflation.

So with every release of the funds, we ask the question: How will this increase the value of the Kin economy?

If it doesn&#39;t, we may have to ask ourselves whether this is a smart spend. Nothing is exclusively black or white, but it can serve as a rule of thumb.

**The KRE**

In this proposal, the KRE is seen as a subsidy in the form of a gift that is given for a specific purpose. That goal can be, for example, to support a startup app or to reward a desired behavior, as long as it serves the growth of the economy. As the Kin economy matures, this basic rule can increasingly be deviated from, but for now we must do everything we can to get a healthy economy. For now it means back to basics.

**What is the purpose of this KRE 4.0 version?**

The goal is to go back to the _basics of economic thinking_.

We try to achieve the following:

1. KRE must ensure growth of the Kin economy.

2. KRE must aid new apps to get through the startup phase.

3. KRE should be an incentive for apps to stay in the Kin economy. 4. KRE rules should be simple to understand.

**Let&#39;s start with the proposal.**

To begin with, please forget everything about the Active User Balance (AUB) as if it doesn&#39;t exist.

**Why?**

In short it comes down to this. Economic Activity is **the FLOW of money** through the economy. A system based on AUB rewards developers for keeping that money where it is....in the wallets. Every SPEND the user makes lowers his balance. That in turn lowers the KRE pay-out, and developers are not crazy. Rewarding the AUB is killing Economic Activity...it hinders the FLOW of Kin.

**Everything you reward gets bigger.**

So the idea of this proposal is to basically reward generating SPENDS. Not the number of SPENDS but the actual net VALUE of SPENDS.

**What are net SPENDS?**

If a user pays for something in the app we call that a SPEND.

The SPEND of the user is in fact the turnover of the developer.

For the purpose of this proposal, we will simply call this turnover SPENDS. Developers Turnover = SPENDS.

Every business has costs, like marketing, pay checks, give aways, etc. Apps have them too....we call them EARNS.

An app can let you EARN a little Kin as an incentive to spend more time in his store or attract more customers. The EARNs for the users are the costs for the developer.

His actual net turnover is the **SPENDS minus EARNS** , and is what we here call **net SPENDS**.

By rewarding these net SPENDS the developer is stimulated to generate more SPENDS then EARNS, which makes sense.

There is no economy in the world where a business that makes no money has any long lasting right of existence. What business gives away more money then customers spend? Subsidizing such a business with public money would only drain the available funds.

However, if a philanthropist would like to do it as a hobby he is probably welcomed, but not with public money.

**Not rewarding EARNS?**

Giving away money (Kin) is easy and it should not **need** to be rewarded. Coming up with good SPEND opportunities is the hard part. It requires being inventive, staying on top of things, adjusting and taking risks. That should be rewarded.

**Rewards**

What we propose is that the developer gets rewarded for **his part** of the total net SPENDS of all apps combined. If all apps combined have a total of 1000 Kin SPENDS and the one app has 100 Kin SPENDS then he gets **1000 / 100 = 10%** of the total available KRE.

Now, this is the basic principle, but not everything.

There should be a cap for a max pay-out or else one app could become so big that it gets a monopoly.

There could also be a correction for the amount of accounts an app brings into the Kin economy (DAS).

In fact the pay-out can be adjusted by every metric that is deemed important. Some examples will be given later on.

**Some definitions**

KRE\_score = The basis for the final payout calculation for app i. it starts off with the net SPENDS and will be adjusted by some parameters.

Total\_spends = The total net SPENDS of all apps combined. Total\_KRE = Total available KRE for that day.

KRE\_payout = The final payout for app i.

**Final Formula:**

**IF KRE\_score \&gt; 0 THEN**

**KRE\_payout = Total\_KRE / Total\_spends \* KRE\_score**

Explanation Final Formula

**Total\_KRE / Total\_spends** gives you the worth of every single spent Kin in proportion with the Total available KRE.

The app is eligible to **KRE\_score** times that amount.

If **KRE\_score** \&lt;1 then the app had no net spends and is not eligible for KRE.

…........................................

Before you enter the Final Formula you can tweak the **KRE\_score** with every metric you want.

**Example 1:**

To prevent 1 or 2 apps from becoming so big that they are paid the entire available KRE, there has to be a cap.

Definitions:

Max\_KRE% = Maximum % one App can get from the total available KRE

**IF ( KRE\_score / Total\_spends \* 100 ) \&gt; Max\_KRE% THEN KRE\_score = Total\_spends \* Max\_KRE% / 100**

The first part **( KRE\_score / Total\_spends \* 100 )** calculates what percentage **KRE\_score** is from the **Total\_spends** of all apps combined.

Then it takes this % and looks if it is higher then the allowed **Max\_KRE%**.

If this is the case then

**KRE\_score** will be made equal to **Max\_KRE%** \* **Total\_spends / 100** ( **KRE\_score** will be x% of **Total\_spends** )

Now we have capped the **KRE\_score** to the maximum of **Max\_KRE%**

You could make a rule that if more than 3 or 4 apps reach **Max\_KRE%** this percentage is adjusted downwards.

Like:

There should always be 25% of the KRE left for smaller apps. That leaves 75% **Max\_to\_divide** between the number of **Top\_apps** that reach **Max\_KRE%**.

**New\_Max\_KRE% = Max\_to\_divide / Top\_apps**

75 4 = 18.75% Numbers are arbitrary of course.

…................................................

**Example 2:**

Let&#39;s say you want to reward developers for the **DAS (Daily Active Spenders)** they bring into the economy.

**Definitions:**

Max\_DAS% = Max % of DAS per app.

This is a cap to prevent that 1 app

gets all just because it has millions of DAS.

Total\_DAS = Total number of DAS of all apps combined DAS = Actual number of DAS app-i brings in.

DAS% = Percentage of DAS for app-i proportional to Total\_DAS

**DAS% = DAS / Total\_DAS \* 100**

( this gives the percentage with which you can increase the **KRE\_score** ) ( it calculates the percentage that **DAS** is from the **Total\_DAS** )

Then we test if this % does not exceed the maximum permitted ( **Max\_DAS%** ). **DAS% = MIN( DAS% , Max\_DAS% )**

**KRE\_score = KRE\_score \* DAS% + KRE\_score**

**KRE\_score** is increased by the result of the former formula

( the calculated DAS% )

…................................................

As usual explaining formulas takes longer than the actual formulas themselves. It&#39;s just a few lines of code and probably can be made even shorter by a good programmer.

**Advantages**

It is a very simple and easy to implement code.

De code can be adjusted with every metric that is deemed important.

Developers can compete for KRE by generating more SPENDS then EARNS. This will drive the Kin economy.

By deducting the EARNS from the SPENDS all the gaming we have seen in earlier iterations of the KRE will be prevented.

The effect will be that less Kin will be given away for free by developers. Kin will actually be bought, either on exchanges or with a buy module in the app.

This will bring in more actual value in the Kin economy and that must have an effect on the Kin price.

KRE funds will no longer be just given away for free without adding value to the Kin economy. It&#39;s now public money well spent.

**What if my app doesn&#39;t generate any SPENDS?**

Apps that don&#39;t generate spends can&#39;t compete for KRE.

However, such an app might have value for the Kin Community. Think of a wallet, which might generate no SPENDS but is VERY useful for the community.

I suggest that for those apps a second fund will be created..

Apps can apply for a grant and a periodical amount of Kin for maintenance. It will be evaluated on a case by case base.

**Why is this the smart thing to do?**

Suppose you let wallets have part of the KRE and it turns out to be very lucrative. In no time we will see many wallets arise and we get the same as with staking. Developers will start making wallets...if they don&#39;t, they can&#39;t compete, and again we have a race to the bottom.

In fact, if wallets are covered by the KRE it would mean that every withdrawal must be seen as a SPEND, which it clearly is not.

By evaluating them on a case by case basis you can say okay, we have enough of this kind of apps. We are no longer subsidizing new ones with public money.

The KRE is standard for apps that give the economy a push forward. Sales (spends) have that effect, but many apps don&#39;t have them. They might be fun, but if they are not funny enough that users will pay for it then they don&#39;t push the economy forward. So, let the KRE be used for what it is intended for.

**How will a system based upon net SPENDS help grow the Kin Economy?**

**Basic economics**

By rewarding developers to generate more SPENDS then EARNS **Kin starts to flow** through the economy. KRE will still be increasing the circling supply of Kin, but now it will actually do what it&#39;s supposed to do, creating **Economic Activity**. Demand will become larger because less free Kin will be given away by apps.

Users will actually have to **buy Kin** , either on exchanges or in-app at buy modules.

Now the benefits of the **payment module** will be fully utilized. The user base will grow because they don&#39;t have to first go to exchanges to get Kin, which can be a very scary thing to do, but they can buy Kin right in the app where they want to spend it.

Apps are benefiting from **two sources of income** , their own generated SPENDS and the KRE reward. Since developers have **no need to protect the AUB** from getting lower, they can come up with meaningful SPENDS. 1 Kin SPENDS are a thing of the past.

No more need for 3 mandatory SPENDS per 30 days.

No need for the developer to limit withdrawals to just a few days a month. No need to lock user balances up to e.g. 100,000 Kin.

No need to hinder tourism because they don&#39;t need to protect their AUB. No more irritation of users which leads to a **better user experience**.

It will save the Kin Foundation a lot of unnecessary transaction fees if there is no need for 3 mandatory spends.

It&#39;s an easy to understand system. Just make a profit like you would in a regular store and get an extra bonus from the KRE.

Users will still be able to EARN some Kin, but maybe not as much as before. The benefit is that **we will get inflation under control**. The price of Kin will go up and that is good for developers, investors and users.

More **meaningful SPEND opportunities** lead to more USERS, leads to more $$ value, leads to more profit for developers, leads to bigger and more apps. The Kin Economy will grow. Large apps with millions of users might get interested in joining and the snowball gets bigger.

The Kin Economy will eventually become a **self-sustaining ecosystem**.