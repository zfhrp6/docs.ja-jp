---
title: "TabControl コントロールの概要 (Windows フォーム) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TabControl"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "プロパティ ページ, Windows フォーム"
  - "タブ ページ, タブ ページの概要"
  - "TabControl コントロール [Windows フォーム], TabControl コントロールの概要"
  - "Windows フォームのダイアログ ボックス, タブ"
ms.assetid: 2b4ea784-a39d-463c-81d8-af74ce068476
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# TabControl コントロールの概要 (Windows フォーム)
Windows フォーム <xref:System.Windows.Forms.TabControl> コントロールは、複数のタブを表示します。タブは、ノートの仕切りページやファイリング キャビネット内のフォルダーを分類するラベルのようなものです。  タブには画像やその他のコントロールを表示できます。  タブ コントロールを使用すると、複数のページを持つダイアログ ボックスを作成できます。このようなダイアログ ボックスは、Windows オペレーティング システムで数多く使用されています \(コントロール パネルから表示する \[画面のプロパティ\] ダイアログ ボックスなど\)。  さらに、<xref:System.Windows.Forms.TabControl> を使用して、関連プロパティをグループ化するためのプロパティ ページを作成できます。  
  
## TabControl の使用  
 <xref:System.Windows.Forms.TabControl> の主要プロパティは <xref:System.Windows.Forms.TabControl.TabPages%2A> です。このプロパティは、個別のタブを保持します。  個別のタブは <xref:System.Windows.Forms.TabPage> オブジェクトです。  タブがクリックされると、その <xref:System.Windows.Forms.TabPage> オブジェクトの <xref:System.Windows.Forms.Control.Click> イベントが発生します。  
  
## 参照  
 <xref:System.Windows.Forms.TabControl>   
 [TabControl コントロール](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)   
 [方法 : Windows フォーム TabControl の表示形式を変更する](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)   
 [方法 : タブ ページにコントロールを追加する](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)   
 [方法 : Windows フォーム TabControl のタブを追加および削除する](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)   
 [方法 : タブ ページを無効化する](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)   
 [Windows フォームのダイアログ ボックス](../../../../docs/framework/winforms/dialog-boxes-in-windows-forms.md)