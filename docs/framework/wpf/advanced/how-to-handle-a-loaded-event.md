---
title: "方法 : 読み込まれたイベントを処理する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "イベント, 読み込み"
  - "Loaded イベント"
  - "XAML, Loaded イベント"
ms.assetid: 0cf8d003-8441-4df4-807a-6db09347e829
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : 読み込まれたイベントを処理する
この例では、<xref:System.Windows.FrameworkElement.Loaded?displayProperty=fullName> イベントを処理する方法と、このイベントの処理に適したシナリオを示します。  ページが読み込まれると、ハンドラーは <xref:System.Windows.Controls.Button> を作成します。  
  
## 使用例  
 次の例では、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を分離コード ファイルと共に使用します。  
  
 [!code-xml[FELoaded#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FELoaded#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FELoaded/CSharp/default.xaml.cs#handler)]
 [!code-vb[FELoaded#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FELoaded/VisualBasic/default.xaml.vb#handler)]  
  
## 参照  
 <xref:System.Windows.FrameworkElement>   
 [オブジェクトの有効期間イベント](../../../../docs/framework/wpf/advanced/object-lifetime-events.md)   
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)