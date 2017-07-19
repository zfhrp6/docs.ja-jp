---
title: "方法 : オブジェクトをマウス ポインターに追従させる | Microsoft Docs"
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
  - "カーソル (マウス ポインター), 追従させる (オブジェクトを)"
  - "マウス ポインター (カーソル) の追従"
  - "マウス ポインター (カーソル), 追従させる (オブジェクトを)"
ms.assetid: 50b20415-14bc-405c-baf3-2fb254fffde3
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : オブジェクトをマウス ポインターに追従させる
マウス ポインターが画面上で移動したときにオブジェクトのサイズを変更する方法を次の例に示します。  
  
 この例には、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] を作成する [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ファイルと、イベント ハンドラーを作成する分離コード ファイルが含まれます。  
  
## 使用例  
 次の [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] が作成する [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] は、<xref:System.Windows.Controls.StackPanel> の内部の <xref:System.Windows.Shapes.Ellipse> で構成され、<xref:System.Windows.UIElement.MouseMove> イベントのイベント ハンドラーを結合しています。  
  
 [!code-xml[mouseMoveWithPointer#MouseMoveWithPointerXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml#mousemovewithpointerxaml)]  
  
 次の分離コードでは、<xref:System.Windows.UIElement.MouseMove> イベント ハンドラーを作成します。  マウス ポインターが移動すると、<xref:System.Windows.Shapes.Ellipse> の高さと幅が増減します。  
  
 [!code-csharp[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseMoveWithPointer/CSharp/Window1.xaml.cs#mousemovepointergetposition)]
 [!code-vb[mouseMoveWithPointer#MouseMovePointerGetPosition](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseMoveWithPointer/VisualBasic/Window1.xaml.vb#mousemovepointergetposition)]  
  
## 参照  
 [入力の概要](../../../../docs/framework/wpf/advanced/input-overview.md)