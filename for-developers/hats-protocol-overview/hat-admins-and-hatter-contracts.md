# Hat Admins & Hatter Contracts

The admin of every hat is another hat. This means that the authority to perform admin functions for a given hat is assigned to the wearer of its admin hat.

The scope of authority for a hat's admin is to determine who can wear it. This is reflected in the ability to create the hat and to mint or (for mutable hats) transfer the hat's token.

### Transitive Admin Powers

In Hats Protocol v1, admin powers are transitive. All of a hat's ancestors — its direct admin, its admin's admin, etc — can serve as its admin.

### Separation of Powers over Hats

In most contexts, an "admin" role has broad, generalized control over the entity it administers. Hats Protocol is different. The generalized control over a given hat is separated into three distinct roles:

<table><thead><tr><th width="200">Role</th><th>Powers</th></tr></thead><tbody><tr><td>Admin</td><td><ul><li>Create new hat</li><li>Issue hat to wearer(s), aka “mint”</li><li>Edit hat properties (while mutable)</li><li>Transfer hat (while mutable)</li></ul></td></tr><tr><td><a href="eligibility-modules.md">Eligibility Module</a></td><td><ul><li>Prevent ineligible addresses from wearing hat</li><li>Revoke hat from specific wearer(s)</li></ul></td></tr><tr><td><a href="toggle-modules.md">Toggle Module</a></td><td><ul><li>Activate / de-active hat ⇒ all wearers lose the hat</li></ul></td></tr></tbody></table>

### **Hatter Contracts**

Logic contracts that serve as admins are informally known as "hatter" contracts. These are contracts that implement specific logic or rules. The admin of a hatter contract is the true admin, but has delegated said admin authority to the logic embedded in the hatter.

Hatter contract logic is a wide design space for DAOs. Here are some examples of hatter logic:

<table data-header-hidden><thead><tr><th width="184.5"></th><th></th></tr></thead><tbody><tr><td><strong>Hat creation</strong></td><td>Allow certain addresses -- such as members of a DAO -- to create hats that are then admin'd by the DAO.</td></tr><tr><td><strong>Hat minting</strong></td><td>Allow certain addresses -- such as members of a DAO -- to mint hat tokens. Together with the above, a DAO could in this way enable its members to create and wear a certain type of hat permissionlessly. This would be especially if using hats to facilitate role clarity and legibility.</td></tr><tr><td><strong>Wearer eligibility</strong></td><td>Enforce certain requirements that prospective wearers must meet in order to wear a given hat, such as membership in a DAO or holding some token(s). <em>Note that this is often more effectively implemented as an eligibility module.</em></td></tr><tr><td><strong>Wearer staking</strong></td><td>One particularly important type of eligibility requirement is staking tokens, DAO shares, or some other asset as a bond that could be slashed if the wearer is not a good steward of the accountabilities associated with the hat, or does not follow through on its associated responsibilities. <em>Note that this is often more effectively implemented as an eligibility module.</em></td></tr></tbody></table>

