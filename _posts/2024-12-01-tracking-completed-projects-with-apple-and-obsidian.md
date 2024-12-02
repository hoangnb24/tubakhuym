---
layout: post
title: "Tracking Completed Projects with Apple Calendar and Obsidian"
subtitle: "Automating task tracking between Obsidian and Apple Calendar"
date: 2024-12-01
# background: '/img/posts/01.jpg'  # You can update this to a relevant background image
---

<iframe 
    width="100%" 
    height="400" 
    src="https://www.youtube.com/embed/7-TeuOACXbY"
    frameborder="0" 
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
    allowfullscreen>
</iframe>

I like to keep track of my completed projects. It’s satisfying to revisit my calendar and see exactly what I’ve accomplished. This habit helps me stay organized and gives me a sense of completion.

To streamline this, I came up with a solution that connects Obsidian and Apple Calendar. Here’s how I made it work:

---

### The Problem: Automating Task Tracking

I wanted two things:  
1. **A way to get notified when a task is marked as “Done” in Obsidian.**  
2. **Automatically creating a calendar event in Apple Calendar whenever a task is completed.**

I explored existing Obsidian plugins but couldn’t find one that matched my needs. So, I decided to build a custom solution!

---

### My Solution

#### 1. A Custom Obsidian Plugin

I created a new plugin to detect when a task is moved to the “Done” section of a specific document in Obsidian.  
If you’re curious, you can check out the source code [here](https://github.com/draphonix/obsidian-applescripts-runner/tree/main).  

This plugin monitors changes and triggers the next step: adding an event to Apple Calendar.

---

#### 2. Adding Events to Apple Calendar with AppleScript

Since I use Apple Calendar, I wrote an AppleScript to create a new calendar event. Here’s the script:

```applescript
-- Define the input
set input to {calendarName:"Logs", summary:"This event is added by AppleScript", description:"description"}

-- Extract input values
set calendarName to calendarName of input
set noteSummary to summary of input
set noteDescription to description of input

-- Get the current date and time
set currentDate to (current date)
-- Define event duration (e.g., 1 hour)
set eventDuration to 60 * minutes
-- Calculate end date
set endDate to currentDate + eventDuration

-- Construct a new event in the Calendar app
try
    tell application "Calendar"
        -- Find the desired calendar
        set targetCalendar to first calendar whose name is calendarName
        -- Create a new event with all properties set
        set newEvent to make new event at end of events of targetCalendar with properties {summary:noteSummary, description:noteDescription, start date:currentDate, end date:endDate}
    end tell
    return "New event created successfully: " & noteSummary & " - " & noteDescription
on error errMsg number errNum
    return "Failed to create event. Error: " & errMsg
end try
```

This script creates a calendar event in a specified calendar (in my case, "Logs"). The event includes a summary, description, start time, and end time.

---
### Reflection

Building this system was a fun little adventure! There’s always room for improvement in both the AppleScript and the plugin, but I’m happy with the results so far.

If you’ve tackled similar problems or have tips for better automation, I’d love to hear about them! Let’s share and learn together.

This setup not only keeps my project tracking smooth but also motivates me to keep checking off tasks. Hope this inspires you to automate some of your workflows!