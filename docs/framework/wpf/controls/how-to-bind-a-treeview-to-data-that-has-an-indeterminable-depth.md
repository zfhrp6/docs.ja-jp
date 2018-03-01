---
title: "方法 : 深度がわからないデータに TreeView をバインドする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TreeView control [WPF], binding to data of indeterminate depth
ms.assetid: daddcd74-1b0f-4ffd-baeb-ec934c5e0f53
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: be21ecb75420b6499e5b95d5f4d93a5f079f9646
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-a-treeview-to-data-that-has-an-indeterminable-depth"></a>方法 : 深度がわからないデータに TreeView をバインドする
バインドする場合がある可能性があります、<xref:System.Windows.Controls.TreeView>の深さがわかっているいないデータ ソースにします。  これは、データが再帰的な場所のフォルダーには、フォルダーを含めることができます、ファイル システムや企業の組織の構造など、本質的に直属の部下として他の従業員の従業員のある場合に発生します。  
  
 データ ソースには、階層化されたオブジェクト モデルが必要です。 たとえば、`Employee`クラスは、従業員の直属の部下である従業員のオブジェクトのコレクションを含めることができます。 データが階層ではない方法で表されている場合は、データの階層的な表現をビルドする必要があります。  
  
 設定すると、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A?displayProperty=nameWithType>プロパティと場合、<xref:System.Windows.Controls.ItemsControl>が生成されます、 <xref:System.Windows.Controls.ItemsControl> 、子項目ごとに後で、子<xref:System.Windows.Controls.ItemsControl>と同じ<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>親として。 設定する場合など、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>データ バインドのプロパティ<xref:System.Windows.Controls.TreeView>、各<xref:System.Windows.Controls.TreeViewItem>生成された使用されている、<xref:System.Windows.DataTemplate>に割り当てられた、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>のプロパティ、<xref:System.Windows.Controls.TreeView>です。  
  
 <xref:System.Windows.HierarchicalDataTemplate>を指定することができます、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>の<xref:System.Windows.Controls.TreeViewItem>、または any<xref:System.Windows.Controls.HeaderedItemsControl>データのテンプレートにします。 設定すると、<xref:System.Windows.HierarchicalDataTemplate.ItemsSource%2A?displayProperty=nameWithType>値であるプロパティ際に使用される、<xref:System.Windows.HierarchicalDataTemplate>を適用します。 使用して、 <xref:System.Windows.HierarchicalDataTemplate>、再帰的に設定することができます、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>各<xref:System.Windows.Controls.TreeViewItem>で、<xref:System.Windows.Controls.TreeView>です。  
  
## <a name="example"></a>例  
 次の例では、バインドする方法、<xref:System.Windows.Controls.TreeView>階層データを使用して、<xref:System.Windows.HierarchicalDataTemplate>を指定する、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>ごと<xref:System.Windows.Controls.TreeViewItem>です。  <xref:System.Windows.Controls.TreeView>を社内の従業員を表す XML データにバインドします。  各`Employee`要素は、その他を含めることができます`Employee`をユーザーに報告を示す要素。 データが再帰的であるため、<xref:System.Windows.HierarchicalDataTemplate>各レベルに適用できます。  
  
 [!code-xaml[TreeViewWithUnknownDepth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewWithUnknownDepth/CS/Window1.xaml#1)]  
  
## <a name="see-also"></a>参照  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)
