---

layout: post

title: "bigfoot.js를 활용한 각주 기능 테스트"

---

bigfoot을 이용하여 각주를 예쁘게 만들고 있다. [^1]: 이렇게 하면 된다는데?

이게 된다면 본문으로 돌아가는 기능을 위해 또 수정해야 한다.

```
<script type="text/javascript" src="/js/jquery-3.3.1.js"></script>
<script type="text/javascript" src="/js/bigfoot.min.js"></script>
<script src="http://code.jquery.com/jquery-1.10.2.js"></script>
<script type="text/javascript">
        var bigfoot = $.bigfoot(
                       {
                       actionOriginalFN: "ignore",
                       positionContent: "true"
                       }
        );
</script>
```
[^]: 이거야?

[^]: 아이디는안써?