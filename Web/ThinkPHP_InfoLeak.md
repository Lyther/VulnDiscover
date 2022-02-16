# ThinkPHP Information Leak

Discovered in ThinkPHP 5.0.24 default page.

While the `PATHINFO` hasn't been configured then ThinkPHP would receive parameter like `http://serverName/index.php?s=/ modular / controller / operation /[ Parameter name / Parameter values ...]`.

If the modular has not been found, system information would be a leak.

## PoC

Given the following request parameter in `index.php`:

```html
GET /index.php?s=example HTTP/1.1
```

![1.png](../Assets/Web_ThinkPHP_InfoLeak_1.png)

Got the following system information:

**Server/Request Data**

![2.png](../Assets/Web_ThinkPHP_InfoLeak_2.png)

**ThinkPHP Constants**

![3.png](../Assets/Web_ThinkPHP_InfoLeak_3.png)

## Summary

The default page of ThinkPHP has the problem of information leakage. Some sensitive system information is leaked.

