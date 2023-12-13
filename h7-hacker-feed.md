# Summary of a video
Out of interest I watched Antti Virtanen's Disobey presentation from 2020 [Im' in your office](https://youtu.be/jW5XebI1PMg?feature=shared). Presentation was about physical security even though it focused more on the digital access controls. 
One might think that new buildings and systems are secure, but surprisingly even the modern digital locks might use insecure communication. Traffic is unencrypted, no authetication is used and nothing is signed. This is due to fact that most 
of the protocols are actually decades old. Sometimes you don't even need to bypass the lock or tamper with it. Sometimes you can just walk in because door isn't actually locked even though it should be. Or you might be able to go around the door using 
another route (going through another room or go over the door). Automatic doors are handy, but they expose the possibility to tamper with the exit sensor leading to a way to open the door from outside by tricking the exit sensor.

Access tags look secure, but usually they are static things with no memory or anything. One can easily copy those tags even with a phone is certain cases. You could also by a relatively cheap device to copy the access tags from close proximate (under 10 cm). 
To mitigate some issues of the access tags, buildings should incorporate pin codes with tags so the tag itself wouldn't be enough to get into building. Most of all office and office building should have proper administrative controls to prevent anyone 
getting access by pretending a janitor or something.

If you want to try out physical access, same pricinpals apply to it as they do in penetration testing. Be sure to have permission to try it out and focus on recon. Doing proper recon helps you on your way since you know what kind of locks they are using, 
where are all the doors etc. And remember, do not try this out without permission, ever! Otherwise you might end up in trouble with the police.
