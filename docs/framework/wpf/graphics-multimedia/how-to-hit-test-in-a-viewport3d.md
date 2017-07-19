---
title: "方法 : Viewport3D でヒット テストを実行する | Microsoft Docs"
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
  - "3-D ビジュアル, ヒット テスト"
  - "ヒット テスト, 3-D ビジュアルの"
  - "Viewport3D"
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Viewport3D でヒット テストを実行する
この例では、<xref:System.Windows.Controls.Viewport3D> で 3D ビジュアルのヒット テストを行う方法を示します。  
  
 <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> は 2D と 3D の情報を返すので、テスト結果を反復処理することで 3D の結果だけを読み取ることができます。  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 次のコードの <xref:System.Windows.Media.HitTestResultBehavior> は、ヒット テストの結果の処理方法を決定します。  `UpdateResultInfo` と `UpdateMaterial` は、ローカルに定義されたメソッドです。  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
  
## 参照  
 [3\-D ヒット テストのサンプル](http://go.microsoft.com/fwlink/?LinkID=159959)