---
title: "方法 : プロパティの変更通知を実装する | Microsoft Docs"
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
  - "変更通知"
  - "データ バインディング, プロパティの変更通知"
  - "通知 (変更の)"
  - "プロパティ, 変更通知"
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : プロパティの変更通知を実装する
[バインディング ターゲット](GTMT)のプロパティに[バインディング ソース](GTMT)の動的変更が自動的に反映される \(たとえば、ユーザーがフォームを編集するとプレビュー ペインが自動的に更新される\) ようにするために、<xref:System.Windows.Data.BindingMode> または <xref:System.Windows.Data.BindingMode> バインディングをサポートするには、クラスが適切なプロパティ変更通知を提供する必要があります。  この例では、<xref:System.ComponentModel.INotifyPropertyChanged> を実装するクラスを作成する方法を示します。  
  
## 使用例  
 <xref:System.ComponentModel.INotifyPropertyChanged> を実装するには、<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> イベントを宣言し、`OnPropertyChanged` メソッドを作成する必要があります。  次に、変更を通知する必要のある各プロパティについて、そのプロパティが更新されるたびに `OnPropertyChanged` を呼び出します。  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 `Person` クラスを使用して <xref:System.Windows.Data.BindingMode> バインディングをサポートする例については、「[TextBox テキストでソースを更新するタイミングを制御する](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)」を参照してください。  
  
## 参照  
 [バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)