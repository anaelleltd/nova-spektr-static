# 1. Background

## 1.1. A Note on Definitions

In the closely-knit fields of blockchains and data-processing networks, it is important to understand the two rather different uses of the word "decentralisation". In the first case, which we might more precisely term *technical decentralisation*, we use the word almost synonymously with "distributed": it is a data-system implementation detail concerning the apportionment of workload and data-channel topology. In the present article, and generally-speaking in the blockchain industry, this is **not** the meaning we intend.

The second definition of "decentralisation", and the one which we mean to use exclusively in the present work, might also be termed *political decentralisation*. Here, the technical specifics of data pathways and workload are irrelevant. Rather we concern ourselves with the socio-economic question of which political/economic actors are able to influence the outcome of the service, potentially causing unintended, inconsistent, unexpected or incorrect behaviour. A system which is decentralised in this way aims to systematically reduce the level of influence of any single participant in an effort to maximise the chances that the overall system performs as intended.

## 1.2. Operational Decentralisation

Public blockchain systems utilize decentralisation to a greater or lesser extent as a means of forming consensus around the inputs of the state-transition function and helping ensure the correctness of its result. By doing so, blockchains are able to provide a massively accessible, global data-processing service with arbitrary rulesets and an unprecedented level of rational expectation of correct operation.

However, the actual level of decentralisation of public blockchain systems, even those which boast highly pluralistic groups of their network's node operators, is in fact quite minimal and generally undermined by centralising factors elsewhere in the "social stack". A recent study [1] showed that the service guarantees of most major networks could be compromised by at most a handful of people. I would posit that this is for three main reasons. Firstly, and most often discussed, is that the portion of power given to the individual actors who operate nodes and maintain the network is highly non-uniform. While no individual operator may be able to dictate consensus unilaterally (and thus break the network at will or through negligence), some very small subgroups are able to bend or break the rules amongst themselves. For the Bitcoin network, the number of individual economic actors required to execute a "double-spend" attack (whereby a confirmed transaction is reverted and another takes its place) varies in the single digits but has been as low as two on occasion.

Secondly, as pointed out by Moxie Marlinspike recently [2], major networks almost universally fail at facilitating decentralised usage of their service to their users. In order to gain the guarantees offered by the decentralised service, it is generally required to participate on the network directly by running the node software. This usually requires large amounts of time, a reliable, high-speed internet connection, plenty of storage and the installation of specialist software. Almost all real users are unable to do this and instead simply trust a centralised intermediary which relays information to and from the network. *A notable example of this is the Infura infrastructure of Ethereum which is used by default in Metamask, the predominant way of accessing Ethereum-based applications with some analysis suggesting as much as 70% of all transactions on the "decentralised" network being made through this single provider.* This reduces the practical factor of decentralisation for most network users to approximately that of a traditionally centralised service.  
*Note: Polkadot can provide its service securely to users both in-browser or on mobile without such an intermediary.*

Thirdly, finally and most importantly for the present work is the practical means by which node operators fulfil their role. It must be understood that blockchains are inherently software systems: operating a node on the network involves securely running a piece of software on a machine able to correctly operate according to the network's protocol. We generally call this piece of software the "blockchain client" or the "node software". Node operators make a decision to run this software and must manually select the software to download and need to decide when and whether to apply updates to it. Most node operators are uninterested in arcane protocol discussions and defer to very basic social cues in their decision. This leads to a silent and hithertoo little-explored centralisation risk for the network. And, unlike the first two points which can arguably be solved purely through mathematics and technology, I posit that this is instead a more entrenched social issue and as such a harder problem to solve. To understand the centralisation risk, it is crucial to understand the factors by which node operators select **which** software to use, and **whether** they should apply some upgrade. If these factors lead to the possibility of a small, well-aligned group of people able to widely deploy changes to the protocol, then it can gravely undermine the protocol and its guarantees.

The present article will soon explore this last point more deeply, but prior to this we will first build some context over the social centralisation forces at play particularly with regards commercial networks.

## 1.3. Problem Factors in the Decentralisation of Commercial Networks

Practically, the decentralisation of public networks intended as largely commercial vehicles (as many of the most-used networks are) has two notable problem factors: organisational privilege and economic disparity. The first is based on the fact that most networks are developed, launched, supported and promoted by a single legal organisation with a typical top-down power structure and funding model. These organisations often control the associated intellectual property and can wield it in an arbitrary fashion irrespective of the supposed values of the community or protocol. *(As an example, the Ethereum Foundation controls the various Ethereum trademarks.)* This organisation can, in the public mindset, become understood as a kind of proxy of the network itself with there being a supposition that the interests of the organisation and the network are equivalent. It becomes implicitly trusted to support, rescue and lead the network and its community in much the same way that a company plays parent to the products it sells. This presumption of trust and ownership can lead to a situation where one private organisation enjoys privilege over a decentralised system that others in the ecosystem do not enjoy.

The second is based on the fact that commercial networks tend to have a huge initial level of economic disparity in terms of the token ownership of their stakeholders. Those who are around at the inception of a network—and its associated currency—tend to receive a large proportion of the overall reward should it become widely adopted. This is true even in the case where there is no "premine" (currency allocation) simply because of the massive information asymmetry between the creators of a network and the adopters. Bitcoin may have had no such explicit allocation, but that does not mean that Satoshi Nakamoto—the pseudonym behind the launch of Bitcoin—is any less rich. Regardless, in a capitalist economy this is generally by design and it can be argued that it gives a clear and elegant means of rewarding the founders and early backers of systems which society ultimately deems useful. However, the more disparate the initial distribution and the less liquid the market, then the longer it takes before the economics can settle and token ownership can become truly reflective of the value with which the owner attributes to them.

During this initial period, we cannot rationally believe that all stakeholders' stakes faithfully reflect their belief in the value of the network. Arguments based on rational behaviour of economic actors are weakened as the markets cannot handle the flux needed to get from this initial imbalanced state to an equilibrium state. As such, mechanisms based on these arguments (such as proof-of-stake validator elections and "coin-voting" governance systems) are fundamentally broken and the correct functioning of the protocol is placed at risk.

## 1.4. Node Software and Protocol Specification

Authoring the node software is a difficult task requiring both a huge investment of time and substantial expertise of the underlying protocol. Because of this, most blockchain networks have only one realisation of node software and one team behind it. Worse still, networks tend to define their **protocol** in terms of the primary (or only) node software, including all bugs, opinionation, accidental design flaws and implementation details. Bitcoin is a good example of this, where its original author provided no protocol definition beyond the codebase and the protocol continues to be defined by that ever-evolving codebase under the dictatorship of a few so-called "core developers", unelected and formally unaccountable. In this case, a decision over the codebase implies a decision over the protocol.

In highly commercial blockchains, the software is subject to a closed development model in which a company's CEO has ultimate and absolute control. This makes the blockchain laughably centralised and entirely unfit for use.

However, even in highly open blockchain projects with open-source software (OSS) development models, decisions in software development must still be made and they will tend to happen under the benevolent dictator model as described by Raymond [3]. This can lead to a problem where a minority, including said "dictator", are of one opinion and the majority are of another. If both sides feel strongly and cannot be reconciled in a technical manner, then OSS projects may schism and become "forked", leading a single project and user-base to be split into two. The resultant projects and their teams fight for users on the merits of their relevant decision. Typically one project eventually wins out but co-existence and even cooperation is not entirely unheard of.

