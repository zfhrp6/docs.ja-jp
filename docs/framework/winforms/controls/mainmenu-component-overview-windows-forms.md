---
title: "MainMenu コンポーネントの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6f5cfe3a97bbbd4d5ba2d3ba089736599b6a2190
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="mainmenu-component-overview-windows-forms"></a>MainMenu コンポーネントの概要 (Windows フォーム)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.MenuStrip>と<xref:System.Windows.Forms.ContextMenuStrip>交換し、する機能を追加、<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>以前のバージョンでのコントロール<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>を選択した場合、旧バージョンとの互換性と将来の使用の両方に保持されます。  
  
 Windows フォーム<xref:System.Windows.Forms.MainMenu>コンポーネントには、実行時にメニューが表示されます。 メイン メニューと個々 の項目のすべてのサブメニューが<xref:System.Windows.Forms.MenuItem>オブジェクト。  
  
## <a name="key-properties"></a>主要プロパティ  
 メニュー項目は、設定して既定の項目として指定できる、<xref:System.Windows.Forms.MenuItem.DefaultItem%2A>プロパティを`true`です。 既定の項目は、メニューをクリックすると、太字のテキストに表示されます。 メニュー項目の<xref:System.Windows.Forms.MenuItem.Checked%2A>プロパティが、`true`または`false`、メニュー項目が選択されているかどうかを示します。 メニュー項目の<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>プロパティが選択された項目の外観をカスタマイズ: 場合<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>に設定されている`true`場合に、アイテムの横にあるラジオ ボタンが表示されます<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>に設定されている`false`項目の横にチェック マークを表示します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.MainMenu>  
 <xref:System.Windows.Forms.Menu>  
 <xref:System.Windows.Forms.MenuItem>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 [MenuStrip コントロールの概要](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
