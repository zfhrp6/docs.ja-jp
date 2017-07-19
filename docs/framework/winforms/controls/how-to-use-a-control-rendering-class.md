---
title: "方法 : コントロールの描画クラスを使用する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "プロフェッショナルな外観, 描画 (Windows フォーム コントロールの)"
  - "視覚スタイル, 描画 (Windows フォーム コントロールの)"
  - "ビジュアル テーマ, 適用 (Windows フォーム コントロールに)"
ms.assetid: c0125e34-cd74-4c35-818c-3e40f462b0a3
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : コントロールの描画クラスを使用する
<xref:System.Windows.Forms.ComboBoxRenderer> クラスを使用してコンボ ボックス コントロールのドロップダウン矢印を表示する方法を次の例に示します。  この例は単純なカスタム コントロールの <xref:System.Windows.Forms.Control.OnPaint%2A> メソッドで構成されています。  <xref:System.Windows.Forms.ComboBoxRenderer.IsSupported%2A?displayProperty=fullName> プロパティを使用して、アプリケーション ウィンドウのクライアント領域で visual スタイルを有効にするかどうかを指定します。  visual スタイルをアクティブにすると、<xref:System.Windows.Forms.ComboBoxRenderer.DrawDropDownButton%2A?displayProperty=fullName> メソッドは、visual スタイルを使用してドロップダウン矢印を表示します。アクティブでない場合、<xref:System.Windows.Forms.ControlPaint.DrawComboButton%2A?displayProperty=fullName> メソッドは従来の Windows スタイルでドロップダウン矢印を表示します。  
  
## 使用例  
 [!code-cpp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/cpp/form1.cpp#10)]
 [!code-csharp[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/CS/form1.cs#10)]
 [!code-vb[System.Windows.Forms_ControlRenderer#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms_ControlRenderer/VB/form1.vb#10)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   <xref:System.Windows.Forms.Control> クラスから派生したカスタム コントロール。  
  
-   カスタム コントロールをホストする <xref:System.Windows.Forms.Form>。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Drawing?displayProperty=fullName>、<xref:System.Windows.Forms?displayProperty=fullName>、および <xref:System.Windows.Forms.VisualStyles?displayProperty=fullName> の各名前空間への参照。  
  
## 参照  
 [visual スタイルが使用されているコントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)