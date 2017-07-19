---
title: "方法 : バインディングの更新の通知を設定する | Microsoft Docs"
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
  - "バインド, 更新, 通知"
  - "データ バインディング, 通知 (バインディングの更新の)"
  - "通知, バインディングの更新"
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : バインディングの更新の通知を設定する
この例では、バインディングの[バインディング ターゲット](GTMT) \(ターゲット\) プロパティまたは[バインディング ソース](GTMT) \(ソース\) プロパティが更新されたときに通知を受け取る設定方法を示します。  
  
## 使用例  
 バインディングのソースまたはターゲットが更新されるたびに、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] はデータ更新イベントを発生させます。  内部的には、このイベントは、バインドされたデータが変更されたため、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] を更新する必要があることを通知するために使用されます。  これらのイベントを動作させ、一方向または双方向のバインディングを正しく動作させるためには、<xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスを使用してデータ クラスを実装する必要があることに注意してください。  詳細については、「[プロパティの変更通知を実装する](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)」を参照してください。  
  
 バインディングで、<xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A> プロパティか <xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A> プロパティ \(または両方\) を `true` に設定します。  このイベントをリッスンするために提供するハンドラーは、変更を通知する要素に直接結び付ける必要があります。また、コンテキストのあらゆる変更について通知を受け取る場合は、データ コンテキスト全体に結び付けます。  
  
 ターゲット プロパティが更新された場合の通知を設定する方法を次の例に示します。  
  
 [!code-xml[DirectionalBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 その後、EventHandler\<T\> デリゲート \(この例では *OnTargetUpdated*\) に基づいてハンドラーを割り当て、イベントを処理することができます。  
  
 [!code-csharp[DirectionalBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 イベントのパラメーターは、変更されたプロパティの詳細 \(複数の要素に同じハンドラーが結び付けられている場合は、種類や特定の要素など\) を特定するために使用できます。これは、単一の要素に複数のプロパティがバインドされている場合に役立ちます。  
  
## 参照  
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)