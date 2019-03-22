---
layout: post
title: "Random List for Multiple Choice Questions"
date: 2019-03-19
---
Last Sunday, when I was just working on my `Anki` flashcards, I came across one card like this:

> LIST: Albumin, Globulin, Cholesterol, Lecithin, Fibrinogen
>
> Question 1: Of these proteins, which ones have a relatively GREATER number of negative charges?
>
> Question 2: Of these proteins, which ones have a relatively SMALLER number of negative charges?

## How can we learn this piece of knowledge?

Well, the most common way that came to our mind might be that "why don't we just remember two lists of proteins? One for the proteins that have greater negative charges, the other for the proteins containing smaller negative charges.

That piece of knowledge becomes to remember:
> - Greater negative charges: Albumin, Lecithin
> - Smaller negative charges: Globulin, Cholesterol, Fibrinogen

That doesn't sound very good because of one of the [20 golden rules of formating knowledge](https://www.supermemo.com/en/articles/20rules) is to avoid lists. One of the reasons is that remembering lists is really difficult and it is nearly impossible to maintain a high retention of a random list unless you apply some mnemonics or some other better tricks along with it.

Consider you are asked to remember the diagnostic standard of *Hypertrophic Cardiomyopathy*. The rules are listed on your professor's slides and no matter how many times you read this diagnosis standard, you just can't drill it into your head.

Why? Because this list is randomized in order. There's no procedural hint that will help you to get what's next on it. You just have to depend on repetition.

Now, let's go back to our example on the front of the passage. We can see that it is basically a kind of knowledge that doesn't need us to ***recall***, but it does need our ***recognition***.

## How to recognize?
There's an easy way to test us. Do multiple choice questions repetitively. But there's also a common problem when we do this: we are easily stuck into remembering the choices rather than the actual knowledge.

For example, let's say we have invented our multiple choice questions like this below:

> Which protein have GREATER negative charges?
>
> A. Albumin
> B. Cholesterol
> C. Globulin
> D. Fibrinogen

If we show this question below over and over again, it won't be long that you will automatically be looking at the `"A, B, C, D ..."` rather than focusing on the name of the proteins expecting our attention.

## Is there an easy way to tackle it?
That's what I'm looking for. We need the answer choices to be random. The answer may be "A" for the first time. But we need it to be **changed** as we review this question.

It's actually very easy. We need to create a randomized list, and make it for the flashcard. That's a simple code to write.

```javascript
function rand(arr){
  var ArrLen = arr.length;
  var r = new Array(ArrLen + 1);
  for (i = 1; i < ArrLen + 1; i++){
    r[i] = parseInt(Math.random() * 1000)
  }

  var o = new Array(ArrLen + 1);
  o = r.slice();

  for (x = 1; x < ArrLen + 1; x++){
    for (y = x+1; y < ArrLen + 1; y++){
      if (r[x] > r[y]){
        r[0] = r[x];
        r[x] = r[y];
        r[y] = r[0];
      }  
    }
  }
  var result = new Array(Arrlen);
  for (j=1; j < ArrLen + 1; j++){
    result[j-1] = arr[r.indexOf(o[j], 1) - 1];
  }
  return result;
}
```

So this code can change an **origin** *array* separated by `,` into a randomized **result** *array*, then we can show the result as a *bulleted list*.

Here's the screenshot.
![1](/assets/2019-3-22-1.png)
![2](/assets/2019-3-22-2.png)
