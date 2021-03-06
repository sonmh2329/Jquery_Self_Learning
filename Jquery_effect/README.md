# Jquery effect

[I. Jquery Hide and Show](#i-jquery-hide-and-show)

[II. Jquery Fade](#ii-jquery-fade)

[III. Jquery Slide](#iii-jquery-slide)

[IV. Jquery Animate](#iv-jquery-animate)

[V. Jquery Stop](#v-jquery-stop)

## I. Jquery Hide and Show

### 1. Hide and show

**Syntax:**

```javascript
    $(selector).hide(speed, callback);
    $(selector).show(speed, callback);
```

Trong đó `speed` để define tốc độ hide và show với các option:

- `"slow"`
- `"fast"`
- `miliseconds` ví dụ 1000 (1s)

Và `callback` thực hiện function nào đó sau khi `hide` và `show` method complete.

**Ví dụ:**

```html

    <p>This is the content wich can hide and show</p>
    <button id="hide">Hide</button>
    <button id="show">Show</button>
    <script>
        $(function() {
            $("hide").click(function() {
                $("p").hide("slow");
            });
            $("show").click(function() {
                $("p").show(1000);
            });

        })
    </script>
```

Khi ấn vào button hide nó sẽ ẩn `<p>` đi từ từ còn khi ấn vào button show nó sẽ hiện `<p>` ra sau 1s.

### 2. Jquery Toggle()

Chúng ta có thể chuyển đối giữa `hide` và `show` bằng toggle method. Tức là ban đầu element được selected sẽ `show`, click lần 1 sẽ `hide` đi và click lần nữa sẽ lại `show` ...

**Syntax:**

```javascript
    $(selector).toggle(speed, callback);
```

**Ví dụ:**

```html
    <p>This content is togglable</p>
    <button id="toggle">Show and hide toggle</button>
    <script>
        $(function() {
            $("toggle").click(function() {
                $("p").toggle();
            })
        })
    </script>
```

**Lưu ý:** Không nên đặt toggle trực tiếp lên click event của element cần đc toggle vì khi `hide` đi là nó biến mất, k click để `show` được nữa

## II. Jquery Fade

Với Jquery ta có thể fade element khi ẩn và hiện

Jquery gồm các fade method sau:

- fadeIn()
- fadeOut()
- fadeToggle()
- fadeTo()

### 1. Jquery fadeIn() và fadeOut() method

`fadeIn` dùng để tạo hiệu ứng `fade in` cho hidden element và ngược lại `fadeOut` để tạo hiệu ứng khi ấn element đi

**Syntax:**

```javascript
    $(selector).fadeIn(speed, callback);
    $(selector).fadeOut(speed, callback);

```

**Ví dụ:**

```html
    <div style="width:50px;height:50px;background-color:red;display:none"></div>
    <button id="btn1">Click me to fade in content</button>
    <button id="btn2">Click me to fade out content</button>
    <script>
        $(function() {
            $("#btn1").click(function() {
                $("div").fadeIn("slow");
            });
            $("#btn2").click(function() {
                $("div").fadeOut(3000);
            })
        })
    </script>
```

### 2. fadeToggle()

`fadeToggle` cũng có chức năng tương tự như `toggle` method nhưng thêm hiệu ứng fade.

**Syntax:**

```javascript
    $(selector).fadeToggle(speed, callback);
```

**Ví dụ:**

```html
    <div style="width:50px;height:50px;background-color:red;display:none"></div>
    <button>Click me to fade in/out content</button>
    <script>
        $(function() {
            $("button").click(function() {
                $("div").fadeToggle(3000);
            })
        })
    </script>
```

### 3. fadeTo()

`fadeTo()` cho phép element fading với opacity.

**Syntax:**

```javascript
    $(selector).fadeTo(speed, opacity, callback)
```

Trong đó `opacity` nằm trong đoạn từ `0 - 1`

**Ví dụ:**

```html
    <div style="width:50px;height:50px;background-color:red;display:none"></div>
    <button>Click me to fade in/out content</button>
    <script>
        $(function() {
            $("button").click(function() {
                $("div").fadeTo(3000,0.5);
            })
        })
    </script>
```

Ví dụ trên sẽ làm `<div>` fading từ trạng thái `hide`( opacity = 0) sang hiện ra với `opacity=0.5`
muốn hiện ra hoàn toàn thì `opacity=1`

## III. Jquery Slide

Cho phép slide element up và down

bao gồm:

- `slideDown()`
- `slideUp()`
- `slideToggle()`

### 1. Jquery slideDown() và slideUp

Giúp element hiện ra hay ẩn đi với slide effect

**Syntax:**

```javascript
    $(selector).slideDown(speed, callback)
    $(selector).slideUp(speed, callback)
```

**Ví dụ:**

```html
    <div id="flip" style="width:100%;height:20px;background-color:black;color:white;">slide flip</div>
    <div id="panel" style="display:none">Hello</div>
    <script>
        $("#flip").click(function() {
            $("#panel").slideDown(3000);
        });
        $("#flip").click(function() {
            $("#panel").slideUp(3000);
        });
    </script>
```

### 2. Jquery slideToggle()

Giúp element toggle between `slideUp` và `slideDown`

**Syntax:**

```javascript
    $(selector).slideToggle(speed, callback);
```

**Ví dụ:**

```html
    <div id="flip" style="width:100%;height:20px;background-color:black;color:white;">slide flip</div>
    <div id="panel" style="display:none">Hello</div>
    <script>
        $("#flip").click(function() {
            $("#panel").slideToggle(3000);
        });
    </script>
```

## IV. Jquery Animate

### 1. Khái niệm và cơ bản

`animate()` method dùng để tạo custom animations

**Syntax:**

```javascript
    $(selector).animate({params},speed, callback);
```

Tham số `params` là CSS properties để được animated, các tham số còn lại giống như các ví dụ trước.

**Ví dụ:**

```html
        <style>
            div {
                background-color: green;
                width: 50px;
                height: 50px;
                position: absolute;
            }
        </style>
    </head>
    <body>
        <button>Click me to see animate</button>
        <div></div>
        <script>
            $(function() {
                $("button").click(function() {
                    $("div").animate({left:'250px'}, "slow");
                })
            })
        </script>
```

Default, tất cả HTML elements đều có static position cho nên không thể di chuyển được, vì vậy để có thể sử dụng animate thì cần set `positon` của element thành `absolute` hoặc `relative`...

Ví dụ trên sẽ làm cho ô `div` move từ vị trí ban đầu đến vị trí cách trái 250px tức là di chuyển về bên phải 250px

Có thể sử dụng nhiều effect trong animate.

**Ví dụ:**

```html
    <style>
            div {
                background-color: green;
                width: 50px;
                height: 50px;
                position: absolute;
            }
        </style>
    </head>
    <body>
        <button>Click me to see animate</button>
        <div></div>
        <script>
            $(function() {
                $("button").click(function() {
                    $("div").animate({
                        left:'250px',
                        width: '200px',
                        height: '200px',
                        opacity: '0.5'
                    });
                })
            })
        </script>
```

Ví dụ trên sẽ làm cho `div` dịch chuyển sang phải và to lên thành 200px với opacity là 0.5

**Lưu ý:** tất cả properties names trong anime phải ở dạng camel case ví dụ ta sẽ phải sử dụng paddingLeft thay vì padding-left hay marginRight thay vì margin-right

### 2. animte() với relative value

Ta có thể thêm `+=` hoặc `-=` vào animate.

**Ví dụ:**

```html

    <style>
            div {
                background-color: green;
                width: 50px;
                height: 50px;
                position: absolute;
            }
        </style>
    </head>
    <body>
        <button>Click me to see animate</button>
        <div></div>
        <script>
            $(function() {
                $("button").click(function() {
                    $("div").animate({
                        left:'250px',
                        width: '+=200px',
                        height: '+=200px',
                        opacity: '0.5'
                    });
                })
            })
        </script>
```

Như vậy animate từ `div` với 50px width-height lên 250px width-height do cộng thêm 200px

### 3. Sử dụng animate với các Pre-defined value

Có thêm thêm các animate value như `"show"`, `"hide"` hay   "`toggle`"

**Ví dụ:**

```html
    <style>
            div {
                background-color: green;
                width: 50px;
                height: 50px;
                position: absolute;
            }
        </style>
    </head>
    <body>
        <button>Click me to see animate</button>
        <div></div>
        <script>
            $(function() {
                $("button").click(function() {
                    $("div").animate({
                        height: "toggle"
                    });
                })
            })
        </script>

```

Khi click vào button `div` sẽ có effect `toggle` giữa `hide` và `show` theo chiều dọc, tương tự nếu để `width: "toggle"` ta sẽ có animate toggle theo chiều ngang

### 4. jQuery animate() - Uses Queue Functionality

By default, jquery animate diễn ra nối tiếp nhau tức là nếu như theo nhiều animate nối tiếp nhau thì khi executed chúng cũng sẽ diễn ra nối tiếp nhau

**Ví dụ:**

```javascript

    $("button").click(function(){
        var div = $("div");
        div.animate({height: '300px', opacity: '0.4'}, "slow");
        div.animate({width: '300px', opacity: '0.8'}, "slow");
        div.animate({height: '100px', opacity: '0.4'}, "slow");
        div.animate({width: '100px', opacity: '0.8'}, "slow");
}); 
```

Xem trong file:

[Ví dụ 1](./jquery_animate_example1.html)

[Ví dụ 2](./jquery_animate_example2.html)




## V. Jquery Stop

`stop` method dùng để dừng các effect trước khi chúng được hoàn thành

**Syntax:**

```javascript
    $(selector).stop(stopAll,goToEnd);
```

Trong đó các tham số:

- `stopAll` có nghĩa là có dừng tất cả các animation trong `queue` animation không. Default là `false`. Có nghĩa là chỉ dừng animation mà đang được active các animation khác trong queue vẫn được thực hiện bình thường.

- `goToEnd` có nghĩa là có đi đến trạng thái complete ngay animation hiện tại không. Default là `false` tức là khi bấm dừng thì nó sẽ dữ nguyên trạng thái hiện tại của element còn nếu là `true` thì element sẽ ngay lập tức reach trạng thái cuối cùng của effect.

Xem ví dụ trong file:

[stop example](./stop_example.html)

## VI. Jquery callback

Bình thường, javascript chạy line by line tuy nhiên đối với jquery effect, function nào đó đặt sau effect code có thể chạy trước khi effect được hoàn thành. Việc đó sẽ dẫn đến một số lỗi không mong muốn.

Vì vậy trong các effect thường có `callback` parameter để function có thể chạy sau khi effect hoàn thành.

**Ví dụ:** chúng ta muốn sau khi `div` hide thì mới có thông báo rằng `div` đã hide. Nếu như chúng ta code như thường mà không dùng call back

```html
    <p>This content can hide</p>
    <button>Click me to hide content</button>
    <script>
        $(function(){
            $("button").click(function() {
                $("p").hide();
                alert("the content is hidden");
            });
        })
    </script>
```

Nếu như dùng callback:

```html
    <p>This content can hide</p>
    <button>Click me to hide content</button>
    <script>
        $(function(){
            $("button").click(function() {
                $("p").hide("slow", function() {
                    alert("the content is hidden");
                });
            });
        })
    </script>
```

Xem ví dụ trong:

[callback example](./callback_example.html)

## VII. Chaining

Ta có thể dùng chaining để thêm nhiều effect cho một element bằng cách sau:

```javascript
    $("#p1").css("color", "red")
    .slideUp(2000)
    .slideDown(2000)
    .hide(1000, function() {
        alert("finish")
    });
```

Xem trong file:

[chaining_example](./chaining_example.html)

Tham khảo tại:

[Jquery effects](https://www.w3schools.com/jquery/jquery_ref_effects.asp)