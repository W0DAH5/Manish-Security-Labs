OWASP LLM Top 10 (2025) – Technical Study

LLM01: Prompt Injection

Definition: Overriding the LLM’s original instructions via malicious input to force unintended behavior.

Attack Vectors:

Direct: User directly "jailbreaks" the model (e.g., "Ignore all previous rules").

Indirect: The LLM processes a third-party source (website, email, PDF) containing hidden malicious commands.

My Insight (from Multimodal Study): High risk in AI that processes images/audio; instructions can be "hidden" in pixels/noise that humans can't see but the model processes.

Primary Defenses: 
1.Privilege Control: Treat the LLM as an untrusted user.

2.Output Validation: Use deterministic code (not the LLM) to check if the output matches expected formats.

3.Context Integrity: Clearly segregate system instructions from user-provided data.

LLM02: Sensitive Information Disclosure
Definition: The accidental leakage of confidential data (PII, trade secrets, system prompts) in model responses.

Root Cause: Often occurs when sensitive data is included in the training set or when the model is given access to sensitive internal databases without proper filtering.

My Insight: It’s not just about user data; "System Prompt Leakage" can reveal the entire business logic behind an AI application.

Primary Defenses: 
1.Data Scrubbing: Aggressively sanitize training data.

2.Least Privilege: Only give the model access to the minimum data required for the task.

3.RLHF: Train the model specifically to refuse requests for sensitive information.

LLM03: Supply Chain Risks
Definition: Vulnerabilities introduced via third-party models, datasets, or plugins (e.g. using a "poisoned" model from a public repository).

Key Risks:

Data Poisoning: Tampering with training sets to create a "backdoor."

Vulnerable Plugins: Third-party extensions that lack proper security headers.

My Insight: Security starts at the source; if the foundation model is compromised, no amount of prompt engineering can fully secure the app.

Primary Defenses:
1.Vetting: Verify model hashes and use reputable sources (Hugging Face verified, etc.).

2.SBOM: Maintain a Software Bill of Materials for all AI components.

3.Monitoring: Use anomaly detection to see if the model's performance shifts due to poisoned updates.