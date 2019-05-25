



# Principle 1: risk cannot be eliminated

The goal of a content security model is not to provide perfect security, it is to provide a level of security that brings the risk down to an acceptable level. Indeed, perfect security is possible only with snake oil. Real solutions aim to make unauthorized access of content difficult, time-consuming and expensive to accomplish.

That is the metric one needs to consider when evaluating every aspect of content security design: when some measure is applied, what exactly does it make more difficult, time-consuming and expensive to accomplish and for whom? In most cases, the cost increases both for the solution author and an attacker for every added element of security design. Watch out for "security theater" that only affects the solution author and makes no difference for an attacker!

At the end of the day, a weak content security model can be made to work if one simply increases the risk tolerance of the content - for example, by giving up on HD ambitions and sticking to SD content. This adjustment takes place in many solutions that are started with unrealistic assumptions about content security and a possible realignment in these terms should be considered in every project from the beginning.

# Principle 2: defense in depth

A robust security model remains functional even if some elements of it are compromised, either by accident or by malicious act. Defense in depth is the best way to achieve this - layer multiple levels of protection so that no single link will lead to a full system compromise.

This is a basic element of information security even outside the content protection field, so in many cases the solutions are obvious. For example, to ensure that disclosure of admin credentials do not lead to system compromise, one should require multi-factor authentication.

In some cases, the cost/benefit balance of adding defense in depth can be prohibitive. For example, if an attacker gains privileged access to your key server, should one invest into defenses inside the server? Obfuscate and encrypt keys in memory and on disk? Obfuscate the logic that uses them? In general, no - this is worthless waste of resources. Better spend that time and money on defenses on other layers of security. No matter how innovative and clever the protection, [if an attacker has privileged access to the executing software, they can extract secrets from it](https://threatpost.com/netflix-compromised-widevine-drm-hack/144220/).

Any claims of effective protection against a privileged attacker are misleading at best. Do not be taken by smooth talk - there are plenty of companies selling products for this who will say otherwise! The only effective means to protect against a privileged attacker is to require an even higher level of privilege, for example by placing the software and secrets inside a secure enclave (sometimes also called a trusted execution environment). That being said, protecting against attacks at such depth requires far more than just a secure enclave and is very costly - any investment into this should come only once a solution already has a very robust security design on all other angles. I have never encountered a solution where this would be the appropriate next step - there is always more lower-hanging fruit!

# Principle 3: minimal required human interaction

Any human interaction that is critical to the correct operation of an information system brings with it some risk.

A good system design avoids such activities and focuses on robust operation with the need for human operators.

# Principle 4: grant the minimal necessary level of access

Even when manual actions by human operators are required, only the minimal access should be granted. Even if an operator needs to install software updates, he does not need to have access to stored encryption keys. A good system design will enable roles to be separated so that different people and/or automated systems only have access to what they need for correct system operation.

# Principle 5: automate everything

# Principle 6: ensure operational effectiveness

# Components of content security model

# DRM versus access control

# Checkbox based security

# References

MPAA

MovieLabs