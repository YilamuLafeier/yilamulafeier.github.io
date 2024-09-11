---
layout: essay
type: essay
title: "In With The New, Out With Old?"
date: 2024-09-05
published: true
labels:
  - Computer Science
  - JavaScript
  - Software Engineering
---

# In With The New, Out With Old?

   My first experience with TypeScript was with my Software Engineering class. While it was new for me (and new for the course), I found that it made JavaScript easier to read at least for myself. I am most used to statically typed 
   languages. My past programming experiences are primarily in Java and C; my first attempt at this course being my only saving grace for the coursework. There is still much for me to refine in my own JavaScript/TypeScript knowledge, however, I 
   do wholeheartedly look forward to expanding that knowledge.
   
   While last semester was a particularly tempestuous period of time for me, I do recall learning JavaScript. I found that while it was leagues simpler than what I was used to, the dynamically typed nature of the language left me confused when 
   skimming through longer code. Sometimes, debugging would take longer than necessary simply because I was so used to variable being defined with types. Errors being caught at the time of compiling allows for less chance with runtime errors as 
   well, though I have not had a large enough project to fully experience this. Comparing two codes: 

### JavaScript
```javascript
function feelsLike(temp, humidity) {
    const feels = -42.379 +
        (2.049 * temp) +
        (10.143 * humidity) -
        (0.2247 * temp * humidity) -
        (0.006837 * temp * temp) -
        (0.054817 * humidity * humidity) +
        (0.001228 * temp * temp * humidity) +
        (0.0008528 * temp * humidity * humidity) -
        (0.00000199 * temp * temp * humidity * humidity);
    
    const fL = "feels like ";

    if (feels <= 79) {
        return fL + feels + ": OK";
    } else if (feels >= 80 && feels <= 90) {
        return fL + feels + ": Caution";
    } else if (feels >= 91 && feels <= 102) {
        return fL + feels + ": Extreme Caution";
    } else if (feels >= 103 && feels <= 125) {
        return fL + feels + ": Danger";
    } else {
        return fL + feels + ": Extreme Danger";
    }
}

```
***versus***
### Typescript
```typescript
function feelsLike(temp: number, humidity: number) {
    const feels: number = -42.379 +
    (2.049 * temp) +
    (10.143 * humidity) -
    (0.2247 * temp * humidity) -
    (0.006837 * temp * temp) -
    (0.054817 * humidity * humidity) +
    (0.001228 * temp * temp * humidity) +
    (0.0008528 * temp * humidity * humidity) -
    (0.00000199 * temp * temp * humidity * humidity);
    
    const fL: string = "feels like ";

    if (feels <= 79) {
        return fL + feels + ": OK";
    } else if (feels >= 80 && feels <= 90) {
        return fL + feels + ": Caution";
    } else if (feels >= 91 && feels <= 102) {
        return fL + feels + ": Extreme Caution";
    } else if (feels >= 103 && feels <= 125) {
        return fL + feels + ": Danger";
    } else return fL + feels + ": Extreme Danger";
}

```

In essence, both code snippets are the same, however, in TypeScript it is much easier to pinpoint what is what. Of course, this is an incredibly rudimentary example, I look forward for the opportunity to work on larger projects using what I am 
currently learning. Where I used `` feelsLike(temp: number, humidity: number)`` in TypeScript is instead `` feelsLike(temp, humidity)`` in JS. It may be obvious, however, there is little clarification in the JavaScript snippet. 

As the semester progresses, I hope to use both languages more. My understanding is still loose, especially in programming as a whole, so this offers me a an opportunity to ~~lock in~~ better my understanding while improving the bad habits I made 
over time. 
