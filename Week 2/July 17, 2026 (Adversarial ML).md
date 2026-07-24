# July 17, 2026 (Adversarial Machine Learning)

**Machine Learning (ML)** models create effective domain-specific data-driven decisions to solve specialized tasks for a growing set of applications

> Some examples are medical diagnosis and self-driving cars!

<u>Machine Learning System:</u>
- **Machine Learning System** = gathers and analyze data through 3 phrases:
	1) **Representation** 
		- **Structure Intensive** - Formulation of concepts, rules, and equations
	2) **Computation**
		- **Process Intensive** - Application of processes or algorithms
	3) **Discrimination**
		- **Knowledge Intensive** - Evaluation against disparate source of info

> ML System can generalize info from data and learn to adapt based on new info!

<u>How ML Effective?</u>
![[Screenshot 2026-07-17 113645.png]]

<u>Why Important?</u>
![[Screenshot 2026-07-17 113830.png]]

<u>Threat Model:</u>
- **Assumptions about:**
	- **access level of adversary**
	- **capabilities of adversary**
	- **potential threats** 
- **TM:**
	- **Goal:**
		- Make AI wrong, leak data, copy the model, or cause unsafe behavior
	- **Access:**
		- can they change training data, send inputs, see scores, inspect model
	- **Knowledge:**
		- White-box means they know internals. Black-box means they only query it
	- **Limits:**
		- How many queries? Can they print stickers? Can they change web page?
- Example = **Self-Driving Car**
	- Physical address to the car, can reverse engineer model, gain information
	- Ability to modify the environment, craft examples to fool the model

<u>Trust Model:</u>
- **Trusted Actor** = given full access or restricted access to a system 
	- Bad actors with access to a system can employ the most effective attacks, this is known as "White-Box Attacks"
- **Untrusted Actor** = NO authorized access to the system
	- Bad actors with no access to a system can employ attacks, this is known as "Black-Box Attacks"

> Different levels of trust restricts a bad actor's attack strategy and its effectiveness

<u>Adversarial Capabilities:</u>

![[Screenshot 2026-07-17 114641.png]]

<u>Adversarial Goals:</u>
- Adversary wants to Exploit:
	- **Confidentiality and Privacy:**
		- Attack with respect to the model and data to identify information about model parameters or data records
	- **Integrity and Availability:**
		- Attack with respect to the model outputs to induce specific system behavior

<u>Security Threats to AI Systems:</u>

![[Screenshot 2026-07-17 114904.png]]

<u>Backdoor Attacks:</u>

![[Screenshot 2026-07-17 115256.png]]

<u>Preventing Poisoning:</u>
- Carefully inspect and triage the training data, do extensive testing:
	- **Provenance** = track where data, labels, and models come from
	- **Auditing** = look for duplicates, outlier, label patterns, and sus triggers
	- **Robust Training** = use method that reduce effects of small poisoned subsets
	- **Canary Tests** = tests unusual trigger-like patterns and edge cases before launch
	- **Monitoring** = watch for strange failures after deployment

<u>threats during testing:</u>

![[Screenshot 2026-07-17 115430.png]]

<u>Attacks During Interference:</u>

![[Screenshot 2026-07-17 115441.png]]

<u>Model Uncertainty:</u>

![[Screenshot 2026-07-17 115733.png]]

![[Screenshot 2026-07-17 115916.png]]

<u>Preventing Evasion Attacks:</u>
- No universal shield, but you can make the model more robust by training on adversarial generated images!
	- **Robust Model** = train with hard examples, use redundancy when mistakes are costly
	- **Input Checks** = look for strange inputs, assume detectors are not perfect
	- **Human Fallback** = use uncertainty, review, and safe failure modes for risky decisions
	- **Test Like an Attacker** = evaluate against adaptive attacks, not only ordinary validation data

<u>Model Assets:</u>
- Training Models are **very expensive**
	- A lot of electricity
	- Takes a lot of research hours to design new methodologies 
- Companies want to protect their "**Intellectual Property (IP)**"
	- Model architecture
	- Training data → may contain "**Personally Identifiable Information (PII)**" 

<u>Model Inversion Attacks:</u>
- Outputs reveal private features
- Attacker uses model outputs to reconstruct or infer sensitive information
- Involves sending an input to the model, performing math to improve model's prediction confidence in particular class repeatedly
- Especially risky when model was trained on sensitive data

<u>Membership Inference Attack:</u>
- Sometimes the secret is not the data itself, but whether the data was included in training
- An attacker can infer private information about people
- **EXAMPLE:** model was trained to predict diseases, and included records from Alice, attacker can check to see if Alice was in the training dataset and infer that she has a particular disease

<u>Model Extraction / Theft Attacks:</u>

![[Screenshot 2026-07-17 120627.png]]

<u>Privacy Defenses:</u>
- Reduce what the model memorizes and what the interface to the model reveals
	- **Data Minimization**
	- **Differential Privacy**
	- **Output limits**
	- **Access Control**
	- **Monitoring**
	- **Rate Limits**
	- **Output Design**
	- **Watermarks**

<u>Example LLM Prompt:</u>

![[Screenshot 2026-07-17 121855.png]]

<u>AI Prompt Injection:</u>

**Prompt injection** = security vulnerability where malicious input overrides an AI's system instructions to execute unintended actions. Because AI models do not distinguish between trusted developer instructions and untrusted user text, attackers can "jailbreak" the AI to leak sensitive data or perform unauthorized operations.

<u>Prompt Injection Example:</u>

![[Pasted image 20260722205905.png]]

<u>Adversarial Examples:</u>
![[Screenshot 2026-07-17 145801.png]]

<u>ML in Autonomous Driving:</u>
![[Screenshot 2026-07-17 145809.png]]

<u>Adversarial Attacks:</u>
![[Screenshot 2026-07-17 145925.png]]

<u>Adversarial Attacks - Type of Evasion Attacks:</u>
- **Fast Gradient Sign Method (FSGM)** = this attack method disturbs input data by adding noise proportional to the gradient of the loss function. It is fast and straightforward, but less effective compared to other methods
- **Basic Iterative Method (BIM)** = BIM improves upon FGSM by applying the noise iteratively, thus increase the likelihood of success
- **DeepFool** = this method attempts to find the minimal disturbance required to fool a classifier. It is highly effective but computationally expensive.
- **Carlini & Wagner (C&W Attack)** = this powerful attack minimizes the disturbance while ensuring the classifier mislabels the adversarial example. It is highly effective, but more computationally demanding than other methods

<u>Carlini & Wagner (C&W) Attack:</u>

![[Screenshot 2026-07-17 150246.png]]

<u> Defense Strategies - Adversarial Training:</u>
- **Definition:**
	- Training the model on adversarial examples along with regular examples to improve robustness
- **Process:**
	- Generate adversarial examples during testing 
	- Include these examples in the training set
	- Regularly update the training set with new adversarial examples
- **Advantages:**
	- Directly improves model robustness against specific types of adversarial attacks
	- Provides a straightforward way to harden models
- **Challenges:**
	- Computationally Expensive 
	- May not generalize well to all types of adversarial examples





