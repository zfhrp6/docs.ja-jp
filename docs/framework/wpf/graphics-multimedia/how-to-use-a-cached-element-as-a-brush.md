---
title: "方法: キャッシュされた要素をブラシとして使用する | Microsoft Docs"
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
  - "BitmapCache [WPF], 使用"
  - "BitmapCacheBrush [WPF], 使用"
  - "キャッシュした要素 [WPF], ブラシとして使用"
  - "CacheMode [WPF], 使用"
ms.assetid: d36e944a-866e-4baf-98c4-fd6a75f6fdd0
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法: キャッシュされた要素をブラシとして使用する
キャッシュされた要素を効率的に再利用するには、<xref:System.Windows.Media.BitmapCacheBrush> クラスを使用します。  要素をキャッシュするには、<xref:System.Windows.Media.BitmapCache> クラスの新しいインスタンスを作成し、そのインスタンスを要素の <xref:System.Windows.UIElement.CacheMode%2A> プロパティに割り当てます。  
  
## 使用例  
 キャッシュされた要素を再利用する方法を次のコード例に示します。  キャッシュされた要素は、大きいイメージを表示する <xref:System.Windows.Controls.Image> コントロールです。  <xref:System.Windows.Controls.Image> コントロールは、<xref:System.Windows.Media.BitmapCache> クラスを使用してビットマップとしてキャッシュされます。これを <xref:System.Windows.Media.BitmapCacheBrush> に割り当てることで、キャッシュが再利用されます。  効率的な再利用を示すために、ブラシは 25 個のボタンの背景に割り当てられます。  
  
 [!code-xml[System.Windows.Media.BitmapCacheBrush#_BitmapCacheBrushXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcachebrush/cs/window1.xaml#_bitmapcachebrushxaml)]  
  
## 参照  
 <xref:System.Windows.Media.BitmapCache>   
 <xref:System.Windows.Media.BitmapCacheBrush>   
 <xref:System.Windows.UIElement.CacheMode%2A>   
 [方法: 要素をキャッシュしてレンダリングのパフォーマンスを向上させる](../../../../docs/framework/wpf/graphics-multimedia/how-to-improve-rendering-performance-by-caching-an-element.md)