---
title: "方法 : BetweenShowDelay プロパティを使用する | Microsoft Docs"
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
  - "BetweenShowDelay 時間プロパティ"
  - "ToolTip コントロール, BetweenShowDelay 時間プロパティ"
ms.assetid: 984ea76d-f2a2-4326-a02e-f97ec3d036d6
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : BetweenShowDelay プロパティを使用する
この例では、<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> 時間プロパティを使用して、ユーザーがあるツールヒントから別のツールヒントにマウス ポインターを直接移動したときに、ほとんど遅延なく、すばやくツールヒントを表示する方法を示します。  
  
## 使用例  
 次の例では、両方の <xref:System.Windows.Shapes.Ellipse> コントロールのツールヒントについて、<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> プロパティを 1 秒 \(1000 ミリ秒\) に設定し、<xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> を 2 秒 \(2000 ミリ秒\) に設定しています。  一方の楕円のツールヒントを表示した後、2 秒以内に別の楕円にマウス ポインターを移動してそこにとどまると、2 番目の楕円のツールヒントがすぐに表示されます。  
  
 次のシナリオではいずれも、<xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> が適用され、2 番目の楕円のツールヒントは 1 秒後に表示されます。  
  
-   2 番目の楕円に移動するのに 2 秒より長くかかる場合。  
  
-   1 番目の楕円の時間間隔の開始時に、ツールヒントが表示されない場合。  
  
 [!code-xml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
[!code-xml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
## 参照  
 <xref:System.Windows.Controls.ToolTip>   
 <xref:System.Windows.Controls.ToolTipService>   
 [方法のトピック](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)   
 [ToolTip の概要](../../../../docs/framework/wpf/controls/tooltip-overview.md)