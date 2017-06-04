---
title: "MenuStrip コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "MenuStrip"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "メニュー, 作成"
  - "MenuStrip コントロール [Windows フォーム], MenuStrip コントロールの概要"
ms.assetid: f45516e5-bf01-4468-b851-d45f4c33c055
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# MenuStrip コントロールの概要 (Windows フォーム)
メニューは、共通のテーマでグループ化されたコマンドを保持することによってユーザーにさまざまな機能を公開します。  
  
 <xref:System.Windows.Forms.MenuStrip> コントロールは、このバージョンの Visual Studio および .NET Framework で追加された新機能です。  このコントロールを使用すると、Microsoft Office に表示されるようなメニューを簡単に作成できます。  
  
 <xref:System.Windows.Forms.MenuStrip> コントロールは、マルチ ドキュメント インターフェイス \(MDI: Multiple Document Interface\) と、メニューのマージ、ツール ヒント、およびオーバーフローをサポートします。  アクセス キー、ショートカット キー、チェック マーク、イメージ、および区分線を追加してメニューの使いやすさと読みやすさを向上させることもできます。  
  
 <xref:System.Windows.Forms.MenuStrip> コントロールは、<xref:System.Windows.Forms.MainMenu> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.MainMenu> コントロールは、下位互換性を保持するため、および将来必要になったときに使用できるように保持されています。  
  
## MenuStrip コントロールの用途  
 <xref:System.Windows.Forms.MenuStrip> コントロールを使用すると、次のことができます。  
  
-   簡単にカスタマイズでき、一般的に使用できるだけでなく、高度なユーザー インターフェイス機能とレイアウト機能 \(テキストとイメージの並べ替えと配置、ドラッグ アンド ドロップ操作、MDI、オーバーフロー、およびメニュー コマンドにアクセスするための代替モード\) をサポートするメニューを作成する。  
  
-   オペレーティング システムの標準的な外観と動作をサポートする。  
  
-   他のコントロールのイベント処理と同じように、コンテナーおよびコンテナーに含まれる項目のすべてを一貫して処理する。  
  
 <xref:System.Windows.Forms.MenuStrip> および関連クラスの特に重要なプロパティのいくつかを次の表に示します。  
  
|プロパティ|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>|MDI 子フォームの一覧を表示するために使用する <xref:System.Windows.Forms.ToolStripMenuItem> を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A?displayProperty=fullName>|MDI アプリケーションの子メニューを親メニューにマージする方法を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A?displayProperty=fullName>|MDI アプリケーションのメニュー内のマージされた項目の位置を取得または設定します。|  
|<xref:System.Windows.Forms.Form.IsMdiContainer%2A?displayProperty=fullName>|フォームが MDI 子フォームのコンテナーであるかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.MenuStrip.ShowItemToolTips%2A>|<xref:System.Windows.Forms.MenuStrip> に対してツール ヒントを表示するかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.MenuStrip.CanOverflow%2A>|<xref:System.Windows.Forms.MenuStrip> がオーバーフロー機能をサポートするかどうかを示す値を取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>|<xref:System.Windows.Forms.ToolStripMenuItem> に関連付けられたショートカット キーを取得または設定します。|  
|<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>|<xref:System.Windows.Forms.ToolStripMenuItem> に関連付けられたショートカット キーを <xref:System.Windows.Forms.ToolStripMenuItem> の横に表示するかどうかを示す値を取得または設定します。|  
  
 重要な <xref:System.Windows.Forms.MenuStrip> コンパニオン クラスを次の表に示します。  
  
|Class|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<xref:System.Windows.Forms.MenuStrip> または <xref:System.Windows.Forms.ContextMenuStrip> に表示される選択可能なオプションを表します。|  
|<xref:System.Windows.Forms.ContextMenuStrip>|ショートカット メニューを表します。|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<xref:System.Windows.Forms.ToolStripDropDownButton> または上位レベルのメニュー項目をクリックしたときに表示される一覧から特定の項目を選択できるようにするコントロールを表します。|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|クリック時にドロップダウン項目を表示する、<xref:System.Windows.Forms.ToolStripItem> から派生するコントロールの基本機能を提供します。|  
  
## 参照  
 <xref:System.Windows.Forms.ToolStrip>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>   
 <xref:System.Windows.Forms.StatusStrip>   
 <xref:System.Windows.Forms.ToolStripItem>   
 <xref:System.Windows.Forms.ToolStripDropDown>