---
title: "How to: Enable Tabbing Between Shapes (Visual Studio) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Line control, implementing tabbing"
  - "Shape control, implementing tabbing"
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Enable Tabbing Between Shapes (Visual Studio)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ライン コントロールとシェイプ コントロールには、`TabStop` プロパティおよび `TabIndex` プロパティはありませんが、コントロール間のタブ移動を有効にすることはできます。  次の例では、Ctrl キーと Tab キーの両方を押すと図形間のタブ移動が実行され、Tab キーのみを押すとボタン間のタブ移動が実行されます。  
  
> [!NOTE]
>  次の手順で参照している Visual Studio ユーザー インターフェイス要素の一部は、お使いのコンピューターでは名前や場所が異なる場合があります。  これらの要素は、使用する Visual Studio のエディションとその設定によって決まります。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
### 図形間のタブ移動を有効にするには  
  
1.  **ツールボックス**から、フォームに 3 つの <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> コントロールおよび 2 つの <xref:System.Windows.Forms.Button> コントロールをドラッグします。  
  
2.  **コード エディター**で、モジュールの先頭に `Imports` ステートメントまたは `using` ステートメントを追加します。  
  
    ```vb#  
    Imports Microsoft.VisualBasic.PowerPacks  
    ```  
  
    ```c#  
    using Microsoft.VisualBasic.PowerPacks;  
    ```  
  
3.  イベント プロシージャに次のコードを追加します。  
  
     [!code-cs[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksTabbingCS/VbPowerPacksTabbing.cs#1)]
     [!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksTabbing/VbPowerPacksTabbing.vb#1)]  
  
4.  `Button1_PreviewKeyDown` イベント プロシージャに次のコードを追加します。  
  
     [!code-cs[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/csharp/VbPowerPacksTabbingCS/VbPowerPacksTabbing.cs#2)]
     [!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/visualbasic/VbPowerPacksTabbing/VbPowerPacksTabbing.vb#2)]  
  
## 参照  
 [How to: Draw Shapes with the OvalShape and RectangleShape Controls](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)   
 [How to: Draw Lines with the LineShape Control](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)   
 [Introduction to the Line and Shape Controls](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)