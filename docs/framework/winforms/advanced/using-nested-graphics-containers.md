---
title: "入れ子になっているグラフィックス コンテナーの使用 | Microsoft Docs"
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
  - "グラフィックス [Windows フォーム], クリップする"
  - "グラフィックス, 入れ子になっているコンテナー"
  - "グラフィックス, 変換 (入れ子になっているオブジェクトの)"
ms.assetid: a0d9f178-43a4-4323-bb5a-d3e3f77ae6c1
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 入れ子になっているグラフィックス コンテナーの使用
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] には、<xref:System.Drawing.Graphics> オブジェクトの状態の一部を一時的に置換または増加するために使用できるコンテナーが用意されています。  コンテナーを作成するには、<xref:System.Drawing.Graphics> オブジェクトの <xref:System.Drawing.Graphics.BeginContainer%2A> メソッドを呼び出します。  <xref:System.Drawing.Graphics.BeginContainer%2A> を繰り返し呼び出すことで、入れ子になったコンテナーを形成できます。  <xref:System.Drawing.Graphics.EndContainer%2A> に対する各呼び出しは、<xref:System.Drawing.Graphics.BeginContainer%2A> と対になっている必要があります。  
  
## 入れ子になっているコンテナーでの変換  
 <xref:System.Drawing.Graphics> オブジェクトを作成し、その <xref:System.Drawing.Graphics> オブジェクト内にコンテナーを作成する例を次に示します。  <xref:System.Drawing.Graphics> オブジェクトのワールド変換は、x 方向に 100 単位、y 方向に 80 単位の平行移動です。  コンテナーのワールド変換は、30°の回転です。  このコードでは、 `DrawRectangle(pen, -60, -30, 120, 60)`  の呼び出しが 2 回行われます。  <xref:System.Drawing.Graphics.DrawRectangle%2A> の最初の呼び出しはコンテナーの内側で行われます。つまり、この呼び出しは、<xref:System.Drawing.Graphics.BeginContainer%2A> が呼び出されてから <xref:System.Drawing.Graphics.EndContainer%2A> が呼び出されるまでの間に行われます。  <xref:System.Drawing.Graphics.DrawRectangle%2A> の 2 回目の呼び出しは、<xref:System.Drawing.Graphics.EndContainer%2A> を呼び出した後に行われます。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.MiscLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#61)]  
  
 上のコードでは、コンテナーの内側から描画された四角形は、まずコンテナーのワールド変換 \(回転\) によって変換され、次に <xref:System.Drawing.Graphics> オブジェクトのワールド変換 \(平行移動\) によって変換されます。  コンテナーの外側から描画された四角形は、<xref:System.Drawing.Graphics> オブジェクトのワールド変換 \(平行移動\) だけによって変換されます。  これら 2 つの四角形を次の図に示します。  
  
 ![入れ子のコンテナー](../../../../docs/framework/winforms/advanced/media/csnestedcontainers1.png "csnestedcontainers1")  
  
