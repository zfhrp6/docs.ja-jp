---
title: "MainMenu コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
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
  - "MenuItem"
  - "MainMenu"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "MainMenu コントロール [Windows フォーム], MainMenu コントロールの概要"
  - "メニュー"
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# MainMenu コンポーネントの概要 (Windows フォーム)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.MenuStrip> と <xref:System.Windows.Forms.ContextMenuStrip> は、以前のバージョンの <xref:System.Windows.Forms.MainMenu> コントロールおよび <xref:System.Windows.Forms.ContextMenu> コントロールに代わると共に追加の機能を提供しますが、<xref:System.Windows.Forms.MainMenu> および <xref:System.Windows.Forms.ContextMenu> は、下位互換性を保つ目的および将来使用する目的で、必要に応じて保持できます。  
  
 Windows フォームの <xref:System.Windows.Forms.MainMenu> コンポーネントを使用すると、実行時にメニューが表示されます。  メイン メニューに属するすべてのサブメニューおよび各項目は <xref:System.Windows.Forms.MenuItem> オブジェクトです。  
  
## 主要なプロパティ  
 <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> プロパティを `true` に設定することによって、メニュー項目を既定の項目として指定できます。  既定の項目は、メニューをクリックしたときに太字のテキストで表示されます。  メニュー項目の <xref:System.Windows.Forms.MenuItem.Checked%2A> プロパティは、`true` または `false` のいずれかの値となり、メニュー項目が選択されているかどうかを示します。  メニュー項目の <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> プロパティは、選択されている項目の外観をカスタマイズします。<xref:System.Windows.Forms.MenuItem.RadioCheck%2A> が `true` に設定されている場合は、項目の横にオプション ボタンが表示され、<xref:System.Windows.Forms.MenuItem.RadioCheck%2A> が `false` に設定されている場合は、項目の横にチェック マークが表示されます。  
  
## 参照  
 <xref:System.Windows.Forms.MainMenu>   
 <xref:System.Windows.Forms.Menu>   
 <xref:System.Windows.Forms.MenuItem>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>   
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)