---
title: "方法 : イメージを並べたパターンによって図形を塗りつぶす | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "ビットマップ [Windows フォーム], 塗りつぶし (図形を)"
  - "イメージ [Windows フォーム], 塗りつぶし (図形を)"
  - "形状, 並べて表示 (イメージを)"
  - "テクスチャ ブラシ, 並べて表示 (イメージを)"
ms.assetid: 6d407891-6e5c-4495-a546-3da5604e9fb8
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : イメージを並べたパターンによって図形を塗りつぶす
床の上にタイルを並べて配置するように、四角形のイメージを隣り合わせに配置して、図形を塗りつぶすことができます。  イメージを並べたパターンで図形の内側を塗りつぶすには、テクスチャ ブラシを使用します。  <xref:System.Drawing.TextureBrush> オブジェクトを構築するときは、<xref:System.Drawing.Image> オブジェクトが引数の 1 つとしてコンストラクターに渡されます。  テクスチャ ブラシを使用して図形の内側を塗りつぶす場合、対象の図形は、このイメージのコピーを繰り返したパターンによって塗りつぶされます。  
  
 <xref:System.Drawing.TextureBrush> オブジェクトのラップ モード プロパティは、四角形のグリッド内でイメージをどのように繰り返すかを決定します。  グリッド内のすべてのイメージを同じ向きで配置することも、イメージをグリッド位置から次のグリッド位置に移動するにつれて反転させていくこともできます。  反転は、水平方向、垂直方向、その両方向で行うことができます。  各種の方法でイメージを反転させて並べたパターンによって図形を塗りつぶす例を次に示します。  
  
### イメージを並べて表示するには  
  
-   次の例では、75 × 75 のイメージを並べたパターンを使用して、200 × 200 の四角形を塗りつぶします。  
  
 ![並べて表示 1](../../../../docs/framework/winforms/advanced/media/tile1.png "tile1")  
  
-   次の図は、イメージを並べたパターンによって、四角形がどのように塗りつぶされるかを示しています。  すべてのイメージの向きは同じで、いずれも反転されていません。  
  
 ![並べて表示 2](../../../../docs/framework/winforms/advanced/media/tile2.png "tile2")  
  
 [!code-csharp[System.Drawing.UsingABrush#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingABrush#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#31)]  
  
### 並べて表示するときにイメージを水平方向に反転させるには  
  
-   次の例では、同じ 75 × 75 のイメージを並べたパターンを使用して、200 × 200 の四角形を塗りつぶします。  ただし、ラップ モードが、イメージを水平方向に反転するように設定されています。  次の図は、イメージを並べたパターンによって、四角形がどのように塗りつぶされるかを示しています。  あるイメージから横方向の次の位置にあるイメージに移るときに、イメージが水平方向に反転されます。  
  
 ![並べて表示 3](../../../../docs/framework/winforms/advanced/media/tile3.png "tile3")  
  
 [!code-csharp[System.Drawing.UsingABrush#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.UsingABrush#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#32)]  
  
### 並べて表示するときにイメージを垂直方向に反転させるには  
  
-   次の例では、同じ 75 × 75 のイメージを並べたパターンを使用して、200 × 200 の四角形を塗りつぶします。  ただし、ラップ モードが、イメージを垂直方向に反転するように設定されています。  
  
     [!code-csharp[System.Drawing.UsingABrush#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#33)]
     [!code-vb[System.Drawing.UsingABrush#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#33)]  
  
### 並べて表示するときにイメージを水平方向と垂直方向に反転させるには  
  
-   次の例では、同じ 75 × 75 のイメージを並べたパターンを使用して、200 × 200 の四角形を塗りつぶします。  ラップ モードは、イメージを水平方向と垂直方向の両方向に反転させるように設定されています。  次の図は、イメージを並べたパターンによって、四角形がどのように塗りつぶされるかを示しています。  あるイメージから横方向の次の位置にあるイメージに移るときに、イメージが水平方向に反転され、あるイメージから縦方向の次の位置にあるイメージに移るときに、イメージが垂直方向に反転されます。  
  
 ![並べて表示 5](../../../../docs/framework/winforms/advanced/media/tile5.png "tile5")  
  
 [!code-csharp[System.Drawing.UsingABrush#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.UsingABrush#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#34)]  
  
## 参照  
 [ブラシを使用した図形の塗りつぶし](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)