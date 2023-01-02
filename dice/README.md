# 為Dice上色
## 如何在同個Mesh上不同顏色?
進入Edit模式中，選好你要是上色的區域，點選Assign即可

## 快速為製作同材質不同顏色的Material
1.Shift+D複製Mesh<br>
2.點一下該材質的數字按鈕，就可以將該材質獨立出來

## 增進材質的真實度

### 添加髒髒的紋理表面 ( Base Color )
- [Input]Texture Coordinate 
- [Vector]Mapping
- [Texture]Image Texture

### 增加次表面 (subsurface)
為何會需要次表面?<br>
由於我們已經將骯髒的圖形做成Base Color了，但想讓骰子整體有個底色，所以要使用次表面來呈現<br>
次表面將會和BaseColor的顏色混合
- subsurface : 控制次表面的顯示程度0-1 ( 0%~100% )
- subsurface Radius
- subsurface Col (次表面顏色)


### 調整粗糙度
有了骯髒紋路後，透過以下節點，控制這些骯髒紋路的顯示
- [Converter] Color Ramp 作為粗糙度的控制器，用來控制要顯示多少骯髒紋路
- [Color] MixRGB : 可以混合兩種顏色，藉以控制骯髒物的RGB色相(或明暗)

# 作業目標
- 製作出三種顏色的骰子
- Material的管理
- 骰子材質的邊緣不可以有明顯界線