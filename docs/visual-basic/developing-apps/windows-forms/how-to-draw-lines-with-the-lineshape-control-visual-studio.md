---
title: "How to: Draw Lines with the LineShape Control (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "LineShape control"
  - "lines, drawing"
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Draw Lines with the LineShape Control (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.PowerPacks.LineShape> コントロールを使用すると、デザイン時および実行時に、フォームまたはコンテナー上に横線、縦線、または斜線を描画できます。  
  
 **メモ** 次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### デザイン時に線を描画するには  
  
1.  **ツールボックス**の **\[Visual Basic PowerPacks\]** タブから <xref:Microsoft.VisualBasic.PowerPacks.LineShape> コントロールをフォームまたはコンテナー コントロールにドラッグします。  
  
2.  サイズ変更ハンドルをドラッグして線のサイズを設定し、移動ハンドルをドラッグして線の位置を指定します。  
  
     **\[プロパティ\]** ウィンドウで `X1`、`X2`、`Y1`、および `Y2` の各プロパティを変更することによって、線のサイズと位置を変更することもできます。  
  
3.  **\[プロパティ\]** ウィンドウで、オプションとして、`BorderStyle` や `BorderColor` などのその他のプロパティを設定して線の外観を変更します。  
  
### 実行時に線を描画するには  
  
1.  **\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックします。  
  
2.  **\[参照の追加\]** ダイアログ ボックスで、**\[Microsoft.VisualBasic.PowerPacks.VS\]** をオンにし、**\[OK\]** をクリックします。  
  
3.  **コード エディター**で、モジュールの先頭に `Imports` ステートメントまたは `using` ステートメントを追加します。  
  
    ```vb#  
    Imports Microsoft.VisualBasic.PowerPacks  
    ```  
  
    ```c#  
    using Microsoft.VisualBasic.PowerPacks;  
    ```  
  
4.  `Event` プロシージャに次のコードを追加します。  
  
     [!code-cs[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>   
 [Introduction to the Line and Shape Controls](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)   
 [How to: Draw Shapes with the OvalShape and RectangleShape Controls](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)