Unfortunately, for peer-to-peer consensus-based networks, canonical operation is crucial, as are safety and security. Forking no longer applies merely to a team and a community but also to a **network** and an **economy**. This exacts such a high cost to one of the forks as to make long-term coexistence as equals rather unrealistic and cooperation essentially unprecedented. Added on to this is the conservatism necessitated by the fact that the software controls an economy. This conservatism leads to a huge advantage to whichever fork can claim the status of the default and a near certain failure for the fork understood as the offshoot and therefore the riskier bet. One needs look no further than the Bitcoin and Ethereum networks' history to see this played out several times over.

## 1.5. The Power of the Default

This hugely important status of "default" is the manifestation of many factors, most of them centralised and unconnected to the merits of the underlying disagreement which led to the fork. Remarkably, the Ethereum Classic fork would show that protocol constancy (*i.e.* being the fork that minimises change) is apparently not a significant factor. The actual factors include distribution channels, code repositories, websites, software publication systems, forums, social media accounts, trademarks, privileged organisations, protocol identifiers (network handshaking) and the backing of major personalities of the space. Often times, these apparently ancillary elements unconnected with the outright protocol functionality are so centralised that a single individual indirectly controls almost all of them. However, in dictating what software runs on the nodes whose operators don't (want to) get involved in the discussion, they manifest themselves as singular levers to dictate the course of the project's following.

## 1.6. The Papal Model

Ethereum, notably, was the first major network to formally specify its protocol [4] in a minimalistic manner unencumbered by the accidental specifics of a particular implementation, and it continues to have multiple node implementations in its second major revision. However, even when the protocol is defined independently of any single development team, decisions on its evolution must be made. Without a strict framework, or *meta-protocol*, for making these decisions, we lose the ability to reason how the protocol will change in the future and thus to rationalise that it will continue operating as expected. As a non-technical, not-especially-diligent stakeholder of the protocol, the lack of a rules-based decision-making system means that one must simply "have blind faith" in the personalities who appear to wield significant influence. The appearance of influence is not the same as influence itself and there may easily be forces at play which are neither obvious nor transparent. As a political model, we might liken it to the Catholic church's papal leadership; an inner circle of self-serving cardinals with, inevitably, an individual "pope"—first among equals—who wields more influence than others and who is able to function as a benevolent dictator where there is a lack of consensus.

To have such an informal decision-making model can be beneficial in the early days of a protocol, when speed, ideation and execution are paramount, and security, reliability and stability can take a back seat. While such decisions can easily and opaquely fall pray to unaccountable external forces or personality politics, if the personality-driven leadership is problematic then, we can reason, the project will quickly fail and its resources can be swiftly deployed elsewhere with no great damage done to its stakeholders.

However, as a protocol matures and becomes increasingly valuable and relied upon, stakeholders must be able to rationalise their belief in continued correct functionality or risk a catastrophic outcome. Being based on religious faith of a preordained "infallible" individual or private organisation, the papal model offers little comfort here, and indeed seems distinctly ill-suited to an age where it is understood that transparency and inclusion are to be championed in public enterprises. Formal processes open to scrutiny and effective decentralisation are key components of the only solution we yet know to this problem of power.

---

# 2. Summary

One of the most pressing areas (if not the most pressing) undermining blockchain networks' decentralisation is that of technical decision making. The avoidance of formalising any specific organisational model is not an act of explicit decentralisation. In fact, it tends to lead to an effective power-structure which is opaque and centralised, as arbitrary and trivial social cues become the driving factors in determining what logic the node operators actually run. It becomes hard to rationalise about this outcome and we lose the credible belief that the network can remain secure, stable and progress to retain its relevance in the ever-changing world, especially in an increasingly unfavourable regulatory environment.

Thus, in order to avoid falling pray to these arbitrary and trivial social factors which open the protocol up to fundamentally centralising forces, we must take explicit action. The Polkadot Fellowship aims to be one example of such an explicit action. The Fellowship is a rules-based social organisation with several aims centred around the support and recognition of the technical expertise needed for technical stability, security and progress of the network.

The Fellowship can be seen as a political collective in that it has an on-chain voice controlled purely by its members according to some algorithm. It can also be seen as an incentivisation mechanism to help induct and retain expertise and talent important for the network. Finally, it can be seen as a vessel to help guide and support the personal development and maximise every individual's potential to contribute. Taken together, it helps ensure a continued pool of protocol expertise and plugs any power-vacuum which would otherwise be filled by *the papal model* or some legacy off-chain enterprise.

## 2.1. Rank

Politically, the Fellowship aims to be a source of expertise and leadership over the technology required in the ongoing maintenance and development of the Polkadot (Main) Network. The members are able to manifest their voice logically and, in protocol terms, exist as an **origin of action** on-chain. However, it is important to note that this has no specific ramifications in controlling the course of the Polkadot protocol. What specific power the collective has within the protocol is granted to it and held in check by other, generally much more inclusive governance apparati such as referenda.

The Fellowship aims to ensure a balance between cultivating, empowering and utilising technical merit relevant to the mainnet's protocol. In all these aspects it is important for the Fellowship to both identify those individuals who have merit and to quantify that merit. Thus the Fellowship is embodied through an on-chain data-structure (somewhat similar to smart-contract) which retains a list of members together with a rank, a scalar value in which the Fellowship approximates the individual's level of relevant expertise, talent and potential for contribution.

## 2.2. Forebears

The Fellowship is a member organisation existing on-chain whose statutes are partially governed by blockchain logic. In this sense, it may be considered similar to the Kusama Society, another purely logical organisation with both on-chain (autonomously enforced) and off-chain (via well specified social convention) components to its rules of operation. The purpose of the present article is in part to specify these rules and social conventions.

Aside from the on-chain element and its usage within an agile economic system, little here is especially novel. Many traditional expertise-oriented organisations which aim to nurture, recognise and govern are architected around a similar social structure. Martial arts have some notable examples with the International Taekwon-Do Federation being one such. This precedence might reasonably give us some confidence in the efficacy of this approach.

## 2.3. Audience, Goals and Non-Goals

While the need for, and broad intention of, the Fellowship is now clear it is important to define its specific goals. We can break these down into benefits, recognition and nurturing.

The Polkadot Fellowship focusses on the sustenance and enrichment of technical expertise relied upon primarily by the Polkadot Main Network. Technologies specific to the core protocol and its practical realisations are explicitly covered. Technologies not specific to the core protocol are generally not covered. While members may engage in any number of activities beyond immediate technical work (designing, programming, debugging), the goal of the organisation is nonetheless that of building technical knowledge critical for the continued existence and evolution of the network protocol itself.

The Fellowship thus aims to embody the expertise over the protocol, its formalisation and design which is utilised by any realisation of the Polkadot meta-protocol (*i.e.* a node implementation), as well as any specific realisation of the Polkadot runtime and any code or technology primarily utilised for the routine maintenance of the network and without which would seriously inhibit the network's potential to sustain itself.

Pure research, education, public outreach, recruitment, management and mentorship may be incidental activities of some members but it must be understood that these should not constitute the primary contributions for a member to receive recognition. The Fellowship is intended to be only the first of its kind. Should the concept (probably after some iteration) become proven effective, we might reasonably expect more instances of expertise-based organisation "fellowships" for other disciplines not covered by the present Fellowship.

### 2.3.1. Specifics

Based on the above, we may conclude that expertise on the following technology and its strict description(s) and/or implementation(s) would be considered a goal of the Fellowship:

