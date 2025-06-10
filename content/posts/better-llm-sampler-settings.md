---
title: "Better LLM Sampler Settings"
date: 2025-06-09T17:43:20Z
lastmod: 2025-06-09T17:43:20Z
draft: false
author: "Skynetcat"
authorLink: "https://skynetcat.github.io/about"

tags: []
categories: []

featuredImage: ""
featuredImagePreview: ""

hiddenFromHomePage: false
hiddenFromSearch: false
---
While I was trying [SmolVLM2](https://huggingface.co/ggml-org/SmolVLM2-500M-Video-Instruct-GGUF/blob/main/SmolVLM2-500M-Video-Instruct-f16.gguf) made by huggingface, I noticed it was hallucinating too much.
<!--more-->

I searched for its recommended sampler settings. Maybe something like what was provided for [Qwen 3](https://huggingface.co/Qwen/Qwen3-1.7B#best-practices):
> For thinking mode (enable_thinking=True), use Temperature=0.6, TopP=0.95, TopK=20, and MinP=0. DO NOT use greedy decoding, as it can lead to performance degradation and endless repetitions.

> For non-thinking mode (enable_thinking=False), we suggest using Temperature=0.7, TopP=0.8, TopK=20, and MinP=0.

However, I accidentally found [this reddit post](https://www.reddit.com/r/LocalLLaMA/comments/17vonjo/your_settings_are_probably_hurting_your_model_why/) that explains how inference settings work for LLMs.

I just grabbed what was recommended at the end of that post, tried it and modified it a little bit:
```
Context Length: 8192
Temp: 0.1
Top-P: 0.9
Top-K: 0
Min-P: 0.1
Mirostat Tau: 5
Mirostat Eta: 0.1
Repetition penalty range: 2048
Repetition penalty: 1.3
Presence penalty: 1
```

To my surprise, hallucination was cut to the minimum.

It occured to me to try it also with [Qwen 3 1.7b Q4](https://huggingface.co/unsloth/Qwen3-1.7B-GGUF/blob/main/Qwen3-1.7B-Q4_0.gguf) and I found the results better than using its recommended sampler settings!

See yourself:
{{< admonition note "Note" >}}
Think was enabled for both responses
{{< / admonition >}}


{{< admonition question "User Request" false >}}
Please give me a detailed guide on how to manage my email efficiently as I have 99+ emails unread. They are mostly useful emails (newsletters from online creators with useful information) 

I want to tackle this so I can clear my inbox and get much out of all the emails.
{{< / admonition >}}

{{< admonition abstract "Response 1: Normal Sampler Settings" false >}}
# **Email Management Guide: Tackling 99+ Unread Emails**  

---

## **1. Organize Your Inbox**  
### **a. Categorize Emails**  
- **Create folders:** Group emails by importance (e.g., "Newsletters," "Updates," "Follow-ups").  
- **Labels:** Use tags like "Project X," "Client A" to categorize emails.  
- **Example:** Label a newsletter as "Marketing" and a client update as "Client A."  

### **b. Use Filters**  
- **Automate sorting:** Set rules to move emails to specific folders based on sender, subject, or keywords (e.g., "All Newsletters" → "Newsletters").  

---

## **2. Prioritize and Mark Important Emails**  
### **a. Star Important Emails**  
- Mark emails with actionable insights (e.g., "Tips for [Topic]").  
- Use "Star" to highlight emails you need to respond to.  

### **b. Set Reminder Alerts**  
- Enable alerts for emails you need to reply to or follow up on.  

---

## **3. Delete vs. Archive**  
### **a. Delete:**  
- Remove emails you no longer need (e.g., spam, duplicates).  
- **Tip:** Delete emails you’ll never need to free up space.  

### **b. Archive:**  
- Move emails to "Archive" for future reference.  
- **Tip:** Archive emails for later use (e.g., a newsletter from a creator).  

---

## **4. Optimize Your Email Settings**  
### **a. Check Less Frequently**  
- Set a "Check email every X hours" to avoid distractions.  
- Use "Read Receipts" only if you need to reply (e.g., for follow-ups).  

### **b. Use "Reply All" Wisely**  
- Respond to bulk emails with "Reply All" to save time.  

---

## **5. Tools & Features**  
### **a. Email Clients**  
- **Gmail/Outlook:** Use built-in filters and labels.  
- **Third-party tools:** Apps like **Filterfy** or **Daisy** (for advanced sorting).  

### **b. Calendar Integration**  
- Sync your calendar with email to manage deadlines and follow-ups.  

---

## **6. Weekly Clean-Up Routine**  
### **a. Schedule a "Cleanup Day"**  
- Dedicate 30 minutes daily to check your inbox.  
- **Tip:** Use the "Star" feature to prioritize emails you need to act on.  

### **b. Archive Old Emails**  
- Move emails older than 30 days to "Archive" to keep your inbox clean.  

---

## **7. Habits to Build**  
- **Set a "No-Email" Rule:** Avoid opening emails unless you need to reply.  
- **Use "Read Later":** Save emails for later (e.g., a newsletter from a creator).  
- **Regular Reviews:** Check your inbox weekly to remove duplicates or outdated emails.  

---

## **Bonus: 5 Tips for Maximizing Value**  
1. **Follow Creators:** Subscribe to newsletters for exclusive content.  
2. **Use Templates:** Respond to emails with pre-written replies.  
3. **Batch Replies:** Reply to multiple emails at once.  
4. **Set Boundaries:** Turn off notifications for non-urgent emails.  
5. **Celebrate Progress:** Reward yourself for clearing 10 emails per week.  

---  
**Remember:** Email is a tool for connection, not a constant stream. Use it to *support* your goals, not just accumulate information. 🚀
{{< /admonition >}}

{{< admonition abstract "Response 2: Modified Sampler" false >}}
### **Step-by-Step Guide to Organize Your Inbox**  
Managing 99+ emails requires intentional strategy. Here’s a breakdown tailored to your goals:

---

#### **1. Categorize Emails Using Labels & Folders**
   - **Create Smart Categories**: 
     - Use existing headers (e.g., “News,”“Project Updates”) or create new ones (e.g., “Creator Insights”).  
       *Example*: Label every newsletter under “Creative Resources” to quickly find relevant updates.  
     - Assign categories dynamically via filters (e.g., “Subject Line Contains ‘Newsletter’”).
   - **Folder Structure**:  
     - Prioritize critical tasks first (e.g., “Urgent Follow-Ups”), then non-critical (“Personal Notes”).  

---

#### **2. Automate Email Handling**
   - **Set Rules in Gmail/Outlook**:  
     - Automatically move subscriptions to “Read Later.”  
     - Flag replies vs. forwards (e.g., label “Drafted Reply” for pending responses).  
   - **Third-Party Tools**:  
     - Use plugins like **Email Rule Manager** (for advanced filtering) or integrators like **Zapier** to automate workflows (e.g., sending reminders after a response).

---

#### **3. Batch Processing Techniques**
   - **Time-Based Scheduling**:  
     - Open your inbox at fixed times (e.g., morning → check once), reducing distractions during peak hours.  
   - **Batch Deletion + Archival**:  
     - Delete low-priority emails immediately (e.g., marketing campaigns); archive others permanently.  
     - Example: Move weekly reports to “Archived Projects.”

---

#### **4. Build Habits Around Email Checks**
   - **Single-Mail Ritual**:  
     - Only open one email per day (especially mornings/evenings). This reduces cognitive load.  
   - **Follow-Up Reminders**:  
     - Set alerts for deadlines (via Google Calendar / Todoist) to ensure no emails slip through.  

---

#### **5. Leverage Technology Wisely**
   - **Sync Across Devices**: Ensure cross-device syncing (G Suite/Microsoft Exchange) avoids duplicates.  
   - **Use Filters Instead of Spam**: Create custom filters (e.g., “From [Name]” > “Important News”) to reduce irrelevant traffic.  

---

#### **6. Regular Maintenance Routines**
   - **Weekly Cleanup**: Sort, delete, and archive monthly.  
   - **Monthly Review**: Check folder balances and adjust priorities quarterly.  

---

#### **7. Mindset Shift Toward Value Extraction**
   - **Highlight Key Messages**: Mark summaries or action-items in drafts/pdfs.  
   - **Avoid Overloading**: Don’t save everything — prioritize actionable insights.  

---

### 🧠 Bonus Tips  
- **Mindfulness Practice**: Reflect daily on why certain emails matter versus others.  
- **Limit Notifications**: Turn off pop-up notifications except for urgent matters.  

By combining tech solutions with mindful habits, you’ll transform chaos into clarity—a foundation for deeper engagement with creator-content! Would you like personalized recommendations for specific platforms (e.g., Gmail, Thunderbird)?
{{< /admonition >}}

This post was originally meant to be published on Reddit but as you know, Reddit sucks. As soon as I post something anywhere they tell me that I don't have enough karma or they just delete it.

Anyways, see you next time :)
