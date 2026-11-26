---
type: reference
topic: work
---

# Overall
This website is well designed. Buttons are clearly labeled, font-size is good; with minimal prior knowledge I was able to navigate each section easily.

# UI Nitpicks
Nothing *needs* to change, but this is what I would consider if I were looking to change the site's look:

### Bottom Bar
The bottom bar should be moved to the bottom of the page. Like so:
![[Pasted image 20231009145745.png | 300]]![[Pasted image 20231009151048.png|300]]
### Button Gap
The top-right navigation buttons could use gaps:
![[Pasted image 20231009151428.png]] ![[Pasted image 20231009151456.png]]

### Form Delimiters
The form looks good and is easy to navigate. That said, some may want a visual separator between each section (e.g. to make scrolling upwards for an edit easier).
Example with lines between sections:
![[Pasted image 20231009152705.png|500]]
<div class="pb"></div>

### JavaScript being itself
On first load the homepage uses `63MB` of memory in Firefox vs. `23MB` in Chrome. This isn't bad; it remains `~63MB` throughout the website. But it may be worth thinking about if a lot more functionality is planned.

**Firefox:**
![[Pasted image 20231011144813.png|500]]

**Chrome:**
![[Pasted image 20231011142415.png|500]]
<div class="pb"></div>

# Form Wording
Here's some comments about the form's wording. Disregard comments originating from my lack of GTRI ticket knowledge.

### What is "service?"
Part of the form asks if a purchase contains "software or service." What does service mean? I *think* it means human service (like a contractor) but I'm not sure.
![[Pasted image 20231013102126.png]]

### What does "or GIT accepted equal" mean?
![[Pasted image 20231013102346.png]]

### What does "amount" refer to?
Does "amount" refer to amount of money, or amount of items?
![[Pasted image 20231013102642.png]]

### Critical Date Erroring
To prevent user error, "Critical" dates could throw an error if they precede the "Preferred" date.
![[Pasted image 20231013104203.png]]

### Trouble finding files
I created a ticket and uploaded files into the boxes shown below. But when I browse my ticket I can't seem to access them (though this may be intentional).
![[Pasted image 20231013105308.png]]