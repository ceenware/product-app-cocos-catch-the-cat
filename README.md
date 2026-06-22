# 小猫围格挑战

站点地址：https://ceenware.github.io/product-app-cocos-catch-the-cat/

抖音开放平台小游戏项目。

## 平台信息

- 仓库：ceenads/product-app-cocos-catch-the-cat
- 抖音小游戏名称：小猫围格挑战
- AppID：ttadb7db0a33d375a902
- 当前状态：基础信息已保存草稿，待上传版本和资质
- 创建日期：2026-06-14
- 开发引擎：普通小游戏引擎(Cocos/Laya/Egret/Godot/其他)
- 平台图标：抖音上架材料/icon-600.png
- 小游戏分类：休闲益智 / 解谜
- 题材标签：动物

## 软著信息

- 软件全称：小猫围格挑战游戏软件 V1.0
- 软件简称：小猫围格挑战

## 提交记录

2026-06-14：抖音开放平台创建流程已接受名称“小猫围格挑战”，生成 AppID `ttadb7db0a33d375a902`。
2026-06-14：基础信息已在抖音开放平台保存为草稿，分类为“休闲益智 / 解谜”，题材标签为“动物”，图标使用 `抖音上架材料/icon-600.png`。

[开始游戏](https://ganlvtech.github.io/phaser-catch-the-cat/)
[![Build Status](https://www.travis-ci.org/ganlvtech/phaser-catch-the-cat.svg?branch=master)](https://www.travis-ci.org/ganlvtech/phaser-catch-the-cat)

## 游戏玩法

* 点击小圆点，围住小猫。
* 你点击一次，小猫走一次。
* 直到你把小猫围住（赢），或者小猫走到边界并逃跑（输）。

## 部署

首先引入游戏框架 `phaser.min.js`

```html
<script src="phaser.min.js"></script>
```

然后引入游戏代码 `catch-the-cat.js`

```html
<script src="catch-the-cat.js"></script>
```

然后在指定的 div 中新建一个游戏的 canvas，并开始游戏

```html
<div id="catch-the-cat"></div>
<script>
    window.game = new CatchTheCatGame({
        w: 11,
        h: 11,
        r: 20,
        initialWallCount: 8,
        backgroundColor: 0xeeeeee,
        parent: 'catch-the-cat',
        statusBarAlign: 'center',
        credit: 'github.com/ganlvtech'
    });
</script>
```

参数列表：

| 参数  | 值    | 说明       |
| :---: | :---: | :--------- |
| w     | `11`  | 横向格子数 |
| h     | `11`  | 竖向格子数 |
| r     | `20`  | 圆半径像素 |

非必选参数：

| 参数            | 值                     | 说明                                |
| :-------------: | :--------------------- | :---------------------------------- |
| backgroundColor | `0xeeeeee`             | 背景颜色                            |
| parent          | `catch-the-cat`        | 父元素的 id 或 DOM 对象             |
| statusBarAlign  | `center`               | 状态栏左对齐 `left` 或居中 `center` |
| credit          | `github.com/ganlvtech` | 右下角的备注信息                    |

## 自己编写算法

参考 `src/solvers/` 中提供的例子编写算法，并使用下列代码替换。

```js
window.game.solver = yourSolver;
```

这个 solver 的返回值即为猫要往哪个方向走一步，如果撞墙则算玩家获胜

| 值 | 说明 |
| :--- | :---------------------- |
| -1 | 猫主动弃权 |
| 0  | 左 |
| 1  | 左上 |
| 2  | 右上 |
| 3  | 右 |
| 4  | 右下 |
| 5  | 左下 |

猫站在星号的位置，数字代表每个方向的编号

```plain
 1 2
0 * 3
 5 4
```

例如

```js
window.game.solver = function (blocksIsWall, i, j) {
    return 0;
};
```

即：一直向左走，直到撞墙。

## 说明

* 游戏的思路和小猫的图片来源于 [www.gamedesign.jp](https://www.gamedesign.jp/flash/chatnoir/chatnoir.html)，原来的游戏名叫 Chat Noir，我只是尝试用 javascript 重写一遍。

## License

MIT License