- the internals of all functional Polkadot node implementations;
- cryptographic data-structures, algorithms, languages and APIs required for the continued upkeep of the Polkadot (Main) Network;
- consensus algorithms concerning the Relay-chain (BABE & GRANDPA);
- trust-free bridges relying on said consensus algorithms (planned to be) utilised by system chains;
- parachain consensus;
- cross-chain message passing (XCMP, HRMP, DMP & UMP);
- the *Polkadot ~~libp2p-based peer~~ networking ~~protocol~~ stack*;
- the Polkadot topology strategies;
- chain synchronisation strategies utilised by Polkadot;
- the Polkadot business-logic (aka the "runtime");
- pallets utilised by the Polkadot (Main) Network and its system chains;
- the internals of the FRAME pallet framework;
- runtime and host APIs;
- the XCM specification and realisation;
- standard RPCs;
- *core technologies needed to enable the existence of the Polkadot Network and its Native feature set;*
- *user-interface code required to carry out the technical work (designing, programming, debugging) required to maintain Polkadot (Main) Network, including operational upgrades* ~~user-interface code required to practically execute upgrades to the Polkadot (Main) Network~~; and
- code or technology required by, and utilised primarily for, any code or technology already included.

In short, if expertise on a technology (or a specific implementation of it) is **required** and **primarily used** for the Polkadot (Main) Network to continue **operating** and **improving**, then it is covered. If it is not then it is not.

Notable examples of technologies/code which are **not** covered:

