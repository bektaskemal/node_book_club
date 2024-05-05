---
marp: true
theme: uncover
class: invert
paginate: true
# <!-- _backgroundColor: #8f0000  --> for red flags maybe?
footer: 'Node Technical Book Club - A Philosophy of Software Design'
---
<!-- _paginate: skip -->
# **NODE Technical Book Club**

## A Philosophy of Software Design -  John Ousterhout
<!-- 
Will cover chapters 16-22
-->
---
## Modifying Existing Code
<!-- Software development is iterative we often need to -->
- A system's design evolves over time but we need to keep complexity from growing.
- Take a strategic approach and refactor after the change if needed.
<!-- Invest instead of a quick fix -->
---
## Maintaining Comments
<!-- - Easy tzo forget -> inaccurate comments -->
- Place comments near the code they describe.
<!-- - DISCUSS: Even suggests placing interface comments to cpp instead of header files.  -->
- Spread implementation comments throughout the code.
- Document changes in the comments in addition to the commit message.
- Avoid duplication.
<!-- - Use references to avoid duplication  -->
---
## Consistency
- Powerful tool for reducing complexity and making its behavior more obvious.
- It can be applied to:
  - Naming
  - Coding style
  - Interfaces
  - Design patterns
  - Invariants
<!-- TODO: Add notes for them -->
<!-- - Interfaces: Different implementations of same interface should be consistent -->
<!-- - Design patterns: Since they are common knowledge, using them consistently makes the code easier to understand -->
<!-- - Invariants: Consistent invariants make it easier to reason about the code -->
---
## Ensuring Consistency
- It is hard to maintain consistency. Tips:
<!-- - Especially when many people work on a project over a long time -->
<!-- - Some groups might have conventions that others don't know -->
<!-- - Newcomers need to learn the conventions -->
  - **Document** the conventions.
  - **Enforce** them using tools.
  - Don't change existing conventions.
  <!-- - Having a better idea is not a sufficient excuse to introduce inconsistencies -->
---
## Code Should be Obvious
<!-- - Obscurity is the of the two main causes of complexity. The other: dependencies-->
- Non-obvious code is hard to understand and prone to bugs due to misunderstandings.
- Good names and consistency help making code obvious. 
- Judicious use of white space makes code more readable. 
<!-- White spaces -> Chunking in tidy first -->
- Use comments to explain non-obvious parts.
---
# <!-- _backgroundColor: #8f0000  -->
### :triangular_flag_on_post: Red Flag: Nonobvious Code
If the meaning and behavior of code cannot be understood with a quick reading, it is a red flag.
Oten this means there is important information that is not immediately clear to someone reading the code.

---
Things that make code less obvious:
  - Event-driven programming
  <!-- Hard to follow flow of control. Use interface comments to handle it -->
  - Generic containers
  <!-- Struct over pairs -->
  <!-- Software should be designed for ease of reading, not writing -->
  - Different types for declartaion and allocation
  <!-- Example: base class pointer stuff -->
  - Code that violates reader expectations 
  <!-- Mention: principle of least surprise -->
---
Ensure that readers always have the information they need to understand the code. To do this:
- Reduce the amount of information needed.
- Take advantage of common knowledge.
- Present the important information using good names and comments.
---
## Software Trends
Let's discuss the trends in software development from the book's perspective.

---
## Object-Oriented Programming
- If used carefully, it can help to produce better software design.
- Private members and methods are useful for information hiding.
- Interface inheritance can lead to more deep interfaces.
- Implementation inheritance reduces duplication so reduces change amplification. But it creates dependencies and results in information leakage.
<!-- Mention: Composition over inheritance -->
---
## Agile Development
- Agile development suggest incremental and iterative development as in the book.
- The risk about agile is that it can lead to tactical programming.
<!-- - "The increments of development should be abstractions not features." -->
---
## Unit Tests
- A good software design requires continuous improvement and refactoring.
- Tests are crucial for refactoring because they provide a safety net.
---
## Test-Driven Development
- TDD focuses on getting the features running, rather than finding the best design.
<!-- - This is tactical programming -->
<!-- - Discuss: As I remember, TDD has refactor step -->
- It makes sense for bug fixing.
---
## Design Patterns
- They represent alternative to design: rather than creating a new design, you can use a pattern.
- They can help making code more obvious and consistent.
- But be careful about overusing them.
---
## Getters and Setters
<!-- Are they a trend, really? -->
- A popular design pattern in Java.
- They are shallow and should be avoided.
---
## Designing for Performance
- How should performance considerations affect software design?
<!-- - Trying to optimize everything will slow you down and create complexity. -->
- The key is to develop a sense of what is likely to be a performance problem. Examples:
  - Network communication
  - Disk I/O
  - Dynamic memory allocation
  - Cache misses
<!-- - Use that sense to choose cheaper solutions when possible. -->
---
- Usually, a more efficient solution is as simple as slower one.
- If the only way to improve efficiency is by adding complexity:
  - If you can hide it, it may be worthwile.
  - Otherwise consider starting with a simpler solution and only add complexity if needed.
  - If you have clear evidence that the performance will be a problem, only then consider starting with the more complex solution.
---
## Measure Before (and After) Optimizing
- Don't rely on your intuition.
- **Measure before** to identify the bottlenecks and to have a baseline.
- **Measure after** to see the impact of your changes.
---
## Design Around the Critical Path
<!-- - The best way to improve performance is with a **fundamental** change. -->
<!-- - Examples: using a cache, using a different algorithm, or changing the data structure. -->
- If you need to redesign for the performance gain:
<!-- - The critical path is the part of the code that is executed most frequently and is the most performance-critical. -->
- Find the minimal code that must be executed in the most common case.
- Ignore current design and all special cases.
- Look for a new design that is good and critical path is close as possible to the minimal code.
- Try to minimize the number of special cases to check.
---
## Decide What Matters
- Structure software systems around what matters most.
- To decide what matters, look for leverage.
<!-- - Where the solution to one problem also allows many problems to be solved. -->
<!-- - Where knowing one piece of information makes it easy to understand many other things. -->
- Try to make as little matter as possible.
<!-- For the things matter, try to minimize the number of places where they matter -->
- Emphasize things that matter.
---
## Conclusion
- The book is about one thing: **complexity**
<!-- - Complexity is what makes systems hard to build and maintain. -->
- Described root causes of complexity and strategies to reduce it.
- Presented red flags to help identify complexity.
- Promoted investment mindset over tactical programming.










