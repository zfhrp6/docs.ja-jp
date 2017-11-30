---
title: "方法 : 要素およびコントロールのマージンを設定する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting [WPF], Margin property
- properties [WPF], Margin property
- Margin property [WPF], setting
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 965e2061d6457084e4f316d27e29865109f62e34
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-set-margins-of-elements-and-controls"></a>方法 : 要素およびコントロールのマージンを設定する
この例を設定する方法について説明、<xref:System.Windows.FrameworkElement.Margin%2A>分離コードで余白の幅を既存のプロパティ値を変更することで、プロパティです。 <xref:System.Windows.FrameworkElement.Margin%2A>プロパティは、プロパティの<xref:System.Windows.FrameworkElement>基本要素、およびさまざまなコントロールとその他の要素によって継承されるためです。  
  
 この例で記述された[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、分離コード ファイルを[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を指します。 両方の分離コードが示すように、[!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)]と[!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)]バージョン。  
  
## <a name="example"></a>例  
 [!code-xaml[FEMarginProgrammatic#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
