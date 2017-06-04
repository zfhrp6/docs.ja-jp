---
title: "方法 : visual スタイル要素を描画する | Microsoft Docs"
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
  - "プロフェッショナルな外観, 適用 (Windows フォーム アプリケーションの要素に)"
  - "視覚スタイル, 描画 (Windows フォーム コントロールの)"
  - "ビジュアル テーマ, 適用 (Windows フォーム アプリケーションの要素に)"
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : visual スタイル要素を描画する
<xref:System.Windows.Forms.VisualStyles?displayProperty=fullName> 名前空間は、visual スタイルによってサポートされている Windows のユーザー インターフェイス \(UI\) を表す <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> オブジェクトを公開します。  このトピックでは、\[スタート\] メニューの **\[ログオフ\]** ボタンと **\[シャットダウン\]** ボタンを表す <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> を描画する <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> クラスの使用法を説明します。  
  
### visual スタイル要素を描画するには  
  
1.  <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> を作成し、これを描画対象の要素に設定します。  <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=fullName> プロパティと <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=fullName> メソッドの使用に注意してください。visual スタイルが無効にされている、または要素が未定義の場合、<xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> コンストラクターは例外をスローします。  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2.  <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> メソッドを呼び出して <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> が現在表す要素を描画します。  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## コードのコンパイル  
 この例には、次の項目が必要です。  
  
-   <xref:System.Windows.Forms.Control> クラスから派生したカスタム コントロール。  
  
-   カスタム コントロールをホストする <xref:System.Windows.Forms.Form>。  
  
-   <xref:System?displayProperty=fullName>、<xref:System.Drawing?displayProperty=fullName>、<xref:System.Windows.Forms?displayProperty=fullName>、および <xref:System.Windows.Forms.VisualStyles?displayProperty=fullName> の各名前空間への参照。  
  
## 参照  
 [visual スタイルが使用されているコントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)