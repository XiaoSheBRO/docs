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

  .carousel .img-container {
    width: 900px;
    height: 200px;
  }

  .carousel .img-container .carousel-item {
    float: left;
    width: 300px;
    height: 200px;
  }

  .carousel .img-container .carousel-item:nth-child(1) {
    margin-left: -300px;
  }

  .carousel .left-btn,
  .carousel .right-btn {
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

  .carousel .left-btn:hover,
  .carousel .right-btn:hover {
    background-color: #ffffffff;
    cursor: pointer;
  }

  .carousel .left-btn {
    left: 10px;
  }

  .carousel .right-btn {
    right: 10px;
  }

  .carousel .modal {
    position: absolute;
    bottom: 0;
    left: 0;
    box-sizing: border-box;
    padding: 0 20px;
    width: 100%;
    height: 40px;
    color: #ffffff;
    line-height: 40px;
    background-color: rgba(0, 0, 0, 0.3);
  }

  .carousel .modal .title {
    float: left;
    font-size: 16px;
    font-weight: bold;
  }

  .carousel .modal .dots {
    float: right;
  }

  .carousel .modal .dots .dot {
    display: inline-block;
    margin-right: 5px;
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background-color: #eee;
    cursor: pointer;
  }

  .carousel .modal .dots .dot.active {
    background-color: #369;
  }

  .carousel .modal .dots .dot:hover {
    background-color: #369;
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
  <div class="modal">
    <div class="title">title</div>
    <div class="dots">
      <span class="dot"></span>
      <span class="dot active"></span>
      <span class="dot"></span>
    </div>
  </div>
</div>
```

<!-- #endregion demo -->
