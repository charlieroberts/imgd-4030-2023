# Course Assignments and Readings

- 8/25 - Introduction to Live Coding
    - Read: [Live Algorithm Programming and a Temporary Organization for its Promotion](https://art.runme.org/1107861145-2780-0/livecoding.pdf) (30 minutes, due 8/29)
    - Watch: [Introduction to Live Coding Music and Visuals](https://www.youtube.com/watch?v=-QY2x6aZzqc) (15 minutes, due 8/29)
    - Do:
       - The first 10 gibber "general" tutorials (30 minutes, due 8/29)
       - The gibber "music tutorials" (30 minutes, due 8/29)
    - Make: (Due 9/1) Create a 3--5 minute live coding performance in [gibber](https://gibber.cc/playground). Record the performance using a screen capture technology of your choice
      (I recommend [OBS](https://objs.project.com). There are lots of different strategies for this! You can start with all your code on the screen, and then highlight different
      parts at different times and run it, modifying as needed. Or you can start "from scratch"; this will probably result in inferior music, but is a fun challenge if you like
      to type fast. Or maybe you just have a few lines of code that you type and then modify for the rest of the performance. There are no wrong answers here.
        Write one page describing what you made, your aesthetic goals, the challenges you faced, and what you would continue to explore if you had more time to develop the performance.
        Critically assess your work, but at the same time, be gentle! It's your first time working with this software / technique and that should be reflected in your standards of assessment.
    - Read [Circles, Sines, and Signals](https://jackschaedler.github.io/circles-sines-signals/), from the introduction to the "sine wave aliasing" lesson (12 lessons total). Due 9/1 (about 45 minutes - 1 hour, depending on how much of a trigonometry refresher you need).
 
- 9/1 - Intro to Metasounds  
    - Explore: (Due 9/5) Complete the tutorials found in [Learning Synths by Ableton](https://learningsynths.ableton.com/en/). Understanding the ideas presented here will help you create interesting sounds/effects for the next part of the assignment for this week.  
    - Make: (Due 9/8) Create 5 different sound effects in Unreal using Metasounds (MS). The sounds should be substantially different from each otehr. Try to explore as many different MS nodes as you can, but be sure to explore: Generators / Oscillators, LFOs, Filters, Delays, and Envelopes at the very least. If you need inspiration, try search for videos on how to create classic video game sounds. You might not find MS specific resources, but it shouldn't be too hard to translate the core concepts into MS. Hook each sound up to a key press using Blueprints... the exact UE5 template project you use isn't important. Create a video of you triggering each sound in succession. Write 1--2 pages describing each sound effect, the nodes you explored, what you were happy with, and anything you wanted to implement but weren't able to figure out.  
    - Read (Due 9/5): [The Programmed Music of Mini Metro](https://designingsound.org/2016/02/18/the-programmed-music-of-mini-metro-interview-with-rich-vreeland-disasterpeace)  
    - Watch (Due 9/5): [Serialism and Sonification in Mini Metro (GDC 2018)](https://www.youtube.com/watch?v=FgV4hSfsl00)

- 9/8
  - Make: (Due 9/15) Using the First Person template in UE5, create a small world where the player can travel between three distinct pieces of procedural music. Each piece of music should feature at least three instruments and play indefinitely. You can drag your Metasound object into the level to place it, and then override the attenuation settings to control the radius of the sound field. On Tuesday we'll look at how to map sound effects to character actions; please prepare a procedural footfall sound to use for thia assignment also.
  - Read/Complete: (Due 9/12) [Creating Procedural Music with Metasounds](https://docs.unrealengine.com/5.1/en-US/creating-procedural-music-with-metasounds/)
  - Read: (Due 9/12) [How No Man's Sky Makes Original Music for Every Player](https://www.digitaltrends.com/gaming/no-mans-sky-music/)

- 9/19
  - Make: (Due 9/26) Experimenting with Reverb. Using a template of your choice in Unreal (you're also welcome to create your own world from scratch) experiment with creating reverbs for at least four different spaces in Unreal. How realistic can you make these spaces sound? Ensure that footfalls for both run and walk are heard, as well as sound effects for jumping; these sound effects should all be authored in Metasounds with some procedural element to them, although you can use audiofile playback within your Metasound patches. For your four different spaces:
  - At least one should use Unreal's built-in Reverberation system
  - At least two should use Convolution Reverb Submix effects
  - One should be experimental... this doesn't need to be realistic, but instead should be a crazy effect.
In addition to the reverb algorithms you choose, you might also want to experiment with occlusion or custom materials; links to tutorials covering these topics will be distributed in the course Discord server. Write a brief description of each reverb you created how you tried to make it realistic (or experimental), approximately 350 words. 

  - Read: (Due 9/26) [What is Reverb?](https://www.izotope.com/en/learn/reflecting-on-reverb-what-it-is-and-how-to-use-it.html#:~:text=De%2Dreverb.-,What%20is%20the%20definition%20of%20reverb%3F,the%20reflections%20eventually%20die%20off.)
  - Experiment: (Due 9/26) [How Generative Music Works](https://teropa.info/loop/)

 - 10/6 Soundscapes
     - Make: (Due 10/13) Create a level in a third-person project in Unreal that employs the following assets:
         - A Soundscape Palette to procedurally generate environmental sounds
         - Custom footstep, jump, and weapon firing sounds
         - At least one room with a convolution reverb applied to it
         - Procedural music created using Metasounds
         - In addition to the procedural music, at least two other Metasound sources must be used for sound effects.
         - Create a short video of the level and submit to Canvas.
