---
layout: post
title: "Random List for Multiple Choice Questions"
date: 2019-03-19
---

{% highlight JavaScript %}
<script type="text/javascript">
      function rand(arr){
        var ArrLen = arr.length;
        var r = new Array(ArrLen+1);
        for (i = 1; i < ArrLen+1; i++){
          r[i] = parseInt(Math.random() * 1000)
        }

        var o = new Array(ArrLen+1);
        o = r.slice();

        for (x = 1; x < ArrLen+1; x++){
          for (y = x+1; y < ArrLen+1; y++){
            if (r[x] > r[y]){
              r[0] = r[x];
              r[x] = r[y];
              r[y] = r[0];
            }  
          }
        }
        var result = new Array(len);
        for (j=1; j<ArrLen+1; j++){
          result[j-1] = arr[r.indexOf(o[j],1)-1];
        }
        return result;
      }
</script>
{% endhighlight %}
