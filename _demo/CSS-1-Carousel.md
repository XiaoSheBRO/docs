# CSS轮播图样式

<!-- #region demo -->

::: normal-demo CSS轮播图样式

```html
<style>
  .carousel {
    position: relative;
    margin: 0 auto;
    width: 300px;
    height: 200px;
    overflow: hidden;
  }

  .img-container {
    width: 900px;
    height: 200px;
  }

  .carousel-item {
    float: left;
    width: 300px;
    height: 200px;
  }

  .left-btn,
  .right-btn {
    position: absolute;
    top: 0;
    bottom: 0;
    margin: auto 0;
    width: 30px;
    height: 30px;
    line-height: 30px;
    font-size: 18px;
    font-family: Arial, sans-serif;
    text-align: center;
    background-color: #ffffff77;
    border-radius: 50%;
  }

  .left-btn {
    left: 10px;
  }
  .right-btn {
    right: 10px;
  }
</style>
<div class="carousel">
  <div class="img-container">
    <img class="carousel-item" src="https://picsum.photos/300/200.webp?random=1" />
    <img class="carousel-item" src="https://picsum.photos/300/200.webp?random=2" />
    <img class="carousel-item" src="https://picsum.photos/300/200.webp?random=3" />
  </div>
  <div class="left-btn">&#9204;</div>
  <div class="right-btn">&#9205;</div>
</div>
```

<!-- #endregion demo -->
