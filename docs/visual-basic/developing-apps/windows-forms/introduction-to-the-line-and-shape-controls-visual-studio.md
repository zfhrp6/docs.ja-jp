---
title: "Introduction to the Line and Shape Controls (Visual Studio) | Microsoft Docs"
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
  - "Line control, overview"
  - "Shape control, overview"
  - "lines, drawing"
  - "shapes, drawing"
ms.assetid: 5c4e8b1a-0733-4020-af6c-f582f4026728
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Introduction to the Line and Shape Controls (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Visual Basic Power Packs のライン コントロールとシェイプ コントロールは、3 つのグラフィカル コントロールの集まりであり、これらを使用してフォームおよびコンテナーに線と図形を描画できます。  <xref:Microsoft.VisualBasic.PowerPacks.LineShape> コントロールは、横線、縦線、および斜線の描画に使用します。  <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> コントロールは円と楕円の描画に使用し、<xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> コントロールは長方形と正方形の描画に使用します。  
  
## ライン コントロールとシェイプ コントロール  
 ライン コントロールとシェイプ コントロールは、<xref:System.Drawing> 名前空間に含まれるグラフィックス メソッドの多くをカプセル化しています。  そのため、グラフィックス オブジェクト、ペン、およびブラシを作成することなく、1 回の手順で線と図形を描画できます。  グラデーション塗りつぶしなどの複雑なグラフィックス手法も、いくつかのプロパティを設定するだけで実現できます。  
  
 グラフィックス メソッドを使用して線と図形を描画することもできますが、ライン コントロールとシェイプ コントロールを使用すると、次のような利点があります。  
  
-   グラフィックス メソッドを呼び出すことができるのは実行時のみです。  ライン コントロールとシェイプ コントロールは、デザイン時にフォームに追加できます。  これによって外観を確認でき、正確に配置できます。また、これらのコントロールは実行時に追加することもできます。  
  
-   ライン コントロールとシェイプ コントロールは、実行時に選択でき、<xref:Microsoft.VisualBasic.PowerPacks.Shape.Click> や <xref:Microsoft.VisualBasic.PowerPacks.Shape.OnDoubleClick%2A> などのイベントを提供します。  グラフィックス メソッドの出力は選択できず、イベントを提供しません。  
  
-   ライン コントロールとシェイプ コントロールには、<xref:Microsoft.VisualBasic.PowerPacks.Shape.BringToFront%2A> メソッドおよび <xref:Microsoft.VisualBasic.PowerPacks.Shape.SendToBack%2A> メソッドがあり、これらのメソッドによってデザイン時にも実行時にも z オーダーを制御できます。  グラフィックス メソッドの z オーダーは、実行時の実行順序を変更することによってのみ制御できます。  
  
-   ライン コントロールとシェイプ コントロールはウィンドウなしのコントロールであり、ウィンドウ ハンドルがないのでシステム リソースの消費が少なく済みます。  
  
### オブジェクト モデル  
 ライン コントロールとシェイプ コントロールは、共有プロパティ、共有メソッド、共有イベントを定義する基本 <xref:Microsoft.VisualBasic.PowerPacks.Shape> クラスから派生しています。  
  
 ラインとシェイプのオブジェクト階層を次の図に示します。  
  
 ![Line および Shape オブジェクト階層のダイアグラム](../../../visual-basic/developing-apps/windows-forms/media/lineshapeobject.png "LineShapeObject")  
ラインとシェイプのオブジェクト階層  
  
 派生する <xref:Microsoft.VisualBasic.PowerPacks.LineShape> クラスには、線に固有のプロパティ、メソッド、およびイベントがあります。  派生する <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> クラスは <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> と <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> の基本クラスであり、このクラスには、すべての図形に共通のプロパティ、メソッド、およびイベントがあります。  独自の `Shape` コントロールを <xref:Microsoft.VisualBasic.PowerPacks.SimpleShape> から派生させて作成することもできます。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.OvalShape> クラスおよび <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> クラスは、円、楕円、四角形、および角の丸い四角形の描画に使用できます。  
  
 フォームまたはコンテナーにライン コントロールまたはシェイプ コントロールを追加すると、非表示の <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> オブジェクトが作成されます。  <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> は、各コンテナー コントロール内で図形のキャンバスとして機能します。各 <xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> には対応する <xref:Microsoft.VisualBasic.PowerPacks.ShapeCollection> があり、これによって、ライン コントロールとシェイプ コントロールを反復処理できます。  カット アンド ペーストまたはドラッグ アンド ドロップを使用して、コンテナー間で図形を移動できます。  コンテナーから最後の図形を削除すると、<xref:Microsoft.VisualBasic.PowerPacks.ShapeContainer> も削除されます。  
  
> [!NOTE]
>  すべてのコンテナー コントロールがライン コントロールとシェイプ コントロールをサポートしているわけではありません。  <xref:System.Windows.Forms.TableLayoutPanel> または <xref:System.Windows.Forms.FlowLayoutPanel> では、ライン コントロールまたはシェイプ コントロールをホストできません。  
  
## 参照  
 <xref:Microsoft.VisualBasic.PowerPacks>   
 [How to: Draw Lines with the LineShape Control](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)   
 [How to: Draw Shapes with the OvalShape and RectangleShape Controls](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)   
 [How to: Enable Tabbing Between Shapes](../Topic/How%20to:%20Enable%20Tabbing%20Between%20Shapes%20\(Visual%20Studio\).md)