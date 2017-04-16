---
title: "方法 : イベントを使用してロールオーバー効果を作成する | Microsoft Docs"
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
  - "色 (要素の), 変更"
  - "要素の色, 変更"
  - "ロールオーバー効果"
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : イベントを使用してロールオーバー効果を作成する
この例では、ある要素が占める領域にマウス ポインターが出入りするのに合わせて、要素の色を変更する方法を示します。  
  
 この例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルと分離コード ファイルで構成されています。  
  
> [!NOTE]
>  この例ではイベントを使用する方法を示しますが、これと同じ効果を実現するには、スタイルで <xref:System.Windows.Trigger> を使用する方法が推奨されます。  詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
## 使用例  
 次の [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] は、<xref:System.Windows.Controls.Border> で囲まれた <xref:System.Windows.Controls.TextBlock> で構成されるユーザー インターフェイスを作成し、<xref:System.Windows.Input.Mouse.MouseEnter> および <xref:System.Windows.UIElement.MouseLeave> イベント ハンドラーを <xref:System.Windows.Controls.Border> に結合します。  
  
 [!code-xml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 次の分離コードでは、<xref:System.Windows.UIElement.MouseEnter> および <xref:System.Windows.UIElement.MouseLeave> イベント ハンドラーを作成します。  マウス ポインターが <xref:System.Windows.Controls.Border> に入ると、<xref:System.Windows.Controls.Border> の背景が赤に変わります。  マウス ポインターが <xref:System.Windows.Controls.Border> から出ると、<xref:System.Windows.Controls.Border> の背景は白に戻ります。  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]