- Rust language (required by realisations of the Polkadot Network, but not primarily used for them);
- libp2p (required by the Polkadot Network but not primarily used for it);
- `subxt` (useful tooling, but not required for Polkadot's continued operation); and
- `ink!` (useful tooling, but not required for Polkadot's continued operation).

Since the Fellowship is about retaining protocol *expertise*, it is not exclusive to developers, but also to ideators, designers, formalisers and research analysts. That said, machine-executable implementations do constitute an absolute requirement of the network's continued existence and thus it may not be unreasonable to expect an outsized proportion of implementors within the Fellowship.

### 2.3.2. Benefits

This refers to what might, in a more legacy context, be considered as the "material aspects" of the organisation. Firstly, members of the Fellowship need to receive support to ensure that their short-term needs are met. If Members cannot afford the time, equipment, accommodation, sustenance, dependents, and leisure activities which life demands, then dedicating themselves to Polkadot becomes unsustainable or unrealistic.

Secondly, it is important that Members feel that their fates are strongly linked to that of the Polkadot network if we are to expect a maximisation of potential. Put another way, we want to ensure that the long-term interests of the Polkadot Network and the individuals critical to its maintenance and development are well-aligned. Thus effective long-term incentivisation acts as both a means of pushing the member to dedicate themselves, as well as an internal compass providing some common cause which can underpin ideological alignment.

### 2.3.3. Recognition

This refers at once to two things: firstly the Polkadot network's ability to **identify** individuals possessing expert knowledge of the protocol and who are most likely to make future contributions. Secondly, as a means of the individual proving to others their expertise over, and dedication to, the network. Both are powerful tools inherent to formalising the expertise-base of the protocol.

Recognition is underpinned by evaluation and recording. While blockchain systems make the act of recording fairly trivial, evaluation must in large part be submitted on-chain through the judgements of existing members. Ensuring those judgements reflect reality is crucial as inaccurate judgements can entirely undermine the social framework. Providing convention on how to evaluate, decentralising the judgement and allowing anonymity to members are all means of encouraging objectivity and accuracy.

### 2.3.4. Nurturing

The Fellowship must provide the appropriate structure to nurture its members to reach their full potential. This is a rather complex and interwoven aim, but for the purposes of describing concrete goals, can be simplified into pedagogy, social support and, most difficult of all, cultural support.

In the first case, pedagogy, we simply mean to facilitate of the spread of knowledge and understanding between members. With social support, we mean to facilitate friendship and kinship between members in order to foster a mutually beneficial, cooperative and supportive environment for members. Finally, with cultural support, we mean the creation of norms and conventions which help the individual bridge the conceptual gaps difficult to grasp or internalise in purely abstract terms. One poignant example of such gaps would be the progression of personal development and the evolving nature of contribution through age and experience. Another would be the difference between the members of a collective and the collective itself.

While ones rank of a discipline may be linear out of necessity, practitioners' journeys may not be characterised as such. The act of contributing to a body of expertise is complex and non-linear. Providing an effectively nurturing environment optimises the member's contributions even as their personal circumstances change, as they almost invariably do. Age, family ties and interests can alter dramatically over the years but within a well-designed cultural structure, the richness of expertise available to the network can still be maximised.

By way of example, martial artists progressing through their discipline will often find that the culture is designed to help guide their focus as their fitness, experience and age changes. Inexperienced and unfit practitioners may be pushed to attain high degrees of fitness and disciplined technique. Those with high levels of fitness and good technique may be pushed towards the sport side. Older practitioners may be directed more towards flexibility, mental focus and the underlying philosophy. Highly experienced practitioners may begin instructing all of the above. Practitioners who have demonstrated themselves at the top of their art may be encouraged to help lead the political organisation.

---

# 3. Tenets

Members are expected to faithfully uphold the following tenets. Clarifications to the rules should be in agreement with these tenets. Acting in clear breach of these tenets may be considered by voters as grounds for non-promotion, demotion or, in extreme cases, exclusion from the Fellowship.

1. Sincerely uphold the interests of Polkadot and avoid actions which clearly work against it.  
2. Respect the philosophy and principles of Polkadot.  
3. Respect the operational procedures, norms and voting conventions of the Fellowship.  
4. Respect your fellow Members and the wider community.

---

# 4. Operational Rules

The operational rules of the Fellowship governing how its membership evolves are detailed below. These rules specify the process for becoming a member, attaining a rank and maintaining it.

During the initial bootstrapping phase some relaxations of these rules may be made in order to expediate decentralisation and ensure pluralism as early as possible in the member judgement process. Specifically, it may be reasonable to have shortened voting timelines and remove the need for some peripheral, demonstrative requirements if and only if it is obvious that the candidate in question possesses the relevant technical knowledge. In all cases, time limits on ranks should still generally be respected.

This leniency, such as it is, should exist only for the initial bootstrapping phase. By the first continuation evaluation ~~grading~~, the full expectations of the member's rank should be met for approval by voters.

Note, as per the tenets, the voting of Members is expected to follow the conventions and bylaws of the Fellowship, and in particular the Rank Specifications.

## 4.1. Entry

1. Any account may register to become a Candidate for a basic deposit. This associates the account with a rank of zero. Being a candidate is essentially a formality to help against state bloat and does not provide any additional entitlement for the individual.  
2. Once the individual is a Candidate, a pre-existing Member may request that they be promoted to a Member.  
3. Promotion:  
   - All Members of rank at least three are invited to approve or reject the Membership.  
   - The window for voting is open for a one month period.  
   - There must be a majority of rank-weighted votes in favour for the promotion to be approved.  
4. If the promotion is approved, they attain Membership and their associated rank increments to a value of one.

## 4.2. Promotion

1. Any Member may request their own promotion subject to the specifications and restrictions of their rank. (Some ranks place hard time limits between subsequent promotions.)  
2. Promotion:  
   - All Members of rank at least two greater than the prospective (post-promotion) rank are invited to approve or reject the Membership.  
   - The window for voting is open for a one month period.  
   - There must be a majority of rank-weighted votes in favour for the promotion to be approved.  
   - In the case of promotion to rank seven or above, all Fellows (members of rank three or greater) are invited to vote.  
   - If no members exist with a high-enough rank to affirm the promotion (always the case for promotion to rank eight and nine), then a general referendum of the Polkadot governance system must approve the promotion.  
3. If the promotion is approved, their associated rank is incremented by one.

## 4.3. Continuation

Ranks are generally kept regardless of current focus, however Members who feel they are not contributing actively for more than two months at a time are expected to voluntarily place themselves on a passive allowance.

Once over a period of time (three months for members below the rank of Fellow, six months for non-Master members who are Fellows or beyond) are automatically demoted unless their rank is re-approved by their peers. This upvote is similar to an evaluation ~~grading~~ and they should submit clear and concise argument ~~evidence~~ showing they are retaining the qualities expected of a member of their rank and have been contributing substantially for the period of time they have been on standard allowance.

There is no concept of suspension. Members are expected to be able to defend their rank every three or six months. The price for effectively suspending one's role (assuming one is not a Master) is a slow demotion through the ranks.

Master ranks are the exception: once a Master, one generally remains a Master regardless of occupation or knowledge. The only way a Master may be demoted or lose their rank entirely is through being found to have acted contrary to Polkadot's interests through a general Polkadot referendum.

## 4.4. Rank Voting

Voting generally happens through cumulative Rank-Voting. This simply means that Members votes are weighted by their Rank as an item in the geometric series. Rank 1 would have a weight of 1, rank 2 would have a weight of 3, rank 3 a weight of 6, &c. Formally:

$$
w(r) = \begin{cases}
0 & \text{when } r \leq 0 \\\\
r + w(r - 1) & \text{otherwise}
\end{cases}
$$

For Membership/Promotion/Continuation Votes, a particular rank is required for voting. In this case, we formulate the rank-weighted vote by first reducing the rank such that \(1\) is the lowest valid value. Formally:

$$
w'(r, m) = w(r - m + 1)
$$

## 4.5. Evaluation Considerations

In digital consensus systems, the evaluation conducted by actors on the network is engineered to be logically unambiguous. However in the social realm, consistency of judgement and evaluation is a highly non-trivial matter. Legal, education- and corporate-ranking systems throughout history bear witness to this. Balancing the expressibility and intention of the lawmakers or systematists with the need for unambiguity and clarity on the part of those who must interpret and execute is a fine art and there are many instances in recent history where one might argue it failed.

In the present work, our domain—and with it our problem surface—is intentionally constrained to the field of engineering core blockchain technology. Nonetheless, we are not yet at a point where we can define all judgements required by Fellowship voters in purely objective terms. Those members called upon to evaluate an individual will, to a greater or lesser extent need to make a judgement call. Pluralism, discussion and a clear framework for gathering a perspective is our antidote to the subjectivism which this otherwise creates.

The framework provided to help guide voters to make their decision is detailed here but is expected to be tweaked, clarified and built on over time. The framework comes in two broad segments: firstly, general subjects for consideration at least partially relevant at all ranks; and secondly criteria specific to a particular rank. The latter is detailed in **Rank Specifications**, whereas in this section we discuss the former.

### 4.5.1. API & Code Design

- **Level 0**: Rarely makes any suggestions, asks questions whose answers are easy to discover. Contributes to noise or stays silent and doesn't learn. This is an indication against Membership.  
- **Level 1**: Generally makes reasonable suggestions for APIs & code, rarely makes bad suggestions (expectation for I Dan).  
- **Level 2**: Generally able to identify flaws in APIs & code of those of the same or higher rank (expectation for II Dan).  
- **Level 3**: Occasionally innovative in API & code design, adapting/importing/inventing ideas that lead to effective solutions (expectation for III Dan).  
- **Level 4**: Often innovative in API & code design (expectation for IV Dan).

### 4.5.2. Code Contributions

Consideration points when evaluating code contributions. There is no attempt to quantify or describe what is reasonable/expected at a particular rank. However, the code contributions of a candidate may reasonably be judged by comparing the answers of these questions to the contributions of other members already at the prospective rank.

- **Correctness**: Does the code actually do what it is meant to do?  
- **Quantity**: How much relevant functionality is delivered in the code?  
- **Modularity**: Is the code only relevant for the immediate features, or was it architected and implemented sufficiently modularly, generally and with sufficient functional-independence to allow for reuse, maintenance and eventual externalisation?  
- **Quality**: Is the code minimal, elegant and comprehensible?  
- **Timeliness**: Was the functionality delivered at the optimum time for maximum value to be extracted through its existence?  
- **Longevity**: Has a past contribution, in hindsight, been of lasting value or was it quickly reimplemented or removed?

### 4.5.3. Social Interaction

These are consideration points when evaluating social interactions with other members. Once again, to be evaluated in a comparative manner to other members already of the prospective rank.

- The individual has the ability to listen, comprehend and form an effective dialectic.  
- The individual avoids ego and the heat & waste brought by pointless argumentation or repeatedly pushing against an answered point.  
- The individual is not afraid of calmly and succinctly challenging others when to do so would lead to them having a greater understanding of the world.  
- The individual is persistently and consistently making themselves available for the support of the network.

### 4.5.4. Voting

Though we explicitly acknowledge that judgements on social matters have an inherent level of subjectivity owing in part to the ambiguity inherent in natural language, we nonetheless expect that our efforts at guiding judgements through specific considerations and criteria should introduce a high amount of consensus to most decisions. As such, we might reasonably expect (and, indeed, desire) that lower ranks vote mostly in line with higher ranks.

A high degree of disparity by a lower rank from a consensus of higher ranks implies either a material misinterpretation of this document which the lower rank should be pushed to correct, or some negligence in their voting routine which would imply a lack of commitment to the Fellowship's norms.

Therefore, for those members up to rank six, the voting record of the member should mostly (up to a threshold) agree with the unanimous determination of those with higher rank. As the member gets a higher rank we can reasonably reduce the threshold, since unanimity becomes less indicative as fewer votes are used to constitute it.

Specifically, at rank three, this threshold is **100%**—namely, of the decisions made where the members of rank four and higher were in complete agreement, we expect any given member of rank three voted the same way. At rank four, this reduces to **90%** (and thus members of rank four need only vote with their superiors 90% of the time). At rank five, this is **80%** and rank six it is **70%**. There is no requirement for Masters.

This threshold is a soft requirement: Voters should generally disapprove in cases where the threshold is not met, but if the individual can adequately explain that their voting record is properly in line with a reasonable interpretation of this document, the core tenets and existing precedent, then the disparity may be overlooked.

Secondly, for non-Master members (ranks one to six inclusive), there is a minimum voting activity level, starting at **90%** of all votes eligible and reducing monotonically by 10% for each rank. This is a hard requirement. Masters, again, do not have such a requirement.

Finally, all voting is expected to follow the Operational Rules and Rank Specifications; disregarding these should be taken into account at the individual's subsequent evaluation(s).

## 4.6. Notes

Ideally, all voting is commit-reveal. However in the interests of expediency an initial implementation may be public.

---

# 5. Rank Summary

| Dan Rank | Name               | Grouping   | From I Dan | Material        | Hardness  | Activity | Agreement |
|---:|--------------------|------------|------------|-----------------|-----------|----------|-----------|
| n/a | Candidate          | n/a        | n/a        | (White)         | n/a       | n/a      | n/a       |
| I   | Humble             | Members    | n/a        | Graphite        | 1–3 Moh   | 90%      | n/a       |
| II  | Proficient         | Members    | ~1 years   | Stibnite        | 2 Moh     | 80%      | n/a       |
| III | Fellow             | Fellows    | ~2 years   | Galena          | ~2.5 Moh  | 70%      | 100%      |
| IV  | Architect          | Architects | >3 years   | Obsidian        | 5–6 Moh   | 60%      | 90%       |
| V   | Architect Adept    | Architects | >4 years   | Ilvaite         | 5.5–6 Moh | 50%      | 80%       |
| VI  | Grand Architect    | Architects | >5 years   | Magnetite       | 5.5–6 Moh | 40%      | 70%       |
| VII | Free Master        | Masters    | >6 years!  | Black Spinel    | 8 Moh     | n/a      | n/a       |
| VIII| Master Constant    | Masters    | >11 years! | Carborundum     | 9 Moh     | n/a      | n/a       |
| IX  | Grand Master       | Masters    | >19 years! | Carbonado       | 10 Moh    | n/a      | n/a       |

> **Note on images**: The original document referenced images such as `graphite.jpeg`, `stibnite.jpeg`, etc. If you add those files alongside this Markdown, you may embed them in the sections below with standard Markdown image syntax, e.g. `![Graphite](graphite.jpeg)`.

---

# 6. Rank Specifications

## 6.1. Candidate

This is the beginning rank and indicates someone new to the Polkadot protocol and codebases, but who has taken a first concrete step through placing a membership deposit and finding a sponsor.

Candidates may be of many levels prior to promotion to rank 1 and through a secondary system these levels may even be codified and properly recognised on-chain.

---

## 6.2. I Dan: Humble Member

*Approx. academic analogue: **Foundation course***  
*Material: **Graphite** (1–3 Moh)*

> Suggested image: `![Graphite](graphite.jpeg)`

The (potentially) softest of the materials, symbolising the beginning of the journey and the most to learn from the world. Also shares the exact same chemical composition as the material of the highest rank Grand Master—the hardest material—symbolising the individual's potential to go all the way.

The primary qualities which should be present and clear in those being given the rank are aspiration, knowledge-discovery, knowledge-sharing and active maintenance. They should demonstrate commitment to the protocol's development through mastery of at least one major component as well as having a broad understanding across the protocol. They will demonstrate commitment to pooling and sharing protocol knowledge through establishing a pattern of availability or communication in one or more online media; forums, chatrooms, issue trackers or Q&A sites. A pattern of general availability on synchronous communication media would also count in the individual's favour and demonstrate a commitment to the network maintenance. The candidate should have a rudimentary awareness of, and ability to be educated on, overall priorities and tradeoffs in development & design of a global, decentralised and unstoppable network, including centralisation risks, non-jurisdictionality, privacy, automation & maintenance vs autonomisation & ownerlessness.

The Candidate must clearly demonstrate an independence of mind and spirit. They should be able to work alone and without direction, to investigate and problem-solve without need for assistance and to be responsible for the design, implementation and/or continued maintenance of a Polkadot component or sub-system which could reasonably be considered important for the continued health and operation of the Polkadot network. The Candidate should be making clear demonstrations of protocol expertise.

There is no specific time which must have passed with Polkadot being the individual's primary life-focus prior to attaining this rank, though a reasonable expectation would be that they have been working on core Polkadot technology continuously for around 12 months.

### 6.2.1. Requirements [for I Dan]

- Three clear examples of a modest but substantial contribution to protocol development.  
- Actively been involved in the design of a component. The component should be either deployed into the protocol or reasonably intended for future deployment into protocol **and** at the standard expected of an internationally peer-reviewed publication.  
- Substantially assisted in the analysis, or authoring of formalisation or implementation of a protocol component. Formalisation should be at the standard expected of a peer-reviewed publication. Analysis should either lead to a change in the protocol or be at the standard expected of a peer-reviewed publication. Implementation should be in a functional implementation of the protocol.  
- Should be able to list all key goals, principles and tenets of Polkadot's overall philosophy.

Possible examples of a "modest but substantial contribution" may be:

- identifying and correcting a non-trivial issue in protocol code or formalisation;  
- being available and playing a crucial operational role for a network fix;  
- proposing a reasonable and non-trivial protocol innovation; or  
- doing a valuable, innovative and insightful refactoring or simplification.


## 6.3. II Dan: Proficient Member

*Approx. academic analogue: **Bachelor's degree***  
*Material: **Stibnite** (2 Moh)*

> Suggested image: `![Stibnite](stibnite.jpeg)`

As a key component in many pyrotechnic preparations, Stibnite represents the process of transformation, symbolising rebirth and metamorphosis. It symbolises the transformative nature of the journey of the individual on the way to becoming proficient and the need to change ones perception as the understanding of the protocol evolves.

A member at this rank should be a core part of the team. Clear demonstration of knowledge of the protocol is crucial, but since the individual knowledge of the protocol is unlikely to be complete then general knowledge acquisition and communication/sharing is also very important. The individual should be becoming deeply familiar with at least one major area of the protocol in their role as a builder and should be becoming increasingly familiar with design considerations typical in protocol development. They should not be asking dumb questions and should instead be making reasonable suggestions. They should be demonstrating a readiness to be a network maintainer through increased levels of availability. Excellent candidates will already be "on-call" for the components of which they have a deep understanding.

It is generally expected that the participant will have been practicing Polkadot as their primary life-focus for at least **one** year, unbroken, after attaining the previous rank.

### 6.3.1. Requirements [for II Dan]

- Primary individual responsible for the formalisation, implementation or analytical improvement of a major component of the protocol. Formalisation, and analysis leading to any improvement, should be in a peer-reviewed publication (or there should be a good reason why not). Implementation should be subject to expert code-review and included in a functional implementation of the protocol.  
- At least one published long-form semi-technical article concerning Polkadot.


## 6.4. III Dan: Fellow

*Approx. academic analogue: **Master's degree***  
*Material: **Galena** (~2.5–2.75 Moh)*

> Suggested image: `![Galena](galena.jpeg)`

Galena is the mineral form of lead. This was known, mined, refined and used by the ancients, and its long role serving human-kind symbolises the foundational level the individual has now reached by completing the first third of the ranks, and also serves a reminder that recognition of skill and commitment is provisioned on the individual's continued servitude to the whole. As a Fellow, the individual attains new privileges and the heavy nature of the substance represents a need of the individual to act with due consideration on decisions which their new responsibility brings.

As a foundational grade, a Fellow represents both a ceiling and a floor: becoming a Fellow indicates the individual has enough knowledge and skill to build substantial protocol components (i.e. all but the major protocol components, e.g. a pallet or 2–10,000 line crate) alone and with high expectations that they will be completed correctly and to a high standard. They should be able and willing to support that which they built given that it is running 24/7 on a public network. This means a commitment to availability even when it may be inconvenient for them and, in periods of lesser-availability, taking on a responsibility to make this clear to their team prior.

They should readily understand the difference between *what something does* (i.e. the interface, the service offered and the reason for doing something) and *how it works* (i.e. the underlying data structures, implementation details, and the specific code). They should readily be able to grasp the solution a particular logic module is attempting to solve, asking the right questions as necessary and documenting their way to save others the trouble. They should be able to extrapolate intent and from it effectively review output and make insightful suggestions over improvements or additions which would help achieve the apparent goals.

They should have no problem making regular low-level implementation/formalism decomposition, designing code or formalisms in a modular and hierarchical manner. Furthermore, they should be showing signs that they are beginning to understand solution decomposition over boundaries efficient for implementation/formalising. Implementation/formalism decompositions should be elegant and, at least sometimes, reusable.

The individual should by now be thinking in a very much in a security-conscious, game-theoretic way, understanding that the systems whose design they are increasingly a part of must function adequately even with a modest minority of malicious users. Recent reviews of their design work should betray no evidence that the individual is either failing to consider this or unable to think in such a way.

As a Fellow the individual, in some quite real sense, represents the Polkadot Network and as such must be ready and willing to both defend it and its values. They should not merely adhere to the basic community code of conduct, but to hold themselves to a higher standard, maintaining a high level of calm and humility but also honesty and directness. They have a responsibility to represent the Fellowship as well as the network and this should be done in a polite and non-combative, but also honest and forthright fashion. Internally, they should be both helpful, tactful and well-spirited, understanding that Polkadot is a team effort.

A Fellow must have a comprehensive knowledge of the overall priorities and tradeoffs in the development and design of a global, decentralised and unstoppable network and be able to express and explain themselves on these matters confidently.

It is generally expected that the participant will have been practicing Polkadot as their primary life-focus for at least **one** year, unbroken, after attaining the previous rank.

### 6.4.1. Requirements [for III Dan]

- **Promotion should involve an in-person evaluation ~~grading~~** during which superiors may invite the individual to answer specific questions concerning their contributions.  
- Defense should include a conversation on the philosophic principles and their relation to the technology where they demonstrate expert knowledge confidently and betray no misinterpretations. They should be able to confidently defend the existence of Polkadot, compared to other projects in the same industry as well as its wider place in society.  
- Substantial presence in defending or advocating Polkadot outside of the ecosystem. This may take one of several forms: at least three published long-form semi-technical articles concerning Polkadot; substantial presence on social media used by other industry participants; presence within conferences or publications of a specific academic or industrial discipline.  
- Demonstrable presence of knowledge sharing within the ecosystem. This may take several forms: an ecosystem presentation on Polkadot or some component of it; activity on the Polkadot community forum or chat channels; activity on Polkadot-related developer forums such as StackExchange. The medium is not important; the impact is everything.  
- Either played a supporting role in the ideation and a primary role in the formalisation of a major protocol component; or played a supporting role in the code-design and a primary role in the implementation of a major protocol component. The formalisation should be included in a well-respected peer-reviewed publication or the design implemented and deployed into the protocol. The implementation should be subject to expert code-review and included in a functional implementation of the protocol.


## 6.5. IV Dan: Architect

*Approx. academic analogue: **Doctorate***  
*Material: **Obsidian** (5–6 Moh)*

> Suggested image: `![Obsidian](obsidian.jpeg)`

This is the first of the middle three *Architect* ranks and connects the portion of the journey where the individual develops beyond knowledge on the past and is expected to contribute to core innovations and design of the protocol's future. The next three materials symbolise three qualities required of the individual during their journey of become a protocol Architect.

The materials are all of approximately the same hardness symbolising that all three qualities are of comparable importance, and their hardnesses (5–6 Moh on each) sit in between the softer materials of the lower three ranks and the harder materials of the upper three ranks, symbolising the maturing nature of the architect's intellect.

The first, for the grade of 4th Dan is Obsidian. It is essentially volcanic glass, composed of silicon with other light elements and easily forms sharp edges. It has been used in tools since ancient times especially for creating cutting blades. The sharp blade symbolises the single-minded focus required by the individual in both becoming a subject matter expert and in innovation itself. It is very slightly softer than the other materials of the expert ranks reflecting that a deep level of expertise, while very important, is the junior of the three qualities.

To attain this grade the candidate should be demonstrating a shift in their focus from the attainment of specific knowledge, comprehension and skills to the less knowledge-based and more creative elements of protocol development: ideation, invention and innovation. Rather than (just) plentiful incremental low-level improvements to the protocol, substantial valuable individual contributions to the (r)evolution of the protocol should have been demonstrated through broad architectural work together with novel designs leading to formalisation and/or implementation of technology (ultimately) found valuable by the Fellowship. Rather than comprehension, their ability to experiment, design and build new technology must be beyond question and their truly novel ideas and designs must be of a consistently high quality and at least occasionally beyond the imaginations of those with higher rank.

The individual should be readily able to understand the design space in which solutions sit. They should be able to not only devise solutions themselves but to adequately *architect* solutions based upon implementation-orientated solution decomposition, breaking down a design into components of a sensible size and complexity yet each with its own clear concern, interface, *raison d'être*. All components should be, when treated in isolation, a solution to a problem in themselves, and if that problem cannot be clearly stated, then it may indicate a misarchitected system.

The participant will have been practicing Polkadot as their primary life-focus for at least **one** year, unbroken, after attaining the previous rank. However, this is only a bare minimum and should not be taken as a presupposition of the expected amount of time required. The candidate should be only be promoted to this grade once the time limit is over **and** they have demonstrated the appropriate aptitude.

### 6.5.1. Requirements [for IV Dan]

- Either played a primary role in both the ideation and subsequent formalisation of a major protocol component; or played a primary role in the code-design and implementation of a major protocol component. The formalisation should be included in a well-respected peer-reviewed publication or the design implemented and deployed into the protocol. The implementation should be subject to expert code-review and included in a functional implementation of the protocol.  
- Further presence of advocating or defending Polkadot outside of the ecosystem. A good benchmark would be one pre-advertised presentation on Polkadot to an industry-wide, academic or other such well-aligned audience outside of the ecosystem. It may also be fulfilled within other media of a similar weight (e.g. a professional journal, major news publication or academic article).


## 6.6. V Dan: Architect Adept

*Approx. academic analogue: **Research Fellow***  
*Material: **Ilvaite** (5.5–6 Moh)*

> Suggested image: `![Ilvaite](ilvaite.jpeg)`

The second material in the middle three ranks is Ilvaite, a mineral which exhibits pleochroism, meaning it appears to change colors depending on the angle in which is it viewed. As the second material in the Architect ranks, it symbolises the need for multiple perspectives, reflecting that great architects often draw upon knowledge and understanding from different teams, areas or even disciplines in order to create a final solution. It should remind the individual that while myopia and deep focus can be an alluring path and even necessary in the pursuit of perfection, they should not overlook the possibility that an alternate form of the problem is already solved by others or that inspiration may arise from apparently unrelated areas of human-pursuits (consider Feynman's story that physics Nobel-prize winning work arose from studying the dynamics of a tea-saucer when spinning in the air).

To attain this rank, the candidate must have demonstrated clear levels of architecture. Their abilities as a builder should now be beyond question and as a leader in technology design should now be becoming clear. They should begin to understand the protocol as a living organism and be able to visualise its path. They should only very rarely misunderstand a protocol consideration, and have a clear grounding in all fields related to protocol design including game theory, economics, programming languages, complexity, entropy and distributed systems. They should be able to speak with technical authority on all levels of the Polkadot protocol past, present and future.

The participant will have been practicing Polkadot as their primary life-focus for at least **one** year, unbroken, after attaining the previous rank. However, this is only a bare minimum and should not be taken as a presupposition of the expected amount of time required. The candidate should be only be promoted to this grade once the time limit is over **and** they have demonstrated the appropriate aptitude.

### 6.6.1. Requirements [for V Dan]

- Play a primary role in ideating, designing **and** formalising or prototyping a major component.  
- Usefully assisted in devising ("creating", "inventing", "incepting") three more major components.  
- Usefully assisted (through advocation, research or rationalisation) in determining the long-term technical roadmap.  
- At least one published long-form article about technology relevant to but not specifically concerning Polkadot.



## 6.7. VI Dan: Grand Architect

*Approx. academic analogue: **Associate Professor***  
*Material: **Magnetite** (5.5–6 Moh)*

> Suggested image: `![Magnetite](magnetite.jpeg)`

Magnetite is a primary form of iron ore. It is ferrimagnetic and both attracted to magnets and able to be magnetised itself. It was used by ancient civilisations in the discovery of magnetism which lead to the use of compasses, and occurs in biological cells used as a navigation aid (with birds and bacteria being two important examples). This material concludes the three key elements of architecture and represents the need not just for the ability to focus on an individual technical direction, nor also to take ideas from broad range of perspectives but also, crucially, to retain a long-term strategic product direction or risk being pulled off-course.

This grade is the highest rank to be arrived at through purely technical prowess and to attain it, the individual must demonstrate they can match or better others of this rank in their absolute technical ability. As a benchmark, they must have played an advisory role in the architecture, design and implementation of at least five major protocol components and actively designed and built at least two from start to finish. They must have demonstrated beyond doubt the ability to nurture into greatness not only new Fellows but also new Architects. They must also be able to withstand or manage the rigours of being a technical architect. A willingness to delegate, to work at a tenable speed and an overall knowledge ones own limitations is crucial.

The participant will have been practicing Polkadot as their primary life-focus for at least **one** year, unbroken, after attaining the previous rank. However, this is only a bare minimum and should not be taken as a presupposition of the expected amount of time required. The candidate should be only be promoted to this grade once the time limit is over **and** they have demonstrated the appropriate aptitude.

### 6.7.1. Requirements [for VI Dan]

- *Devised*, led the *design* and overseen (or led) the implementation of a major protocol innovation.  
- At least three published long-form articles about technology relevant to but not specifically concerning Polkadot.  
- **Discuss:** What have you learnt from this individual which you might ultimately find useful in your efforts to help Polkadot succeed?

> *Note:* This is the first rank for which pre-specified discussion points become a crucial part of the evaluation ~~grading~~ and where those voting on the promotion must make a qualitative assessment on the outcome of the discussion in comparison to the precedent of prior promotions.


## 6.8. VII Dan: Free Master

*Approx. academic analogue: **Professor***  
*Material: **Black Spinel** (8 Moh)*

> Suggested image: `![Black Spinel](spinel.jpeg)`

As the only named material here which is rarely black (Spinel is commonly one of several other colours), it symbolises the individual's journey through many shades of life and arrival into the set of Masters. As a material far harder than all those previously, it symbolises that the individual's journey as a student is ending and the beginning of their journey as a protector and leader.

The rank of Master indicates a move into the upper three ranks of the Fellowship and with it a refocusing from the predominantly technical qualities surrounding invention, design, architecture and development into the more philosophic, strategic, socio-political and sophist qualities associated with good leadership. To attain this rank there must have been a clear demonstration of these qualities.

The rank calls for intellectual conversation no longer focussed primarily inside the protocol but also outside into the wider industry and social, political, commercial and technological environment in which Polkadot ultimately sits. It calls for education and advocacy, both at the technical and less-technical levels. This can take many forms, not least written articles, interviews, social media, conferences and other pod-/vid-casts. At this rank, the individual might reasonably spend their effort split equally three ways: today (expertise and availability on the protocol which is running the network right now), tomorrow (helping design and evolve the protocol which it will become) and the future (helping shape the overall direction of the protocol and including its social and political elements).

Masters are expected to gain themselves (and by extension Polkadot) a good standing and reputation beyond the Polkadot ecosystem. They are expected to be a living advertisement of Polkadot's tenets and its philosophical and intellectual rigour. At this rank they are an outward intellectual representative of Polkadot and must at all times conduct themselves in concordance with both the edge and the humility that a true master of an art must possess.

Masters need no longer defend their place in the Fellowship. However, promotion to Master cannot be done just by other members of the Fellowship, no matter the rank. Instead, Masters may only be conveyed by a Root call, which should by convention happen only after the majority of rank nine members have issued their approval. Conversely, it is only through a general referendum that the rank may be revoked.

To attain this rank, the individual **must** have been practicing Polkadot as their primary life-focus for **six** years in total, in addition to the demonstrating the administrative, knowledge, intellectual, social and skill-based qualities expected.

### 6.8.1. Requirements [for VII Dan]

- Contributed to the broader understanding of the philosophy behind Polkadot during an in-depth conversation. Perhaps through drawing parallels to existing body of literature, perhaps through rational discourse with experts. Should be ready and confident in their ability to explain and defend the newfound understanding.  
- Several major presentations on the Polkadot network and protocol with an audience that included peers from other ecosystems and/or industries.  
- **Discuss:** Does the wider academic community or industry tend to learn from this individual (even if the individual did not discover this knowledge themselves)?



## 6.9. VIII Dan: Master Constant

*Approx. academic analogue: **Professor in a historical seat***  
*Material: **Carborundum** (9 Moh)*

> Suggested image: `![Carborundum](carborundum.jpeg)`

Man-made crystal from 1800s, used for cutting & polishing.

As the only purely man-made associated material, Carborundum represents the fact that the Fellowship and their members are forged by mankind, not born of nature. Carborundum, being among the hardest of minerals, finds a lot of use for cutting and polishing; this symbolises the individual's role, changing to that of helping others become polished masters in their own right.

This rank indicates a Master with an elevated level of commitment to furthering the interests of the Polkadot network. To attain the rank, it should be clear that the individual is helping shape the future of the network, its protocol and its overall ecosystem in a way commensurate with the overarching tenets laid out in the Polkadot Paper, the goals of Web3 and the principles of enlightened liberalism.

To attain this rank, the individual **must** have been practicing Polkadot as their primary life-focus for **eleven** years, as well as fulfilling the social and administrative qualities expected of being in the previous rank.

### 6.9.1. Requirements [for VIII Dan]

- At least one article considered canonical by masters which further develops the understanding of the philosophical principles underpinning Polkadot.  
- At least one article about an innovation relevant to but not specifically concerning Polkadot which is ultimately recognised as a pan-industry innovation.  
- Generally recognised as an intellectual heavyweight outside of the Polkadot ecosystem.  
- **Discuss:** How did this individual's idea or invention become adopted in the wider academic community or industry?



## 6.10. IX Dan: Grand Master

*Approx. academic analogue: **Nobel/Field's Laureate***  
*Material: **Carbonado** (10 Moh)*

> Suggested image: `![Carbonado](carbonado.jpeg)`

Carbonado is a black form of diamond and the hardest mineral known to man. This symbolises both the peak of seniority and knowledge that the rank represents but also the limitation of human-knowledge and that the journey of discovery never ends.

To attain this rank, the individual **must** have been practicing Polkadot as their primary life-focus for **nineteen** years, as well as fulfilling the social and administrative qualities expected of being in the previous rank.

### 6.10.1. Requirements [for IX Dan]

- Generally recognised as a philosophical, social, artistic, political and/or technological heavyweight outside of blockchain or crypto.  
- **Discuss:** what outstanding service did the individual provide to the Polkadot network?

---

# 7. Notes on Master Ranks

The three Dan ranks of Master have a series of sub-ranks (which also function as honours) not recognised within the on-chain voting system and unimportant for voting weight, defined primarily to recognise some exceptional service of the individual to Polkadot. In addition to recognition of effort, they help mark and celebrate milestones within the journey of personal development during which, especially at the stage of Master, time can flow a little too easily with significant events being less apparent.

The Master may reasonably be described by the mainline grouping (Master), mainline rank (Free Master, Master Constant, Grand Master) or specific sub-rank. The latter would be considered most polite since it implies the most knowledge concerning the individual.

Initially no such sub-ranks are defined, but each **Master** shall be free to name one in their new rank as they attain the ranks of `VII Dan`, `VIII Dan` or `IX Dan`.

At most ten shall ultimately be given for `VII Dan` and sixteen for `VIII Dan`. There is no limit to the number of sub-ranks for those of rank `IX Dan`.

The elevation within sub-ranks must be agreed in-person at a Masters' meeting, and must be for some specific act of special service of Polkadot going beyond the general expectations of contribution at the rank. In general, a sub-rank may be attained no less than six months following the previous, 12 months for sub-ranks of `IX Dan`. Attaining all sub-ranks should not be considered strictly necessary for promotion from their rank, however it would be a near inescapable indication that the member should be promoted.

## 7.1. Obligations of Masters

Being a master comes with additional obligations:

- Fellowship can, through a standard vote of Fellows, implore a Master to assist with some piece of technical work.  
- Assistance may be substantial (including advising on strategy, architecture, design, APIs and algorithms) but must be constrained.  
- This mechanism is used only in the most extreme circumstances where:  
  - Existing non-Master Members are unable to complete the work themselves to a standard needed for network safety;  
  - The Master has expert knowledge and can lend knowledge and experience which are crucial to achieve success and otherwise unavailable;  
  - The assistance involved is of a clearly constrained scope; 1–2 hours should be the typical expectation in terms of time, though under extreme circumstances, 1–2 days may be needed. Two weeks' of assistance should be considered an upper limit.  
- Failure to assist the Fellowship can be considered grounds for breach of Rule #1 and may be considered grounds for demotion or, in extreme circumstances, expulsion. As with all Master-level punishment, this is determined & enforced through General Referendum.

## 7.2. Annexes, Clarifications and Conventions

On elevation to a Master rank, the individual is able to propose an annex (additional rule), clarification or non-binding convention to this manifesto. Pre-existing rules always take precedence. These amendments are included by default after a one month challenge period passes, during which time a majority ranked-vote of the Fellows (and above) may cancel it. Amendments must not break the principles nor any pre-existing rules.

---

# 8. Allowances

These are a monthly affordance, paid in DOT. There are two levels: standard and passive. Standard should be between the 80th–90th percentile of gross income in the OECD group of countries. Passive is no greater than 50% of standard. The total amount given as passive allowance should be no greater than 10% of the total amount given as standard allowance.

Members are free to place themselves on a passive allowance if they believe they are unlikely to contribute substantially within any given month. (At challenge or evaluation ~~grading~~ time, members who do not may find the lack of productivity difficult to explain.) Regardless, members must keep their knowledge and skills up to date.

---

# 9. Prizes

Since sub-ranks are not available to Members, Members, and especially Masters, are invited to create **honourable prizes**. Prizes should include some sort of endowment (e.g. a DOT gilt or high quality staked DOT derivative) and a description of what it should be awarded for and who should judge. A reasonable selection would be a Masters level vote, but need not be.

Prizes should eventually be recorded on-chain but an initial implementation may not.

---

# 10. Events and Gatherings

At least once per year the members of the Fellowship should gather. This should be paid for by the treasury. Lower evaluations ~~gradings~~ (I–III Dan) should happen here (though I and II Dan may happen remotely).

There should be additional meetings exclusively for Fellows and (when there are practical numbers) Masters. Information on these meetings should (for security purposes) be kept on a need-to-know basis. Disregarding this is a breach of Fellowship rules. Upper evaluations ~~gradings~~ (IV–VI Dan) should happen here.

---
---

# References

[1] Moxie Marlinspike. My first impressions of web3. https://moxie.org/2022/01/07/web3-first-impressions.html, 2022.

[2] Eric Raymond. The cathedral and the bazaar. Knowledge, Technology & Policy, 12(3):23–49, 1999.

[3] Evan Sultanik, Trent Brunson, Mike Myers, Alexander Remie, Sam Moelius, Talley Amir, Felipe Manzano, Eric Kilmer, and Sonya Schriner. Are blockchains decentralized? unintended centralities in distributed ledgers. Technical report, Trail of Bits, 2022.

[4] Gavin Wood. Ethereum: a secure decentralised generalised transaction ledger. http://gavwood.com/paper.pdf, 2014.

---

# Appendix A. Terminology

- **Architect**: A member of the Fellowship whose rank is between least four and six inclusive.  
- **Candidate**: An individual who is not yet a member of the Fellowship; they may be said to be "unranked", but logically their rank may be inferred as zero.  
- **Dan**: Alternative means of specifying a rank where roman numerals are used. E.g. *I Dan* is equivalent to *rank 1*, whereas *VII Dan* is equivalent to *rank 7*, &c.  
- **Fellow**: A member of the Fellowship whose rank is at least three.  
- **Master**: A member of the Fellowship whose rank is at least seven.  
- **Member**: A member of the Fellowship; this implies their rank is at least one.  
- **Primarily**: The case where a single individual is responsible for the vast majority of work done such that if no others contributed then a (perhaps lesser but still correct and useful) artefact would be delivered.

---

# Appendix B. Philosophy & Principles of Polkadot

> *Note: This section needs substantial improvement in the coming months.*

## B.1. Enlightened Liberalism

Honesty and freedom. But respect, politeness and tolerance.  
**Required reading:** *The Open Society and its Enemies*

## B.2. Critical Rationalism

Judge only by actions, not suppositions, associations or words.  
**Required reading:** *A Pocket Popper*

## B.3. Web3

Reduce the need for the individual to trust the group by providing them with tools to interact usefully with the world themselves.  
**Required reading:** *What Web3.0 looks like*

## B.4. Polkadot

Decentralised, empower the individual.

---

# Appendix C. Meta-notes

> *Note: This section captures the current train of thought and is better moved to an online forum for community discussion.*

*Careful, now…*

- Rank & hierarchy come with baggage.  
- Members should know and practice equality and humility.  
- Correctness is not determined by rank but nature herself and members must never forget this.  
- There could be some requirement to keep on building (at least a minor amount) all the way up to the top in order to keep progressing through the grades.  
- Re-emphasise that plentiful teaching, education and rational advocacy is a crucial part of moving through the last half of the grades.

## C.1. Ideas & Considerations

- Introducing shadowing a pre-existing Fellow as a requirement for Fellow evaluation ~~grading~~.  
- Introduce sponsors:  
  - A sponsor is required for each candidate or member who seeks a promotion.  
  - The sponsor must be a member of at least two ranks greater than the rank sought for promotion.  
  - If a promotion is denied, the sponsor may not sponsor further promotions for a period of six months.  
- Require also a small write-up of lessons learned at each grade, especially following the shadowing.  
- Master ranks should be encouraged to develop into disciplines separate to Polkadot and find ways to contribute their learnings back into the whole.  
- In general, evaluations ~~gradings~~ should be conducted in-person. From III Dan evaluation ~~grading~~ and above, they **MUST** be in-person unless environmental conditions make it impossible (e.g. pandemic). If the individual wishes to remain anonymous, a mask or other facial-covering may be worn.  
- Bring in smaller milestones e.g. public technical presentation.  
- Bring in knowledge of principles: enlightened liberalism; critical rationalism; Web3 & truth vs trust; Polkadot and its five guiding tenets in the paper. Candidates should move from basic knowledge to the ability to converse to eventually having a deep understanding and contributing back.

