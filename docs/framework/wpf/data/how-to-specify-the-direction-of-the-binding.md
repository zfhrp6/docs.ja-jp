---
title: "方法 : バインディングの方向を指定する | Microsoft Docs"
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
  - "バインディングの方向"
  - "データ バインディング, 方向 (バインディングの)"
  - "方向 (バインディングの)"
ms.assetid: 37334478-028b-4514-86c9-1420709f4818
caps.latest.revision: 21
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# 方法 : バインディングの方向を指定する
この例では、バインディングで[バインディング ターゲット](GTMT) \(ターゲット\) プロパティのみを更新するか、[バインディング ソース](GTMT) \(ソース\) プロパティのみを更新するか、またはターゲット プロパティとソース プロパティの両方を更新するかを指定する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Data.Binding.Mode%2A> プロパティを使用して、バインディングの方向を指定します。  バインディングの更新で使用可能なオプションを次の列挙値の一覧に示します。  
  
-   <xref:System.Windows.Data.BindingMode> は、ソース プロパティまたはターゲット プロパティのいずれかが変更されると、ターゲット プロパティまたはソース プロパティを更新します。  
  
-   <xref:System.Windows.Data.BindingMode> は、ソース プロパティが変更されたときに、ターゲット プロパティのみを更新します。  
  
-   <xref:System.Windows.Data.BindingMode> は、アプリケーションの起動時または <xref:System.Windows.FrameworkElement.DataContext%2A> の変更時に、ターゲット プロパティのみを更新します。  
  
-   <xref:System.Windows.Data.BindingMode> は、ターゲット プロパティが変更されると、ソース プロパティを更新します。  
  
-   <xref:System.Windows.Data.BindingMode> を指定すると、ターゲット プロパティの <xref:System.Windows.Data.Binding.Mode%2A> の既定値が使用されます。  
  
 詳細については、<xref:System.Windows.Data.BindingMode> 列挙体の解説を参照してください。  
  
 <xref:System.Windows.Data.Binding.Mode%2A> プロパティを設定する方法を次の例に示します。  
  
 [!code-xml[DirectionalBinding#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#4)]  
  
 ソースの変更を検出するには \(<xref:System.Windows.Data.BindingMode> および <xref:System.Windows.Data.BindingMode> バインディングの場合\)、ソースで <xref:System.ComponentModel.INotifyPropertyChanged> などの適切なプロパティの変更通知機構を実装する必要があります。  <xref:System.ComponentModel.INotifyPropertyChanged> の実装の例については、「[プロパティの変更通知を実装する](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)」を参照してください。  
  
 <xref:System.Windows.Data.BindingMode> または <xref:System.Windows.Data.BindingMode> のバインディングでは、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> プロパティを設定することにより、ソースの更新のタイミングを制御できます。  詳細については、<xref:System.Windows.Data.Binding.UpdateSourceTrigger%2A> を参照してください。  
  
## 参照  
 <xref:System.Windows.Data.Binding>   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)