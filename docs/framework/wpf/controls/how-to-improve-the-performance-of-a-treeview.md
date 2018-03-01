---
title: "方法 : TreeView のパフォーマンスを改善する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TreeView control [WPF], improving the performance
ms.assetid: b792c740-cf2b-4da8-8ba8-3d2e5a821874
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2c13a9c89bdcb149df61f26177ea8705e502402f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-improve-the-performance-of-a-treeview"></a>方法 : TreeView のパフォーマンスを改善する
場合、<xref:System.Windows.Controls.TreeView>多くの項目を含むの読み込みにかかる時間は、ユーザー インターフェイスに大きな遅延を引き起こす可能性があります。 設定して、読み込み時間を向上させることができます、`VirtualizingStackPanel.IsVirtualizing`添付プロパティ`true`です。  UI ユーザーがスクロール時に応答しに時間がかかる場合があります、<xref:System.Windows.Controls.TreeView>をマウスのホイールを使用するか、スクロール バーのつまみをドラッグします。 パフォーマンスを向上させることができます、<xref:System.Windows.Controls.TreeView>を設定してユーザーをスクロールするときに、`VirtualizingStackPanel.VirtualizationMode`添付プロパティ<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>です。  
  
## <a name="example"></a>例  
  
## <a name="description"></a>説明  
次の例を作成、<xref:System.Windows.Controls.TreeView>が設定された、`VirtualizingStackPanel.IsVirtualizing`添付プロパティを true と`VirtualizingStackPanel.VirtualizationMode`添付プロパティ<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>パフォーマンスを最適化します。  
  
## <a name="code"></a>コード  
 [!code-xaml[RecycleItemContainerShippets#VirtualizingTreeView](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizingtreeview)]  
  
 次の例では、前の例で使用するデータを示します。  
  
 [!code-csharp[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#treeviewdata)]
 [!code-vb[RecycleItemContainerShippets#TreeViewData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#treeviewdata)]  
  
## <a name="see-also"></a>参照  
 [コントロール](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
