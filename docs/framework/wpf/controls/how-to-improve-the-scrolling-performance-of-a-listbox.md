---
title: '方法 : ListBox のスクロール速度を向上させる'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListBox control [WPF], reusing item containers
- ListBox control [WPF], improving scrolling performance
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
ms.openlocfilehash: 224b996ad97d9a71ce43023143b68c2ab5b8467b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552793"
---
# <a name="how-to-improve-the-scrolling-performance-of-a-listbox"></a>方法 : ListBox のスクロール速度を向上させる
場合、 <xref:System.Windows.Controls.ListBox> 、多くのアイテムが含まれています、ユーザーがスクロールすると、ユーザー インターフェイスの応答が遅くなる、<xref:System.Windows.Controls.ListBox>をマウスのホイールを使用するか、スクロール バーのつまみをドラッグします。 パフォーマンスを向上させることができます、<xref:System.Windows.Controls.ListBox>を設定してユーザーをスクロールするときに、`VirtualizingStackPanel.VirtualizationMode`添付プロパティ<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>です。  
  
## <a name="example"></a>例  
  
## <a name="description"></a>説明  
次の例を作成、<xref:System.Windows.Controls.ListBox>設定と、`VirtualizingStackPanel.VirtualizationMode`添付プロパティ<xref:System.Windows.Controls.VirtualizationMode.Recycling?displayProperty=nameWithType>スクロール中にパフォーマンスを向上させます。  
  
## <a name="code"></a>コード  
 [!code-xaml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 次の例では、前の例で使用するデータを示します。  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]
