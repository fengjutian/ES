* Array 数组
* 数组去重  

```
function noRepeat(arr) {
    return [...new Set(arr)];
}
```
* 查找数组的最大值

```
function arrayMax(arr) {
    return Math.max(...arr);
}
```  

* 查找数组的最小值

```
function arrayMin(arr){
	return Math.min(...arr);
}
```

* 返回size为长度的数组分割的原数组  

```
function chunk(arr, size = 1) {
    return Array.from(
        {
            length: Math.ceil(arr.length / size);
        },
        (v, i) => arr.slice(i * size, i * size + size)
    )

}
```  

* 检查数组中某元素出现的次数

```
function countOccurrences(arr, value) {
    return arr.reduce((a, v) => (v === value ? a + 1 : a + 0), 0)
}
```

* 对比两个数组并且返回其中不同的元素

```
function diffrence(arrA, arrB) {
    return arrA.filter((v) => !arrB.includes(v))
}
```

* 返回两个数组中相同的元素

```
function intersection(arrA, arrB) {
   return arrA.filter((v) => arrB.includes(v)) 
}
```

* 范湖数组中下标间隔nth的元素

```
function everyNth(arr, nth) {
    return arr.filter((v, i) => i % nth === nth - 1);
}
```

* 获取滚动条位置

```
function getScrollPosition(el = window) {
  return {
    x: el.pageXOffset !== undefined ? el.pageXOffset : el.scrollLeft,
    y: el.pageYOffset !== undefined ? el.pageYOffset : el.scrollTop,
  };
}
```

* 滚动条回到顶部动画

```
function scrollToTop() {
  const scrollTop =
    document.documentElement.scrollTop || document.body.scrollTop;
  if (scrollTop > 0) {
    window.requestAnimationFrame(scrollToTop);
    window.scrollTo(0, c - c / 8);
  } else {
    window.cancelAnimationFrame(scrollToTop);
  }
}
```

* 判断当前位置是否为页面底部[返回值为 true/false]

```
function bottomVisible() {
  return (
    document.documentElement.clientHeight + window.scrollY >=
    (document.documentElement.scrollHeight ||
      document.documentElement.clientHeight)
  );
}
```

* 判断元素是否在可视范围内 [partiallyVisible 为是否为完全可见]

```
function elementIsVisibleInViewport(el, partiallyVisible = false) {
  const { top, left, bottom, right } = el.getBoundingClientRect();

  return partiallyVisible
    ? ((top > 0 && top < innerHeight) ||
        (bottom > 0 && bottom < innerHeight)) &&
        ((left > 0 && left < innerWidth) || (right > 0 && right < innerWidth))
    : top >= 0 && left >= 0 && bottom <= innerHeight && right <= innerWidth;
}
```

* 进入全屏

```
function launchFullscreen(element) {
  if (element.requestFullscreen) {
    element.requestFullscreen();
  } else if (element.mozRequestFullScreen) {
    element.mozRequestFullScreen();
  } else if (element.msRequestFullscreen) {
    element.msRequestFullscreen();
  } else if (element.webkitRequestFullscreen) {
    element.webkitRequestFullScreen();
  }
}

launchFullscreen(document.documentElement);
launchFullscreen(document.getElementById("id")); //某个元素进入全屏
```

* 退出全屏

```
function exitFullscreen() {
  if (document.exitFullscreen) {
    document.exitFullscreen();
  } else if (document.msExitFullscreen) {
    document.msExitFullscreen();
  } else if (document.mozCancelFullScreen) {
    document.mozCancelFullScreen();
  } else if (document.webkitExitFullscreen) {
    document.webkitExitFullscreen();
  }
}

exitFullscreen();
```

* 全屏事件

```
document.addEventListener("fullscreenchange", function (e) {
  if (document.fullscreenElement) {
    console.log("进入全屏");
  } else {
    console.log("退出全屏");
  }
});
```

* 检查浏览器是否支持某个css属性值（es6版）

```
/**
 * 检查浏览器是否支持某个css属性值（es6版）
 * @param {String} key - 检查的属性值所属的css属性名
 * @param {String} value - 要检查的css属性值（不要带前缀）
 * @returns {String} - 返回浏览器支持的属性值
 */
function valiateCssValue (key, value) {
    const prefix = ['-o-', '-ms-', '-moz-', '-webkit-', ''];
    const prefixValue = prefix.map(item => {
        return item + value;
    });
    const element = document.createElement('div');
    const eleStyle = element.style;
    // 应用每个前缀的情况，且最后也要应用上没有前缀的情况，看最后浏览器起效的何种情况
    // 这就是最好在prefix里的最后一个元素是''
    prefixValue.forEach(item => {
        eleStyle[key] = item;
    });
    return eleStyle[key];
}

```