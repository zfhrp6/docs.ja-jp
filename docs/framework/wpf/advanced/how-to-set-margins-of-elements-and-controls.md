---
title: "方法 : 要素およびコントロールのマージンを設定する | Microsoft Docs"
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
  - "Margin プロパティ, 設定"
  - "プロパティ, Margin プロパティ"
  - "設定, Margin プロパティ"
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : 要素およびコントロールのマージンを設定する
この例では、分離コードでマージンに関する既存のプロパティ値を変更することで、<xref:System.Windows.FrameworkElement.Margin%2A> プロパティを設定する方法を説明します。  <xref:System.Windows.FrameworkElement.Margin%2A> プロパティは <xref:System.Windows.FrameworkElement> 基本要素のプロパティであるため、各種コントロールやその他の要素によって継承されます。  
  
 この例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] で記述され、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] が参照する分離コード ファイルを使用して作成されています。  分離コードは、[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] と [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] の両方のバージョンで示されています。  
  
## 使用例  
 [!code-xml[FEMarginProgrammatic#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]