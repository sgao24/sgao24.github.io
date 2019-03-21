---
layout: post
title: "Random List for Multiple Choice Questions"
date: 2019-03-19
---
Last Sunday, when I was just working on my `Anki` flashcards, I came across one card like this:

> LIST: Albumin, Globulin, Cholesterol, Lecithin, Fibrinogen

> Question 1: Of these proteins, which ones have a relatively GREATER number of negative charges?
> Question 2: Of these proteins, which ones have a relatively SMALLER number of negative charges?

## How can we learn this piece of knowledge?

Well, the most common way that came to our mind might be that "why don't we just remember two lists of proteins? One for the proteins that have greater negative charges, the other for the proteins containing smaller negative charges.

That part of knowledge becomes:
>

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
