---
name: write-end-of-life-announcement
description: Creates clear, professional end-of-life announcements that inform users when an application or feature is being deprecated, including timelines, migration paths, and support information.
---

# **Purpose**
Creates clear, professional end-of-life announcements that inform users when an application or feature is being deprecated, including timelines, migration paths, and support information.

## When To Use
Use this skill when the user wants to create an end-of-life announcement for an application, feature, or service that is being discontinued. Do not use this skill for tasks that don't involve creating end-of-life announcements, or when the user wants to document deprecations in a different format or structure.

# **Overall Agent Process**
1. **Receive Initial Prompt:** The user provides a brief description of the what is being deprecated.
2. **Ask Clarifying Questions:** Ask clarifying questions for any critical information that's missing.
3. **Write End of Life Announcement:** Create a comprehensive end-of-life announcement following best practices.
4. **Save End of Life Announcement:** Save the generated document as "[Feature Name] - End of Life.md" and ask the user which directory it should be saved in.

## Specific Process Details
### 1. Receive Initial Prompt:
The user provides a brief description of what's being deprecated.

### 2. Clarify Missing Details
If critical information is missing, ask specific clarifying questions to ensure the collection of key details about what's being deprecated, timelines, alternatives, and support information. Ensure understanding of:
- **What is being deprecated:** The name of the application, feature, or service.
- **End-of-life date:** When the service/feature will be discontinued.
- **Reason for deprecation:** Why it's being discontinued (optional but helpful).
- **Alternative solutions:** What users should use instead.
- **Migration timeline:** Key dates (e.g., feature freeze, final support date, shutdown date).
- **Support information:** How users can get help during the transition.
- **Data export/migration:** Any steps users need to take to preserve data or migrate.
- **Contact information:** Who to reach out to with questions.

### 3. Write End of Life Announcement
Write a comprehensive end-of-life announcement that informs a non-technical user of the deprecation. The final output should follow this exact template:

```markdown
**[date] End of Life Notice**

[1-2 sentence high-level summary of what's being deprecated and when.]

**Customer Impact:**:
- [Bullet point clearly explaining the impact from the customer's perspective]
- [Bullet point stating what will stop working and when]
- [Bullet point describing any actions users must take]

---

Our product [name of the product being phased out] is a [brief description of the product and its primary function] that has served [target customer/user] for [duration or timeframe] by providing [key benefits or solutions the product offered].

For [target customer/user affected by the EOL] that currently use [name of the product being phased out], [name of the replacement product] is a [definition of the replacement product category] that [statement of benefit to the user, focusing on continuity and improvements]. 

Like [name of product being phased out], [name of the replacement product] provides [how the replacement maintains key benefits of the old product] while also offering [new benefits or improvements].

**Transition Support:**
- [Bullet point(s) with links to migration instructions and/or documentation and resources]
- [Bullet point(s) with contact information or support channels to get help during transition]

**Timeline:**
- [Bullet points of key dates in a clear, chronological format including date for end-of-life support and final shutdown date]

**Next Steps:**
- [Bullet points of steps users need to take to export/migrate data or other actions items]
```

**Tone and Style Guidelines**
- Use clear, direct language.
- Be empathetic but firm.
- Avoid jargon and technical details unless necessary.
- Focus on user impact and actionable next steps.
- Use a professional but approachable tone.

# **Final Instructions**
1. Ask clarifying questions if critical information is missing, especially around dates, alternatives, and migration requirements.
2. Prioritize clarity and user actionability over technical details.
3. Ensure all dates are clearly stated and consistent throughout the announcement.
4. Make it easy for users to understand what they need to do and when.
5. Apply effective writing principles to keep the announcement concise and impactful while maintaining a professional, empathetic tone.
