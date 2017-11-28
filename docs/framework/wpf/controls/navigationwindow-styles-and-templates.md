---
title: "NavigationWindow のスタイルとテンプレート"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- states [WPF], NavigationWindow
- NavigationWindow [WPF], styles and templates
- ControlTemplate [WPF], NavigationWindow
- parts [WPF], NavigationWindow
- styles [WPF], NavigationWindow
- templates [WPF], NavigationWindow
ms.assetid: 3656055e-3222-43c8-b868-fd0c90cc31a3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b48b0b4451f0cf93b86ee448db255f337a859b74
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="navigationwindow-styles-and-templates"></a>NavigationWindow のスタイルとテンプレート
このトピックは、のスタイルとテンプレートについて説明します、<xref:System.Windows.Navigation.NavigationWindow>コントロール。 既定値を変更することができます<xref:System.Windows.Controls.ControlTemplate>コントロールの外観を一意にします。 詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
## <a name="navigationwindow-parts"></a>NavigationWindow 部分  
 次の表に、名前付きのパーツの<xref:System.Windows.Navigation.NavigationWindow>コントロール。  
  
|パーツ|型|説明|  
|-|-|-|  
|PART_NavWinCP|<xref:System.Windows.Controls.ContentPresenter>|コンテンツの領域。|  
  
## <a name="navigationwindow-states"></a>NavigationWindow 状態  
 次の表に、用ビジュアル状態、<xref:System.Windows.Navigation.NavigationWindow>コントロール。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|-|-|-|  
|有効|ValidationStates|コントロールを使用して、<xref:System.Windows.Controls.Validation>クラスおよび<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`false`します。|  
|InvalidFocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスします。|  
|InvalidUnfocused|ValidationStates|<xref:System.Windows.Controls.Validation.HasError%2A?displayProperty=nameWithType>添付プロパティは`true`がコントロールにフォーカスがないです。|  
  
## <a name="navigationwindow-controltemplate-example"></a>NavigationWindow ControlTemplate の例  
 この例には、すべての要素で定義されているが含まれますが、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Navigation.NavigationWindow>既定では、特定の値見なす必要がありますの例とします。  
  
 [!code-xaml[ControlTemplateExamples#NavigationWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/navigationwindow.xaml#navigationwindow)]  
  
 前の例では、次のリソースの 1 つ以上を使用します。  
  
 [!code-xaml[ControlTemplateExamples#ResizeGrip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/resizegrip.xaml#resizegrip)]  
[!code-xaml[ControlTemplateExamples#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/shared.xaml#resources)]  
  
 完全なサンプルについては、[Styling with ControlTemplates Sample](http://go.microsoft.com/fwlink/?LinkID=160041)を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.FrameworkElement.Style%2A>  
 <xref:System.Windows.Controls.ControlTemplate>  
 [コントロールのスタイルとテンプレート](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)  
 [コントロールのカスタマイズ](../../../../docs/framework/wpf/controls/control-customization.md)  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)
