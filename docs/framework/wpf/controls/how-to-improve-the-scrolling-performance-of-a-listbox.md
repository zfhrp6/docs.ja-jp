---
title: "方法 : ListBox のスクロール速度を向上させる | Microsoft Docs"
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
  - "ListBox コントロール [WPF], 向上 (スクロールのパフォーマンスを)"
  - "ListBox コントロール [WPF], 再利用 (項目コンテナーを)"
ms.assetid: 1e2bf8f3-c8ce-47f7-a400-a7fe11d1a848
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : ListBox のスクロール速度を向上させる
<xref:System.Windows.Controls.ListBox> に多くの項目が含まれていると、マウス ホイールの操作、またはスクロール バーのつまみのドラッグによる <xref:System.Windows.Controls.ListBox> のスクロール時に、ユーザー インターフェイスの反応が遅くなる可能性があります。  <xref:System.Windows.Controls.VirtualizingStackPanel.VirtualizationMode%2A?displayProperty=fullName> 添付プロパティを <xref:System.Windows.Controls.VirtualizationMode> に設定することで、ユーザーがスクロールを実行したときの <xref:System.Windows.Controls.ListBox> のパフォーマンスを向上させることができます。  
  
## 使用例  
  
## Description  
 次の例では、<xref:System.Windows.Controls.ListBox> を作成し、<xref:System.Windows.Controls.VirtualizingStackPanel.VirtualizationMode%2A?displayProperty=fullName> を <xref:System.Windows.Controls.VirtualizationMode> に設定することで、スクロール時のパフォーマンスを向上させます。  
  
## コード  
 [!code-xml[RecycleItemContainerShippets#VirtualizationMode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml#virtualizationmode)]  
  
 次の例は、前の例で使用するデータを示しています。  
  
 [!code-csharp[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RecycleItemContainerShippets/CSharp/Window1.xaml.cs#listboxdata)]
 [!code-vb[RecycleItemContainerShippets#ListBoxData](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RecycleItemContainerShippets/visualbasic/window1.xaml.vb#listboxdata)]