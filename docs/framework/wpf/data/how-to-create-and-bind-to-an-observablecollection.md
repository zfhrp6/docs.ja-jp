---
title: "方法 : ObservableCollection を作成およびバインドする | Microsoft Docs"
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
  - "クラス, ObservableCollection"
  - "データ バインディング, ObservableCollection クラス"
  - "通知"
ms.assetid: 6cf7e275-df76-41c6-a611-53b889b8fd5a
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : ObservableCollection を作成およびバインドする
この例では、項目が追加または削除されたときに通知するコレクション クラスである <xref:System.Collections.ObjectModel.ObservableCollection%601> クラスから派生したコレクションを作成およびバインドする方法を示します。  
  
## 使用例  
 `NameList` コレクションの実装例を次に示します。  
  
 [!code-csharp[MultiBinding#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml.cs#1)]
 [!code-vb[MultiBinding#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MultiBinding/VisualBasic/NameList.vb#1)]  
  
 このコレクションをバインディングに使用できるようにする方法は、「[XAML でデータをバインディング可能にする](../../../../docs/framework/wpf/data/how-to-make-data-available-for-binding-in-xaml.md)」で説明した、他の[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] オブジェクトの場合と同様です。  たとえば、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でコレクションをインスタンス化し、次に示すように、そのコレクションをリソースとして指定します。  
  
 [!code-xml[MultiBinding#OCHowTo](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#ochowto)]  
[!code-xml[MultiBinding#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#resources2)]  
  
 その後、次の方法でコレクションにバインドできます。  
  
 [!code-xml[MultiBinding#MultiBindingListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MultiBinding/CSharp/Window1.xaml#multibindinglistbox)]  
  
 `NameItemTemplate` の定義は、ここには示していません。  
  
> [!NOTE]
>  コレクション内のオブジェクトは、「[バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)」で説明されている要件を満たす必要があります。  特に、<xref:System.Windows.Data.BindingMode> または <xref:System.Windows.Data.BindingMode> \(たとえば、ソース プロパティが動的に変更される場合は [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] を更新する必要がある\) を使用している場合には、<xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスなどの、適切なプロパティ変更通知機構を実装する必要があります。  
  
 詳細については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」の「コレクションへのバインド」を参照してください。  
  
## 参照  
 [ビュー内のデータの並べ替え](../../../../docs/framework/wpf/data/how-to-sort-data-in-a-view.md)   
 [ビュー内のデータをフィルター処理する](../../../../docs/framework/wpf/data/how-to-filter-data-in-a-view.md)   
 [XAML でビューを使用してデータの並べ替えおよびグループ化を行う](../../../../docs/framework/wpf/data/how-to-sort-and-group-data-using-a-view-in-xaml.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)