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

That doesn't sound very good because of one of the [20 golden rules of formating knowledge](https://www.supermemo.com/en/articles/20rules) is to avoid lists. One of the reasons is that remembering lists is tough.

Consider you are asked to remember the diagnostic standard of *Hypertrophic Cardiomyopathy*. The rules are listed on your professor's slides and no matter how many times you read this diagnosis standard, you just can't drill it into your head.
Why? Because this list is randomized in order. There's no procedural hint that will help you to get what's next on it. You just have to depend on repetition. However, I have to say that this example is a little bit different from the one listed on the top of this passage. But I will discuss it more in the future.

## Is there a better way to remember?
That's what I'm looking for. Actually, we don't need to remember the orders of the list.

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
  var result = new Array(len);
  for (j=1; j < ArrLen + 1; j++){
    result[j-1] = arr[r.indexOf(o[j], 1) - 1];
  }
  return result;
}
```
