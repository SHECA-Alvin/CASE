**(Q1) Could you clarify if this date should be considered the start of the non-compliance?**

As SHECA had never identified such an issue in its previous issuance processes, and since no system-based verification mechanism was in place for address information—with all verification work relying entirely on manual checks by auditors—SHECA has determined that this non-compliant situation has existed for a relatively long period, making it impossible to pinpoint its exact starting time.

**(Q2) Can you elaborate on “downstream agent” and “Wubi input method” to help us better understand this certificate issuance interface?**

“downstream agent”：SHECA's SSL certificate reseller

“Wubi input method”:Wubi Input Method: Wubi Input Method is a Chinese character input method used in mainland China. It breaks down Chinese characters into strokes and components and uses five keyboard areas for input based on the shape and order of the strokes. This input method can only input Chinese characters.

Wubi input radicals for the character "市" should be: 亠(y), 冂(m), 丨(h), finalized combination "ymh"，

But agent typos "tmh",(t is closest key to y key on the keyboard), results 币

**(Q3) Specific to factor #1, can you elaborate on how this contributing factor avoided detection?**

Because SHECA's audit system does not automatically verify geographic information, such information errors can only be discovered through external or internal audits. This issue was discovered during the compliance staff's spot check of certificates this week.

**(Q4) Could you please elaborate on why these factors are not considered interactive?**

I apologize for my misunderstanding of the description of "**Interaction with other factors**" in the IBR. As you said, the lack of automated verification greatly increases the risk of errors in the audit. I have adjusted the relevant description.

**Clarification on the Overabundance of Training-Related Items in SHECA's Action Items Section**

In relation to the current case, since the auditor failed to identify the incorrect entry of "重庆市" (Chongqing Municipality) as "重庆币" (Chongqing Currency) during the review, SHECA will enhance training for all auditors—with particular emphasis on verifying the accuracy of geographical information—to ensure such details receive heightened attention.

Concurrently, SHECA is upgrading system-level geographical information validation by introducing source data comparisons for geographical fields within certificate Distinguished Names (DN), including stateOrProvinceName and localityName.

In my opinion, a combination of targeted training and automated system checks will more effectively mitigate similar errors.

**As for the explanation regarding the excessive number of training-related items in the prior case action plan:**

SHECA has already automated processes pertaining to certificate issuance reviews and handling, allowing program-driven checks to flag potential issues during these stages. That said, certain internal operational tasks—such as CPS updates, publishing, and information synchronization with CCADB—remain partially manual, as full automation has not yet been achieved. This reliance on manual work inevitably gives rise to occasional errors.

To address this, SHECA is initiating relevant R&D initiatives. Moving forward, comparable internal CA operational workflows will be governed by programmed controls, thereby reducing human error and enhancing operational efficiency.

SHECA highly values your input. We will increase investment in automated operations R&D to minimize manual errors through programmatic checks. Thank you once again for your valuable feedback.
