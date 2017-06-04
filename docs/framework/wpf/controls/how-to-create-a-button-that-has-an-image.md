---
title: "方法 : イメージを持つ Button を作成する | Microsoft Docs"
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
  - "Button コントロール [WPF], 作成"
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法 : イメージを持つ Button を作成する
この例では、<xref:System.Windows.Controls.Button> 上にイメージを含める方法を示します。  
  
## 使用例  
 次の例では、2 つの <xref:System.Windows.Controls.Button> コントロールを作成します。  1 つの <xref:System.Windows.Controls.Button> はテキストを含み、もう 1 つはイメージを含みます。  イメージは data と呼ばれるフォルダーにあります。このフォルダーは、例のプロジェクト フォルダーのサブフォルダーです。  ユーザーがイメージを持つ <xref:System.Windows.Controls.Button> をクリックすると、もう 1 つの <xref:System.Windows.Controls.Button> の背景とテキストが変化します。  
  
 この例では、マークアップを使用して <xref:System.Windows.Controls.Button> コントロールを作成しますが、<xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベント ハンドラーはコードで記述します。  
  
 [!code-xml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## 参照  
 [コントロール](../../../../docs/framework/wpf/controls/index.md)   
 [コントロール ライブラリ](../../../../docs/framework/wpf/controls/control-library.md)