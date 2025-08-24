---
description: Stream tokens and rewards to hat wearers
---

# Role-Based Compensation

Hats enables organizations to stream or send tokens and rewards to an account that only the hat-wearer has access to, using a combination of a Hats Signer Gate-enabled Safe with financial protocols like Superfluid, Sablier, or Splits. Organizations can even grant assets, including governance power, to a specific role without needing to know who has that role at any given moment. Thanks to the eligibility and accountability criteria that can be programmed into a hat, those assets are then only accessible by those holding the role only as long as they remain eligible.

<figure><img src="https://lh7-us.googleusercontent.com/V_bZ749T27w_gobouZoX8v2qr-pI-r6MaaJYYvbOwjcHfsUrXaTl4Ccyyxq3NgIJQGUtSZrPTGYOXQr9PD0d9r5OUXhAXZ07T3OZC41FE3Ebcq4Zn8ztmAq5bhWV2i1EZSwQx44Ta5X61KgZuQ8wIYA" alt=""><figcaption><p>A subset of the <a href="https://app.hatsprotocol.xyz/trees/100/92">RaidGuild Hats tree</a></p></figcaption></figure>

**Case Study:** RaidGuild is one of the original dev shops in the web3 space, with nearly 200 client projects (called “raids”) under its belt. As its membership expanded beyond [Dunbar's number](https://www.bbc.com/future/article/20191001-dunbars-number-why-we-can-only-maintain-150-relationships), the DAO required a clearer and more accountable way of operating. Hats Account enabled RaidGuild to set up payments to people in key roles via Superfluid streams. Without sufficient accountability mechanisms in place, the DAO had historically been hesitant to do this even though those roles were under-resourced. [See the full case study here.](https://www.hatsprotocol.xyz/wearer/raidguild-case-study)

**How you can use it:** Spin up a hat-connected 1/1 Safe multisig using the [Hats Signer Gate Factory](https://docs.hatsprotocol.xyz/hats-integrations/hat-gated-authorities/safe-multisig-signing-authority#id-2a.-deploy-a-new-hats-signer-gate-contract-using-the-hats-signer-gate-factory). Then, stream tokens to the multisig address via Superfluid or Sablier, or include it in an 0xSplit contract, and voilà, you’ve created a role-based compensation system!