## 入れ子になっているコンテナーでのクリッピング  
 入れ子になっているコンテナーがクリッピング領域を処理するようすを次の例に示します。  このコードは、<xref:System.Drawing.Graphics> オブジェクトを作成し、その <xref:System.Drawing.Graphics> オブジェクト内にコンテナーを作成します。  <xref:System.Drawing.Graphics> オブジェクトのクリッピング領域は四角形で、コンテナーのクリッピング領域は楕円です。  このコードは、<xref:System.Drawing.Graphics.DrawLine%2A> メソッドを 2 回呼び出します。  <xref:System.Drawing.Graphics.DrawLine%2A> の最初の呼び出しはコンテナーの内部で行われ、<xref:System.Drawing.Graphics.DrawLine%2A> の 2 回目の呼び出しはコンテナーの外側で、<xref:System.Drawing.Graphics.EndContainer%2A> の呼び出しの後に行われます。  最初の直線は、2 つのクリッピング領域の交差部分でクリップされます。  2 番目の直線は、<xref:System.Drawing.Graphics> オブジェクトの四角形のクリッピング領域だけによってクリップされます。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#62)]
 [!code-vb[System.Drawing.MiscLegacyTopics#62](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#62)]  
  
 クリップされた 2 つの直線を次の図に示します。  
  
 ![入れ子のコンテナー](../../../../docs/framework/winforms/advanced/media/nestedcontainers2.png "nestedcontainers2")  
  
 上の 2 つの例が示すように、変換およびクリッピング領域は入れ子になっているコンテナー内では累積されます。  コンテナーおよび <xref:System.Drawing.Graphics> オブジェクトのワールド変換を設定すると、コンテナーの内側から描画された項目に対しては両方の変換が適用されます。  この場合、最初にコンテナーの変換が適用され、次に <xref:System.Drawing.Graphics> オブジェクトの変換が適用されます。  コンテナーおよび <xref:System.Drawing.Graphics> オブジェクトのクリッピング領域を設定すると、コンテナーの内側から描画された項目は、2 つのクリッピング領域の交差部分でクリップされます。  
  
## 入れ子になっているコンテナーでの画質設定  
 入れ子になっているコンテナーでの画質の設定 \(<xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.TextRenderingHint%2A> など\) は累積されず、コンテナーの画質設定によって <xref:System.Drawing.Graphics> オブジェクトの画質設定が一時的に置き換えられます。  コンテナーを新規作成するときに、そのコンテナーの画質設定は既定値に設定されます。  たとえば、スムージング モードが <xref:System.Drawing.Drawing2D.SmoothingMode> の <xref:System.Drawing.Graphics> オブジェクトがあるとします。  コンテナーを作成する場合、そのコンテナー内のスムージング モードは既定のスムージング モードになります。  コンテナーのスムージング モードは自由に設定でき、そのコンテナーの内側から描画される全項目は、設定されているモードに基づいて描画されます。  <xref:System.Drawing.Graphics.EndContainer%2A> を呼び出した後で描画される項目は、<xref:System.Drawing.Graphics.BeginContainer%2A> を呼び出す前に有効だったスムージング モード \(<xref:System.Drawing.Drawing2D.SmoothingMode>\) に基づいて描画されます。  
  
## 入れ子になっている複数層のコンテナー  
 1 つの <xref:System.Drawing.Graphics> オブジェクト内に作成できるコンテナー数は 1 つに限定されているわけではありません。  各コンテナーが前のコンテナーの入れ子になっている一連のコンテナーを作成でき、入れ子になっているコンテナーごとにワールド変換、クリッピング領域、および画質設定を指定できます。  最も内側のコンテナーから描画メソッドを呼び出す場合は、最も内側のコンテナーから始まり最も外側のコンテナーで終了するという順序で、変換が適用されます。  最も内側のコンテナーの内側から描画された項目は、すべてのクリッピング領域の交差部分でクリップされます。  
  
 <xref:System.Drawing.Graphics> オブジェクトを作成し、そのテキストの画質を指定する属性として <xref:System.Drawing.Drawing2D.SmoothingMode> を設定する例を次に示します。  このコードは、1 つのコンテナーがもう 1 つのコンテナー内に入れ子になっている 2 つのコンテナーを作成します。  外側のコンテナーのテキストの画質を指定する属性は <xref:System.Drawing.Text.TextRenderingHint> に、内側のコンテナーのテキストの画質を指定する属性は <xref:System.Drawing.Drawing2D.SmoothingMode> に設定されます。  このコードは、3 つの文字列を描画します。1 つは内側のコンテナーからの文字列、1 つは外側のコンテナーからの文字列、もう 1 つは <xref:System.Drawing.Graphics> オブジェクト自体からの文字列です。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#63)]
 [!code-vb[System.Drawing.MiscLegacyTopics#63](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#63)]  
  
 これらの 3 つの文字列を次の図に示します。  内側のコンテナーおよび <xref:System.Drawing.Graphics> オブジェクトから描画された文字列は、アンチエイリアシングによって滑らかになっています。  外側のコンテナーから描画された文字列はアンチエイリアシングによって滑らかになってはいません。これは、<xref:System.Drawing.Graphics.TextRenderingHint%2A> プロパティが <xref:System.Drawing.Text.TextRenderingHint> に設定されているためです。  
  
 ![入れ子のコンテナー](../../../../docs/framework/winforms/advanced/media/nestedcontainers3.png "nestedcontainers3")  
  
## 参照  
 <xref:System.Drawing.Graphics>   
 [Graphics オブジェクトの状態の管理](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)