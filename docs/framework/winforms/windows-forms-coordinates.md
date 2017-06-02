---
title: "Windows フォームの座標 | Microsoft Docs"
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
  - "クライアント座標"
  - "座標, Windows フォーム"
  - "画面座標"
  - "Windows フォームの座標"
ms.assetid: cc06e61f-43b6-4408-a676-2542dcfcd96e
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# Windows フォームの座標
Windows フォームの座標系はデバイス座標に基づいています。Windows フォームを描画するときの基本測定単位はデバイス単位 \(通常、ピクセル\) です。  画面上の点は x 座標と y 座標の組み合わせで表され、x 座標は右に行くほど大きくなり、y 座標は下に行くほど大きくなります。  画面上の原点の位置は、画面座標かクライアント座標のいずれを指定しているかによって異なります。  
  
## 画面座標  
 Windows フォーム アプリケーションでは、画面上のウィンドウの位置を画面座標で指定します。  画面座標の場合、原点は画面の左上隅になります。  ウィンドウの完全な位置は、多くの場合、ウィンドウの左上隅と右下隅を定義する 2 点の画面座標を含む <xref:System.Drawing.Rectangle> 構造体によって表されます。  
  
## クライアント座標  
 Windows フォーム アプリケーションでは、フォームやコントロール内の点の位置をクライアント座標で指定します。  クライアント座標の原点は、コントロールやフォームのクライアント領域の左上隅になります。  クライアント座標により、アプリケーションでフォームやコントロールを描画するときに、画面上の位置とは無関係に一貫した座標値を使用できます。  
  
 クライアント領域の寸法も、その領域のクライアント座標を含む <xref:System.Drawing.Rectangle> 構造体によって表されます。  常に四角形の左上の座標がクライアント領域に含まれ、右下の座標は除外されます。  グラフィックス操作には、クライアント領域の右辺と下辺が含まれません。  たとえば、<xref:System.Drawing.Graphics.FillRectangle%2A> メソッドは、指定した四角形の右辺と下辺まで塗りつぶしますが、これらの辺を含みません。  
  
## 座標の種類の変換  
 画面座標からクライアント座標への変換が必要になることがあります。  この変換は、<xref:System.Windows.Forms.Control> クラスの <xref:System.Windows.Forms.Control.PointToClient%2A> メソッドや <xref:System.Windows.Forms.Control.PointToScreen%2A> メソッドを使用して簡単に行うことができます。  たとえば、<xref:System.Windows.Forms.Control> の <xref:System.Windows.Forms.Control.MousePosition%2A> プロパティは画面座標で報告されますが、クライアント座標に変換することもできます。  
  
## 参照  
 <xref:System.Windows.Forms.Control.PointToClient%2A>   
 <xref:System.Windows.Forms.Control.PointToScreen%2A>