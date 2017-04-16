---
title: "変換順序が重要となる理由 | Microsoft Docs"
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
  - "変換, 順序の重要性"
ms.assetid: 37d5f9dc-a5cf-4475-aa5d-34d714e808a9
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 変換順序が重要となる理由
1 つの <xref:System.Drawing.Drawing2D.Matrix> オブジェクトに格納できるのは、1 つの変換または連続する複数の変換です。  後者を複合変換と呼びます。  複合変換の行列は、個々の変換の行列を掛け合わせることによって得られます。  
  
## 複合変換の例  
 複合変換では、個々の変換が行われる順序が重要となります。  たとえば、最初に回転し、スケーリングし、平行移動する場合と、最初に平行移動し、回転し、スケーリングする場合とでは結果が異なります。  [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] では、複合変換は左から右に行われます。  S がスケール行列、R が回転行列、T が平行移動行列である場合、その積である SRT \(そのままの順序\) は、最初にスケーリングし、回転し、平行移動する複合変換の行列となります。  積 SRT によって生成される行列は、積 TRS によって生成される行列と異なります。  
  
 実行順序が重要となる理由の 1 つとして、回転やスケーリングなどの変換が座標系の原点を基準にして行われるという点が挙げられます。  原点を中心とするオブジェクトをスケーリングする場合と、原点から離れているオブジェクトをスケーリングする場合とでは、結果が異なります。  同様に、原点を中心とするオブジェクトを回転する場合と、原点から離れているオブジェクトを回転する場合とでも、その結果は異なります。  
  
 スケーリング、回転、および平行移動をこの順序で組み合わせて実行される複合変換を次の例に示します。  <xref:System.Drawing.Graphics.RotateTransform%2A> メソッドに渡される引数 <xref:System.Drawing.Drawing2D.MatrixOrder> は、スケーリングの後に回転が続くことを示します。  同様に、<xref:System.Drawing.Graphics.TranslateTransform%2A> メソッドに渡される引数 <xref:System.Drawing.Drawing2D.MatrixOrder> は、回転の後に平行移動が続くことを示します。  <xref:System.Drawing.Drawing2D.MatrixOrder> および <xref:System.Drawing.Drawing2D.MatrixOrder> は、<xref:System.Drawing.Drawing2D.MatrixOrder> 列挙体のメンバーです。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.MiscLegacyTopics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#21)]  
  
 次の例は、上の例と同じメソッドを呼び出していますが、呼び出しの順序が逆になっています。  操作は最初に平行移動し、回転し、スケーリングするという順序になり、最初にスケーリングし、回転し、平行移動する場合とは、結果が大きく異なります。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.MiscLegacyTopics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#22)]  
  
 複合変換の個々の変換の順序を逆にする方法の 1 つとして、連続する複数のメソッドの呼び出し順序を反転させる方法があります。  操作の順序を制御する 2 番目の方法として、行列の順序引数を変更する方法もあります。  次の例は、<xref:System.Drawing.Drawing2D.MatrixOrder> が <xref:System.Drawing.Drawing2D.MatrixOrder> に変更されている点を除いて上の例と同じです。  行列の掛け合わせは SRT の順序で行われます。この場合、S、R、T は、それぞれスケール、回転、平行移動の行列です。  複合変換の順序は、最初がスケーリング、次が回転、最後が平行移動となります。  
  
 [!code-csharp[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.MiscLegacyTopics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.MiscLegacyTopics/VB/Class1.vb#23)]  
  
 直前の例の結果は、このトピックの最初の例の結果と同じになります。  それは、メソッドの呼び出し順序も、行列の掛け合わせ順序も両方とも反転させたためです。  
  
## 参照  
 <xref:System.Drawing.Drawing2D.Matrix>   
 [座標系と変換](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)   
 [マネージ GDI\+ での変換の使用](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)