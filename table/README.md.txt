# 教學影片
https://www.udemy.com/course/blender-environments/learn/lecture/32846802#overview
# 編輯材質
請進入 Shading 模式
# 製作步驟 :

## 為桌子添加照片材質
新增一個[Texture]Image Texture節點，並上傳完圖片後，將Color --> Principled BSDF 的 Base Color 即可<br>
*ps.記得把viewPort Shading 模式改為 Material Preview 就可以預覽效果囉

## 增加紋理座標控制節點
新增一個[Input]Texture Coordinate 節點、及[Vector]Mapping 節點，來控制座標的輸出<br>
1.選好[Input]Texture Coordinate的紋理輸入方式後，將該輸出連接到[Vector]Mapping的Vector<br>
2.[Vector]Mapping的Vector連接到[Texture]Image Texture的Vector

## 增加粗糙度貼圖 : 
1.新增一個[Texture]Image Texture節點，使用rough的圖片
2.將Color Space 改為 none-color
3.將[Vector]Mapping 的 Vector --> 連接到 該[Texture]Image Texture 的 Vector ( 使其座標能夠正常的Mapping到桌面上 )
4.為了可以控制粗糙度，新增一個 [Converter] Color Ramp
5.把該[Texture]Image Texture 的Color --> 連接到[Converter] Color Ramp 的Fac --> 再將 [Converter] Color Ramp 的Color 連接到Principled BSDF 的 Roughness 

## 增加法線貼圖 高度normal map :
讓我們可以呈現材質的凹凸
1.新增一個[Texture]Image Texture節點，使用nor的圖片
2.將[Vector]Mapping 的 Vector --> 連接到 該[Texture]Image Texture 的 Vector 
3.把該[Texture]Image Texture 的 Color --> 先連接[Vector]Normal Map 的 Color --> 再將[Vector]Normal Map 的 Normal 連接到 Principled BSDF 的 Normal 

ps. 在連接到Normal前為何需要一個<br>
因為從Image中輸出的是Color，而Normal接受的輸入是Vector，所以我們需要轉換器，將之計算為Vector。<br>
並且我們才可以透過[Vector]Normal Map 來控制凹凸的強度。

# 節點介紹
## 基本Material節點
- [Shader] Principled BSDF 節點 : 可以視為主要的Material著色器入口節點 <br>
- [Output] Material Output 節點 : 最終將Material輸出的節點

## Texture類節點
### Image Texture 節點 - 為Mesh貼上照片材質

## Input類節點
### Texture Coordinate 節點 - 紋理座標
可以選擇多種表達紋理座標的輸入方式，例如UV、Object等等...
通常會搭配[Vector]Mapping 節點，來達到控制座標的目的

## Vector 類節點
### Mapping 節點 - 
透過平移、旋轉、縮放來變換輸入的向量

# image 相關屬性名詞解說
### Roughness : 粗糙度 ( 又稱光澤度 )
主要控制著"反射"的銳利度，值從0-1 ( 完全銳利 / 非常柔和 )
也就是當光源照射下來後，會呈擴散狀的顯示在材質上
- albedo : 反照率
- diffuse : 擴散



# 快速製作適合的展開圖

最簡單的方式就是對著Mesh點右鍵，選擇Smart UV Project

## 英文單字

Shader : 著色器
coordinate : 聯合, 協調, 座標


# 練習目標 : 
為這張桌子貼上材質，必須要有Roughness、Normal
