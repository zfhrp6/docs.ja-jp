---
title: "方法 : カスタム ルーティング イベントを作成する | Microsoft Docs"
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
  - "作成, ルーティング イベント"
  - "イベント, ルーティング"
  - "ルーティング イベント, 作成"
ms.assetid: b79f459a-1c3f-4045-b2d4-1659cc8eaa3c
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : カスタム ルーティング イベントを作成する
カスタム イベントが[イベント ルーティング](GTMT)をサポートするには、<xref:System.Windows.EventManager.RegisterRoutedEvent%2A> メソッドを使用して <xref:System.Windows.RoutedEvent> を登録する必要があります。  この例では、カスタム ルーティング イベントを作成するときの基本を示します。  
  
## 使用例  
 次の例に示すように、まず、<xref:System.Windows.EventManager.RegisterRoutedEvent%2A> メソッドを使用して <xref:System.Windows.RoutedEvent> を登録します。  通常、<xref:System.Windows.RoutedEvent> の静的フィールド名は、サフィックスの ***Event*** で終わる必要があります。  この例では、イベントの名前は `Tap` で、イベントのルーティング方法は <xref:System.Windows.RoutingStrategy> です。  登録呼び出しの後、追加および削除の[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] イベント アクセサーをイベントに提供できます。  
  
 ここに示す例では、イベントは `OnTap` 仮想メソッドによって発生しますが、イベントを発生させる方法やイベントを変更に応答させる方法は必要に応じて決まることに注意してください。  
  
 この例では、基本的に <xref:System.Windows.Controls.Button> のサブクラス全体を実装していることに注意してください。また、このサブクラスは、個別のアセンブリとして作成され、個別の [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ページでカスタム クラスとしてインスタンス化されています。  これは概念として、サブクラス化されたコントロールは、他のコントロールで構成されるツリーに挿入でき、このような場合、このコントロールのカスタム イベントは、ネイティブな [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 要素とまったく同じイベント ルーティング機能を備えるということを示しています。  
  
 [!code-csharp[RoutedEventCustom#CustomClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/SDKSampleLibrary/class1.cs#customclass)]
 [!code-vb[RoutedEventCustom#CustomClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventCustom/VB/SDKSampleLibrary/Class1.vb#customclass)]  
  
 [!code-xml[RoutedEventCustom#Page](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventCustom/CSharp/RoutedEventCustomApp/default.xaml#page)]  
  
 トンネル イベントも同じように作成されますが、登録呼び出しで <xref:System.Windows.RoutedEvent.RoutingStrategy%2A> は <xref:System.Windows.RoutingStrategy> に設定される点が異なります。  通常、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、トンネル イベントに "Preview" がプレフィックスとして付加されます。  
  
 バブル イベントの動作についての例を確認するには、「[ルーティング イベントを処理する](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)」を参照してください。  
  
## 参照  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)   
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)