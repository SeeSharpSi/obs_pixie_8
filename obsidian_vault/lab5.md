---
type: assignment
topic: school
---

#IT4823 #school 

# What is happening
This lab has us create two simple Android applications that each take a password and provide a "copy" button and a "paste" button. We get the applications running on a Pixel 2 API on top of Android 5.0 (Lollipop).
My assumption is that Android allows applications to use a "paste" button that pulls from your clipboard without prompt. This is bad for obvious reasons; people copy passwords and entry codes often. The application can also copy to clipboard without a prompt, though this is not as much of an issue as pasting is. That said, Google recently made changes to their API to provide a "toast message" to the user asking them for permission to paste from clipboard. This should have been fixed sooner, but better late than never. [Here](https://developer.android.com/about/versions/12/behavior-changes-all#clipboard-access-notifications) is a link to their documentation.
![[Pasted image 20231021141937.png]]