# Sample Call

An illustrative example of how the agent handles an after-hours emergency.

---

**Agent:** Thanks for calling the maintenance line. This is Emma. Is anyone in danger, or is there fire, gas or flooding right now?

**Tenant:** There's water coming through my kitchen ceiling. It's getting worse.

**Agent:** I'm sorry, that sounds stressful. Let's get this handled fast. If you can, please move anything electrical away from the water. Can you tell me your full name?

**Tenant:** Maria Lopez.

**Agent:** Thanks, Maria. What's the best number to call you back on?

**Tenant:** 555-201-4478.

**Agent:** That's 5-5-5, 2-0-1, 4-4-7-8. Correct?

**Tenant:** Yes.

**Agent:** And the property address and unit?

**Tenant:** 1420 Oak Street, unit 3B.

**Agent:** Got it. When did the leak start?

**Tenant:** About twenty minutes ago.

**Agent:** If nobody's home when the technician arrives, may they enter?

**Tenant:** Yes, that's fine.

**Agent:** Any pets in the unit?

**Tenant:** One cat.

*Agent calls `log_maintenance_request` → urgency `emergency`, category `plumbing`*

**Agent:** You're all set. Your ticket number is M-R, 4-K-9-Z. Because this is an emergency, I've alerted the on-call technician, and you'll get a call back within 30 minutes. Is there anything else about this repair?

**Tenant:** No, thank you.

**Agent:** Thanks for calling. We'll take care of it.

---

## What happened behind the scenes

1. Vapi sent the tool call to the n8n webhook.
2. n8n created ticket `MR-4K9Z…` and added a row to the **Requests** sheet.
3. Because urgency = `emergency`, n8n texted the on-call technician the address, issue and tenant's callback number.
4. n8n returned the ticket number to Vapi, and the agent read it back to the tenant.
