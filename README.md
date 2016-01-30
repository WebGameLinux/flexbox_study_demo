# Flexbox布局

学习Flexbox布局。书上给出的图片不是十分理解，下图更容易理解：
![Alt text](http://www.ruanyifeng.com/blogimg/asset/2015/bg2015071004.png)  
容器默认存在两根轴：水平的主轴（main axis）和垂直的交叉轴（cross axis）。主轴的开始位置（与边框的交叉点）叫做main start，结束位置叫做main end；交叉轴的开始位置叫做cross start，结束位置叫做cross end。
项目默认沿主轴排列。单个项目占据的主轴空间叫做main size，占据的交叉轴空间叫做cross size

### 容器的属性
依次学习以下容器的6个属性
- flex-direction
- flex-wrap
- flex-flow
- justify-content
- align-items
- align-content
#### flex-direction
flex-direction属性决定主轴的方向（即项目的排列方向）。
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Flexbox布局----flex-direction</title>
    <style>
        .flex{
            width: 350px;
            height: 200px;
            border: 1px solid #555;
        }
        .flex_row{
            display: flex;
            flex-direction: row; /*主轴为水平方向,起点在左端*/
        }
        .flex_row_reverse{
            display: flex;
            flex-direction: row-reverse;/*主轴为水平方向,起点在右端*/
        }
        .flex_column{
            display: flex;
            flex-direction: column;/*主轴为垂直方向,起点在上端*/
        }
        .flex_column_reverse{
            display: flex;
            flex-direction: column-reverse;/*主轴为垂直方向,起点在下端*/
        }
        .flex_item{
            width: 80px;
            height: 80px;
            margin: 5px;
            background : #009246;

            display: flex;
            align-items: center;    /*垂直居中*/
            justify-content: center;  /*水平居中*/
        }
    </style>
</head>
<body>
    <p>flex-direction:row(default)</p>
    <div class="flex flex_row">
        <div class="flex_item">one</div>
        <div class="flex_item">two</div>
        <div class="flex_item">three</div>
    </div>

    <p>flex-direction:flex_row_reverse</p>
    <div class="flex flex_row_reverse">
        <div class="flex_item">one</div>
        <div class="flex_item">two</div>
        <div class="flex_item">three</div>
    </div>

    <p>flex-direction:column</p>
    <div class="flex flex_column">
        <div class="flex_item">one</div>
        <div class="flex_item">two</div>
        <div class="flex_item">three</div>
    </div>

    <p>flex-direction:row_column_reverse</p>
    <div class="flex flex_column_reverse">
        <div class="flex_item">one</div>
        <div class="flex_item">two</div>
        <div class="flex_item">three</div>
    </div>
</body>
</html>
```
总结：把主轴当作x轴坐标，此属性就是x轴的方向。
#### flex-wrap
默认情况下，项目都排在一条线（又称"轴线"）上。flex-wrap属性定义，如果一条轴线排不下，如何换行。
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Flexbox布局----flex-wrap</title>
    <style>
        .flex{
            width: 350px;
            height: 200px;
            border: 1px solid #555;
            display: flex;
            flex-direction: row; /*主轴为水平方向,起点在左端*/
        }
        .flex_nowrap{
            flex-wrap: nowrap;  /*不换行*/
        }
        .flex_wrap{
            flex-wrap: wrap;  /*换行*/
        }
        .flex_wrap_reverse{
            flex-wrap: wrap-reverse;  /*换行,第一行在下方*/
        }
        .flex_item{
            width: 80px;
            height: 80px;
            margin: 5px;
            background : #009246;

            display: flex;
            align-items: center;    /*垂直居中*/
            justify-content: center;  /*水平居中*/
        }
    </style>
</head>
<body>
    <p>flex-wrap:nowrap(default)</p>
    <div class="flex flex_nowrap">
        <div class="flex_item">one</div>
        <div class="flex_item">two</div>
        <div class="flex_item">three</div>
        <div class="flex_item">four</div>
        <div class="flex_item">five</div>
    </div>

    <p>flex-wrap:wrap</p>
    <div class="flex flex_wrap">
        <div class="flex_item">one</div>
        <div class="flex_item">two</div>
        <div class="flex_item">three</div>
        <div class="flex_item">four</div>
        <div class="flex_item">five</div>
    </div>

    <p>flex-wrap:wrap_reverse</p>
    <div class="flex flex_wrap_reverse">
        <div class="flex_item">one</div>
        <div class="flex_item">two</div>
        <div class="flex_item">three</div>
        <div class="flex_item">four</div>
        <div class="flex_item">five</div>
    </div>
</body>
</html>
```
#### flex-flow
flex-flow属性是flex-direction属性和flex-wrap属性的简写形式，默认值为row nowrap
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Flexbox布局----flex-flow</title>
    <style>
        .flex{
            width: 350px;
            height: 200px;
            border: 1px solid #555;
            display: flex;
            flex-flow: row wrap-reverse; /*主轴为水平方向,起点在左端;换行,首行在下方*/
        }
        .flex_item{
            width: 80px;
            height: 80px;
            margin: 5px;
            background : #009246;

            display: flex;
            align-items: center;    /*垂直居中*/
            justify-content: center;  /*水平居中*/
        }
    </style>
</head>
<body>
    <p>flex-flow:row wrap_reverse</p>
    <div class="flex">
        <div class="flex_item">one</div>
        <div class="flex_item">two</div>
        <div class="flex_item">three</div>
        <div class="flex_item">four</div>
        <div class="flex_item">five</div>
    </div>
</body>
</html>
``` 
#### justify-content
justify-content属性定义了项目在主轴上的对齐方式。
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Flexbox布局----justify-content</title>
    <style>
        .flex{
            width: 350px;
            height: 200px;
            border: 1px solid #555;
            display: flex;
            flex-flow: row nowrap;
        }
        .flex_start{
            justify-content: flex-start; /*左对齐*/
        }
        .flex_end{
            justify-content: flex-end;  /*右对齐*/
        }
        .flex_center{
            justify-content: center;   /*居中对齐*/
        }
        .flex_between{
            justify-content: space-between; /*平均分布在主轴上,开始位置为主轴起始点,结束位置为主轴终点*/
        }
        .flex_around{
            justify-content: space-around; /*平均分布在主轴上,但是两端保留一半的空间*/
        }
        .flex_item{
            height: 80px;
            margin: 0px 5px;
            background : #009246;

            display: flex;
            align-items: center;    /*垂直居中*/
            justify-content: center;  /*水平居中*/
        }
        .one{
            width: 80px;
        }
        .two{
            width: 50px;
        }
        .three{
            width: 90px;
        }
    </style>
</head>
<body>
    <p>justify-content:flex_start(default)</p>
    <div class="flex flex_start">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
    </div>
    <p>justify-content:flex_end</p>
    <div class="flex flex_end">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
    </div>
    <p>justify-content:center</p>
    <div class="flex flex_center">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
    </div>
    <p>justify-content:flex_between</p>
    <div class="flex flex_between">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
    </div>
    <p>justify-content:flex_around</p>
    <div class="flex flex_around">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
    </div>
</body>
</html>
```
#### align-items
align-items属性定义项目在交叉轴上如何对齐。
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Flexbox布局----align-items</title>
    <style>
        .flex{
            width: 350px;
            height: 200px;
            border: 1px solid #555;
            display: flex;
            flex-flow: row nowrap;
        }
        .flex_start{
            align-items: flex-start;
        }
        .flex_end{
            align-items: flex-end;
        }
        .flex_center{
            align-items: center;
        }
        .flex_stretch{
            align-items: stretch;
        }
        .flex_baseline{
            align-items: baseline;,
        }
        .flex_item{
            width: 80px;
            margin: 0px 5px;
            background : #009246;

            display: flex;
            align-items: center;    /*垂直居中*/
            justify-content: center;  /*水平居中*/
        }
        .one{
            height: 80px;
        }
        .two{
            height: 50px;
        }
        .three{
            height: 90px;
        }
    </style>
</head>
<body>
    <p>align-items:flex_start</p>
    <div class="flex flex_start">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
    </div>
    <p>align-items:flex_end</p>
    <div class="flex flex_end">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
    </div>
    <p>align-items:flex_center</p>
    <div class="flex flex_center">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
    </div>
    <p>align-items:flex_stretch</p>
    <div class="flex flex_stretch">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
    </div>
    <p>align-items:flex_baseline</p>
    <div class="flex flex_baseline">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
    </div>
</body>
</html>
```
#### align-content
align-content属性定义了多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用。
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Flexbox布局----align-content</title>
    <style>
        .flex{
            width: 350px;
            height: 200px;
            border: 1px solid #555;
            display: flex;
            flex-flow: row wrap;
        }
        .flex_start{
            align-content: flex-start;  /*与交叉轴的起点对齐*/
        }
        .flex_end{
            align-content: flex-end;    /*与交叉轴的终点对齐*/
        }
        .flex_center{
            align-content: center;      /*与交叉中的中点对齐*/
        }
        .flex_stretch{
            align-content: stretch;
        }
        .flex_between{
            align-content: space-between;,
        }
        .flex_around{
            align-content: space-around;
        }
        .flex_item{
            height: 60px;
            margin: 5px;
            background : #009246;

            display: flex;
            align-items: center;    /*垂直居中*/
            justify-content: center;  /*水平居中*/
        }
        .one{
            width: 80px;
        }
        .two{
            width: 50px;
        }
        .three{
            width: 90px;
        }
        .four{
            width: 70px;
        }
        .five{
            width: 60px;
        }
    </style>
</head>
<body>
    <p>align-content:flex_start</p>
    <div class="flex flex_start">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
        <div class="flex_item four">four</div>
        <div class="flex_item five">five</div>
    </div>
    <p>align-content:flex_end</p>
    <div class="flex flex_end">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
        <div class="flex_item four">four</div>
        <div class="flex_item five">five</div>
    </div>
    <p>align-content:flex_center</p>
    <div class="flex flex_center">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
        <div class="flex_item four">four</div>
        <div class="flex_item five">five</div>
    </div>
    <p>align-content:flex_stretch(default)</p>
    <div class="flex flex_stretch">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
        <div class="flex_item four">four</div>
        <div class="flex_item five">five</div>
    </div>
    <p>align-content:flex_between</p>
    <div class="flex flex_between">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
        <div class="flex_item four">four</div>
        <div class="flex_item five">five</div>
    </div>
    <p>align-content:flex_around</p>
    <div class="flex flex_around">
        <div class="flex_item one">one</div>
        <div class="flex_item two">two</div>
        <div class="flex_item three">three</div>
        <div class="flex_item four">four</div>
        <div class="flex_item five">five</div>
    </div>
</body>
</html>
```
> **总结：**以上6个属性设置的是容器的布局方式。将主轴、交叉轴想象成二位坐标即可。

### 项目的属性
依次学习以下容器的6个属性
- order
- flex-grow
- flex-shrink
- flex-basis
- flex
- align-self
#### order
order属性定义项目的排列顺序。数值越小，排列越靠前，默认为0。
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Flexbox布局----order</title>
    <style>
        .flex{
            width: 350px;
            height: 200px;
            border: 1px solid #555;
            display: flex;
            flex-flow: row wrap;
        }
        .flex_item{
            height: 80px;
            width: 60px;
            margin: 5px;
            background : #009246;

            display: flex;
            align-items: center;    /*垂直居中*/
            justify-content: center;  /*水平居中*/
        }
        .one{
            order: 2;
        }
        .two{
            order: 1;
        }
        .three{
            order: 0;   /*第二个显示*/
        }
        .four{
            order: 3
        }
        .five{
            order: -1;  /*第一个显示*/
        }
    </style>
</head>
<body>
<p>order</p>
<div class="flex">
    <div class="flex_item one">one</div>
    <div class="flex_item two">two</div>
    <div class="flex_item three">three</div>
    <div class="flex_item four">four</div>
    <div class="flex_item five">five</div>
</div>
</body>
</html>
```
#### flex-grow
flex-grow属性定义项目的放大比例，默认为0。
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Flexbox布局----flex-grow</title>
    <style>
        .flex{
            width: 350px;
            height: 200px;
            border: 1px solid #555;
            display: flex;
            flex-flow: row wrap;
        }
        .flex_item{
            height: 80px;
            width: 90px;
            margin: 5px;
            background : #009246;

            display: flex;
            align-items: center;    /*垂直居中*/
            justify-content: center;  /*水平居中*/
        }
        .grow{
            flex-grow: 2;
        }
    </style>
</head>
<body>
<p>flex-grow(default:0)</p>
<div class="flex">
    <div class="flex_item">1</div>
    <div class="flex_item grow">2</div>
    <div class="flex_item">1</div>
    <div class="flex_item">1</div>
    <div class="flex_item grow">2</div>
</div>
</body>
</html>
```
#### flex-shrink
flex-shrink属性定义了项目的缩小比例，默认为1。
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Flexbox布局----flex-shrink</title>
    <style>
        .flex{
            width: 350px;
            height: 200px;
            border: 1px solid #555;
            display: flex;
            flex-flow: row nowrap;
        }
        .flex_item{
            height: 80px;
            width: 90px;
            margin: 5px;
            background : #009246;

            display: flex;
            align-items: center;    /*垂直居中*/
            justify-content: center;  /*水平居中*/
        }
        .shrink{
            flex-shrink: 3;     /*空间不足缩小为其他项目1/3*/
        }
    </style>
</head>
<body>
<p>flex-shrink(default:1)</p>
<div class="flex">
    <div class="flex_item">1</div>
    <div class="flex_item">1</div>
    <div class="flex_item">1</div>
    <div class="flex_item">1</div>
    <div class="flex_item shrink">3</div>
</div>
</body>
</html>
```
#### flex
flex属性是flex-grow, flex-shrink 和 flex-basis的简写，默认值为0 1 auto。该属性还有两个快捷值：auto(即1 1 auto)和none(即0 0 auto)
``` html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Flexbox布局----flex</title>
    <style>
        .flex{
            width: 350px;
            height: 200px;
            border: 1px solid #555;
            display: flex;
            flex-flow: row nowrap;
        }
        .flex_item{
            height: 80px;
            width: 90px;
            margin: 5px;
            background : #009246;

            display: flex;
            align-items: center;    /*垂直居中*/
            justify-content: center;  /*水平居中*/
        }
        .flex_flex {
            flex: 1;    /*相当于flex-grow:1*/
        }
        .flex_auto{
            flex: auto;  /*相当于1 1 auto*/
        }
        .flex_none{
            flex: none;  /*相当于0 0 auto*/
        }
    </style>
</head>
<body>
    <p>flex:1</p>
    <div class="flex">
        <div class="flex_item">one</div>
        <div class="flex_item">two</div>
        <div class="flex_item flex_flex">three</div>
    </div>
    <p>flex:auto</p>
    <div class="flex">
        <div class="flex_item">one</div>
        <div class="flex_item">two</div>
        <div class="flex_item flex_auto">three</div>
    </div>
    <p>flex:none</p>
    <div class="flex">
        <div class="flex_item">one</div>
        <div class="flex_item">two</div>
        <div class="flex_item flex_none">three</div>
    </div>
</body>
</html>
```
#### align-self
align-self属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。


[1]:https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Flexible_Box_Layout/Using_CSS_flexible_boxes
[2]:http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html


参考链接：
- [Flex 布局教程：语法篇](http://www.ruanyifeng.com/blog/2015/07/flex-grammar.html)
- [Flex 布局教程：实例篇](http://www.ruanyifeng.com/blog/2015/07/flex-examples.html)(TODO)
- [React Native](http://item.jd.com/11844102.html)(京东)
