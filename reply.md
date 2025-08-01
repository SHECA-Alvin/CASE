**(Q1) Could you clarify if this date should be considered the start of the non-compliance?**

由于在SHECA之前的签发过程中未曾发现此类情况，且SHECA未对地址信息进行系统校验，所有校验均依赖审核人员的人工核查。SHECA认为这种不合规情况长期存在，因此无法确定不合规具体开始发生的时间。

**(Q2) Can you elaborate on “downstream agent” and “Wubi input method” to help us better understand this certificate issuance interface?**

“downstream agent”意思是SHECA的SSL证书代理商

“Wubi input method”:Wubi Input Method: Wubi Input Method is a Chinese character input method used in mainland China. It breaks down Chinese characters into strokes and components and uses five keyboard areas for input based on the shape and order of the strokes. This input method can only input Chinese characters.

Wubi input radicals for the character "市" should be: 亠(y), 冂(m), 丨(h), finalized combination "ymh"，

But agent typos "tmh",(t is closest key to y key on the keyboard), results 币

**(Q3) Specific to factor #1, can you elaborate on how this contributing factor avoided detection?**

因为SHECA的审核系统中并没有对地理信息的自动校验，此类信息错误只能通过外部审计或内部审计发现，本次是在合规人员对本周证书抽查的过程中发现了次问题。

**(Q4) Could you please elaborate on why these factors are not considered interactive?**

抱歉，我对IBR中 Interaction with other factors 的描述理解存在不清晰，正如您说的 缺少自动化的验证大大增加了审核出现错误的风险，我已调整了相关描述。

**Clarification on the Overabundance of Training-Related Items in SHECA's Action Items Section**

In relation to the current case, since the auditor failed to identify the incorrect entry of "重庆市" (Chongqing Municipality) as "重庆币" (Chongqing Currency) during the review, SHECA will enhance training for all auditors—with particular emphasis on verifying the accuracy of geographical information—to ensure such details receive heightened attention.

Concurrently, SHECA is upgrading system-level geographical information validation by introducing source data comparisons for geographical fields within certificate Distinguished Names (DN), including stateOrProvinceName and localityName.

In my opinion, a combination of targeted training and automated system checks will more effectively mitigate similar errors.

**As for the explanation regarding the excessive number of training-related items in the prior case action plan:**

SHECA has already automated processes pertaining to certificate issuance reviews and handling, allowing program-driven checks to flag potential issues during these stages. That said, certain internal operational tasks—such as CPS updates, publishing, and information synchronization with CCADB—remain partially manual, as full automation has not yet been achieved. This reliance on manual work inevitably gives rise to occasional errors.

To address this, SHECA is initiating relevant R&D initiatives. Moving forward, comparable internal CA operational workflows will be governed by programmed controls, thereby reducing human error and enhancing operational efficiency.

SHECA highly values your input. We will increase investment in automated operations R&D to minimize manual errors through programmatic checks. Thank you once again for your valuable feedback.
