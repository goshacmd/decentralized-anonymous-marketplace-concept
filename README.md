# Silk Road 2.0

Silk Road 1.0 has demonstrated that it's possible to run an anonymous online marketplace. While technologically it wasn't that bad, there was a critical point of failure — its centralized nature. Capture administrator and everything is doomed.

Here is my proposal of a distributed anonymous marketplace that doesn't have a single point of failure.

*This concept does not focus on moral issues of participating in a voluntary anonymous trade nor does it enorse a specific use of a system it describes. It is more of a concept of decentralization of current marketplaces.*

Let us start by looking at some of SR 1.0 problems and try to figure a solution for them.

### Internal account balances

On Silk Road 1.0, every account got its internal balance. Users deposited money by sending them to DPR's wallets and the system credited the amount to their balance. On transactions between buyers & sellers, just the balances were updated and no actual money transfers took place. Moreover, the users didn't own these Bitcoin wallets so they were never in control.

It is, however, a bad idea to rely on a single person and trust all the money to them. Even if they are a good person themselves, there are violent third parties that can try to interrupt the operation any moment and try to seize the money.

So, that is a problem. Now. Problem, meet solution.

The solution is seemingly obvious. Let the parties transact directly without passing the money through the wallets of 3rd parties that can be compromised.

You own your money and don't have to trust anyone with it. Perfect, right?

But there is a reason SR needed the money to pass through its wallets. It's because there was a need in arbitration. Luckily, there is a way to arbitrate without rising your money to someone...

### Arbitration

So, arbitration. It's needed to resolve disputes the buyer and seller might have. Like the item arriving not in time. Or not arriving at all.

The way it worked on SR was like this: you buy something, the payment is held in a "pending" state, unless you finalize the order. You finalize it if you got your item and you have no concerns about it.

If you do, however, you can dispute with the buyer. If you are unable to meet an agreement, the administrator steps in and tries to resolve your conflict. Depending on outcome, the money may be transferred to the seller, refunded to the buyer partially, or refunded to the buyer fully.

And that is why it was needed for the money to be held by this trusted third party. Relying on them is, again, a bad idea, and luckily, there is another solution to this problem.

The solution is Bitcoin [transaction scripts](https://en.bitcoin.it/wiki/Script). Without digging into much detail, there is a way to allow mediation of Bitcoin transaction. There is even [an example](https://en.bitcoin.it/wiki/Contracts#Example_2:_Escrow_and_dispute_mediation) on Bitcoin wiki.

Basically, it works this way:

* the sender adds a public key of a mediator to the transaction, so that there are 3 people involved in transaction
* once transaction is broadcast, it kind of stays in the "pending" state unless two of these three cast their "yes" vote on transaction

There are three possible outcomes:

1. the buyer and the seller do agree about the transaction, cast their "yes"-s and money goes to the seller
2. the buyer does not agree and asks the mediator to help:
  * the mediator decides the seller didn't fulfill their part of agreement (e.g. didn't deliver) and casts a "no", and so does the buyer, then the transaction is no longer pending and the money is returned to the buyer
  * the mediator decides the seller did fulfill their part of agreement and casts a "yes", and so does the seller, then the transaction is no longer pending and the money reaches the seller

There are a few benefits to this scheme:

* you do not have to trust your money to the mediator. At worst, the money ends up being in seller's/buyer's possession — but definitely not mediator since there is no way the mediator can change the output of transaction
* the mediator doesn't have to be an admin or representative of SR. It can be anyone that both the buyer & the seller trust

Inviting a third party mediator is an interesting idea, as it also removes the dependency on marketplace owner to mediate your dispute... but how would it work?

A reputation system. Everyone can be an arbitrator and they get chosen based on their reputation. Which is what the next chapter is about.

### Reputation

A system like Namecoin could be used to maintain identities and reputation of buyers, sellers, mediators, and marketplace owners.

### Federated distributed marketplaces

There is yet another reason that relying on a single entity is bad. Even if your money always transfers to the buyer directly, and mediation is done by a third party, there is one more thing that isn't distributed — the marketplace itself. If someone arrests or otherwise intimidates the owner, everything goes down. Boom. The money is still yours but the operations had stopped. You can no longer buy or sell.

As a solution, something like this might be proposed: marketplace app is OSS and everyone can run their own. And, indeed, it's a good solution. If some marketplace owner gets arrested, the others are still functioning and almost no harm is caused to everyone else.

Yet, there is a little thing that makes this approach far from desirable: discoverability, for one thing. You will have to manually discover a variety of marketplaces and signup for all of them. What if there was a better way?..

In fact, there is. There is this project called [Diaspora](http://joindiaspora.com). Basically, it's a social network that everyone can run. The key idea is that instead of tens or hundreds of separate social networks that everyone runs, there is one. Everyone can merely run a node that will host this node's user accounts and associated data.

It also enables for easier discovery. You can subscribe to users from various other nodes, see their posts, and so on. So it's a **federated** distributed social network.

A similar concept can be applied to anonymous marketplaces as well. Everyone can run their own node, and that node will store its users' account data and catalog of items those users have.

From the user perspective though, there will be a single unified catalog of various goods.

## Wrap up

The solution I propose will allow to get rid of centralization that SR 1.0 have had and hence there won't be a single point of failure (central authority). The federated distributed marketplace will be much more difficult to shut down. And even in the case of shut down, no one is loosing their money.

These are basically my thoughts on how such a system could be implemented. It's very likely that I missed something important or didn't fully think it through. All feedback would be highly appreciated.

Twitter: [@goshakkk](http://twitter.com/goshakkk)

Bitcoin: 18sQnMCavXPPBzWfTYXd9aDju6NbWc89NL
