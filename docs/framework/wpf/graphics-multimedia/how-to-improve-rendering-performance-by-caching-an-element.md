---
title: "方法: 要素をキャッシュしてレンダリングのパフォーマンスを向上させる | Microsoft Docs"
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
  - "BitmapCache [WPF], 向上 (レンダリングのパフォーマンスを)"
  - "CacheMode [WPF], 向上 (レンダリングのパフォーマンスを)"
  - "パフォーマンス [WPF], キャッシュ (要素を)"
  - "レンダリングのパフォーマンス [WPF], キャッシュ (要素を)"
  - "UIElement [WPF], キャッシュ"
ms.assetid: 4739c1fc-60ba-4c46-aba6-f6c1a2688f19
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法: 要素をキャッシュしてレンダリングのパフォーマンスを向上させる
複合 <xref:System.Windows.UIElement> のレンダリングのパフォーマンスを向上させるには、<xref:System.Windows.Media.BitmapCache> クラスを使用します。  要素をキャッシュするには、<xref:System.Windows.Media.BitmapCache> クラスの新しいインスタンスを作成し、そのインスタンスを要素の <xref:System.Windows.UIElement.CacheMode%2A> プロパティに割り当てます。  <xref:System.Windows.Media.BitmapCache> は、<xref:System.Windows.Media.BitmapCacheBrush> で効率的に再利用できます。  
  
## 使用例  
 次のコード例では、複合要素を作成し、それをビットマップとしてキャッシュして、要素をアニメーションするときのパフォーマンスを向上させる方法を示します。  要素は、多くの頂点を持つ図形ジオメトリを保持するキャンバスです。  既定値を持つ <xref:System.Windows.Media.BitmapCache> がキャンバスの <xref:System.Windows.UIElement.CacheMode%2A> に割り当てられ、キャッシュされたビットマップのスムーズなスケーリングがアニメーションで表示されます。  
  
 [!code-xml[System.Windows.Media.BitmapCache#_BitmapCacheXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/system.windows.media.bitmapcache/cs/window1.xaml#_bitmapcachexaml)]  
  
## 参照  
 <xref:System.Windows.Media.BitmapCache>   
 <xref:System.Windows.Media.BitmapCacheBrush>   
 <xref:System.Windows.UIElement.CacheMode%2A>   
 [方法: キャッシュされた要素をブラシとして使用する](../../../../docs/framework/wpf/graphics-multimedia/how-to-use-a-cached-element-as-a-brush.md)