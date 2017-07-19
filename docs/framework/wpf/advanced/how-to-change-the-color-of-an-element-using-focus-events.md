---
title: "方法 : フォーカス イベントを使用して要素の色を変更する | Microsoft Docs"
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
  - "要素, 変更 (色を)"
  - "フォーカス イベント, 変更 (要素の色を)"
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : フォーカス イベントを使用して要素の色を変更する
要素がフォーカスを取得したときや失ったときに <xref:System.Windows.UIElement.GotFocus> イベントおよび <xref:System.Windows.UIElement.LostFocus> イベントを使用してその要素の色を変更する方法を次の例に示します。  
  
 この例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルと分離コード ファイルで構成されています。  
  
## 使用例  
 次に示す [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] では、2 つの <xref:System.Windows.Controls.Button> オブジェクトで構成されるユーザー インターフェイスを作成し、<xref:System.Windows.UIElement.GotFocus> イベントと <xref:System.Windows.UIElement.LostFocus> イベントのイベント ハンドラーを <xref:System.Windows.Controls.Button> オブジェクトに結び付けます。  
  
 [!code-xml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 次の分離コードでは、<xref:System.Windows.UIElement.GotFocus> および <xref:System.Windows.UIElement.LostFocus> イベント ハンドラーを作成します。  <xref:System.Windows.Controls.Button> がキーボード フォーカスを取得すると、<xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.Control.Background%2A> が赤に変更されます。  <xref:System.Windows.Controls.Button> がキーボード フォーカスを失うと、<xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.Control.Background%2A> が白に変更されます。  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## 参照  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)