---
title: "方法 : Enter キーが押されたことを検出する | Microsoft Docs"
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
  - "Enter キー, 検出"
  - "キー, Enter"
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : Enter キーが押されたことを検出する
キーボードで <xref:System.Windows.Input.Key> キーが押されたことを検出する方法を次の例に示します。  
  
 この例は、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルと分離コード ファイルで構成されています。  
  
## 使用例  
 ユーザーが <xref:System.Windows.Controls.TextBox> で <xref:System.Windows.Input.Key> キーを押すと、テキスト ボックスに入力された内容が[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] の別の領域に表示されます。  
  
 次の [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] は、<xref:System.Windows.Controls.StackPanel>、<xref:System.Windows.Controls.TextBlock>、および <xref:System.Windows.Controls.TextBox> で構成されるユーザー インターフェイスを作成します。  
  
 [!code-xml[keydown#KeyDownUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 次の分離コードでは、<xref:System.Windows.UIElement.KeyDown> イベント ハンドラーを作成します。  押されたキーが <xref:System.Windows.Input.Key> キーの場合は、<xref:System.Windows.Controls.TextBlock> にメッセージが表示されます。  
  
 [!code-csharp[keydown#KeyDownSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## 参照  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)   
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)