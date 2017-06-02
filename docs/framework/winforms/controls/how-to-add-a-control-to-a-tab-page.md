---
title: "方法 : タブ ページにコントロールを追加する | Microsoft Docs"
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
  - "タブ コントロール, タブ オーダー"
  - "タブ ページ, 追加 (コントロールを)"
  - "TabPage コントロール"
ms.assetid: b092532e-7346-469f-b9a1-897f9bea4fb7
caps.latest.revision: 19
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 19
---
# 方法 : タブ ページにコントロールを追加する
Windows フォーム <xref:System.Windows.Forms.TabControl> を使用すると、他のコントロールを整理して表示できます。  次の手順は、最初のタブにボタンを追加する方法を示しています。  タブ ページのラベル部分にアイコンを追加する方法の詳細については、「[方法 : Windows フォーム TabControl の表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)」を参照してください。  
  
### プログラムによってコントロールを追加するには  
  
1.  <xref:System.Windows.Forms.TabPage> の <xref:System.Windows.Forms.Control.Controls%2A> プロパティから返されたコレクションの <xref:System.Windows.Forms.Control.ControlCollection.Add%2A> メソッドを使用します。  
  
     [!code-cpp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cpp/add.cpp#1)]
     [!code-csharp[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/cs/add.cs#1)]
     [!code-vb[TabPageControlCollectionHowToAdd#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/tabpagecontrolcollectionhowtoadd/vb/add.vb#1)]  
  
## 参照  
 [TabControl コントロール](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)   
 [TabControl コントロールの概要](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)   
 [方法 : Windows フォーム TabControl の表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)   
 [方法 : タブ ページを無効化する](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)   
 [方法 : Windows フォーム TabControl のタブを追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)