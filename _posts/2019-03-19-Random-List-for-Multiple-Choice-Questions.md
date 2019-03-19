---
layout: post
title: "Random List for Multiple Choice Questions"
---

{% highlight HTML %}
<script type="text/javascript">
      function rand(arr){
        var len = arr.length;
        var r = new Array(len+1);
        for (i = 1; i < len+1; i++){
          r[i] = parseInt(Math.random() * 1000)
        }

        var o = new Array(len+1);
        o = r.slice();

        for (x = 1; x < len+1; x++){
          for (y = x+1; y < len+1; y++){
            if (r[x] > r[y]){
              r[0] = r[x];
              r[x] = r[y];
              r[y] = r[0];
            }  
          }
        }
        var result = new Array(len);
        for (j=1; j<len+1; j++){
          result[j-1] = arr[r.indexOf(o[j],1)-1];
        }
        return result;
      }
</script>
{% endhighlight %}
