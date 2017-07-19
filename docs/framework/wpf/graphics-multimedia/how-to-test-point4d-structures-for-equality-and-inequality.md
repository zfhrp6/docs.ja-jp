---
title: "方法 : Point4D 構造体が等価かどうかをテストする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "等価比較, テスト (Point4D 構造体を)"
  - "非等価比較, テスト (Point4D 構造体を)"
  - "Point4D 構造体, テスト (等しいかどうかを)"
  - "Point4D 構造体, テスト (等しくないかどうかを)"
  - "テスト, Point4D 構造体が等しいかどうか"
  - "テスト, Point4D 構造体が等しくないかどうか"
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : Point4D 構造体が等価かどうかをテストする
この例では、<xref:System.Windows.Media.Media3D.Point4D> 構造体の等価および非等価をテストする方法を示します。  
  
 <xref:System.Windows.Media.Media3D.Point4D> 等価性メソッドを使用して <xref:System.Windows.Media.Media3D.Point4D> 構造体の等価および非等価をテストする方法を次のコード例に示します。  <xref:System.Windows.Media.Media3D.Point4D> 構造体は、オーバーロードされた等価 \(`==`\) 演算子を使用して等価かどうかがテストされ、次にオーバーロードされた非等価 \(`!=`\) 演算子を使用して非等価かどうかがテストされます。最後に、静的 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> メソッドを使用して <xref:System.Windows.Media.Media3D.Point3D> 構造体と <xref:System.Windows.Media.Media3D.Point4D> 構造体が等価かどうかがチェックされます。  
  
## 使用例  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## 参照  
 <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>   
 <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>   
 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>