---
title: "Windows フォームの MenuStrip コントロールへのメニュー項目のマージ | Microsoft Docs"
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
  - "MenuStrip, マージ"
  - "マージ, 一般的な概念"
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Windows フォームの MenuStrip コントロールへのメニュー項目のマージ
マルチ ドキュメント インターフェイス \(MDI: Multiple Document Interface\) アプリケーションがある場合、子フォームのメニュー項目またはメニュー全体を親フォームのメニューにマージできます。  
  
 このトピックでは、MDI アプリケーションでメニュー項目のマージに関連する基本概念について説明します。  
  
## 一般的な概念  
 マージ手順には、ターゲット コントロールとソース コントロールが関係します。  
  
-   ターゲットは、メニュー項目をマージするメイン フォームまたは MDI 親フォームの <xref:System.Windows.Forms.MenuStrip> コントロールです。  
  
-   ソースは、ターゲット メニューにマージするメニュー項目が含まれる MDI 子フォームの <xref:System.Windows.Forms.MenuStrip> コントロールです。  
  
 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A> プロパティは、作成するドロップダウン リストのメニュー項目を、現在の MDI 親フォームに対する MDI 子フォームのタイトルを使用して識別します。  たとえば、**\[ウィンドウ\]** メニューで現在開いている MDI の子フォームを列挙します。  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A> プロパティは、MDI 子フォームの <xref:System.Windows.Forms.MenuStrip> のどのメニュー項目を表示するかを指定します。  
  
 メニュー項目のマージは手動または自動で行うことができます。  どちらの方法でもメニュー項目は同様にマージされますが、マージをアクティブにする方法は異なります。詳細については、このトピックで後述する「手動マージ」と「自動マージ」を参照してください。  手動マージと自動マージのどちらでも、個々のマージ処理は次のマージ処理に影響します。  
  
 <xref:System.Windows.Forms.MenuStrip> のマージによって、ある <xref:System.Windows.Forms.ToolStrip> のメニュー項目を閉じずに他のメニュー項目に移動します。<xref:System.Windows.Forms.MainMenu> の場合と同様です。  
  
## MergeAction の値  
 <xref:System.Windows.Forms.MergeAction> プロパティを使用してソース <xref:System.Windows.Forms.MenuStrip> のメニュー項目にマージ処理を設定します。  
  
 次の表で、使用できるマージ処理の意味と一般的な使用法を説明します。  
  
|MergeAction の値|Description|一般的な用途|  
|--------------------|-----------------|------------|  
|<xref:System.Windows.Forms.MergeAction>|\(既定\) ターゲット項目のコレクションの末尾にソース項目を追加します。|プログラムの一部がアクティブな場合、メニューの末尾にメニュー項目を追加します。|  
|<xref:System.Windows.Forms.MergeAction>|ターゲット項目のコレクションのうち、ソース項目に設定された <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> プロパティに相当する場所にソース項目を追加します。|プログラムの一部がアクティブな場合、メニューの中間または先頭にメニュー項目を追加します。<br /><br /> <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 値がどちらのメニュー項目でも同じ場合、逆順で追加します。  元の順序を維持するには、<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> を適切に設定します。|  
|<xref:System.Windows.Forms.MergeAction>|一致するテキストを検索します。一致するテキストが見つからない場合は <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 値を使用します。次に、この一致するターゲット メニュー項目をソース メニュー項目で置換します。|ターゲット メニュー項目を、名前は同じで何かが異なるソース メニュー項目で置換します。|  
|<xref:System.Windows.Forms.MergeAction>|一致するテキストを検索します。一致するテキストが見つからない場合は <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 値を使用します。次に、ソースのすべてのドロップダウン項目をターゲットに追加します。|メニュー項目をサブメニューに挿入または追加したり、メニュー項目をサブメニューから削除したりするメニュー構造を構築します。  たとえば、MDI 子フォームのメニュー項目をメインの <xref:System.Windows.Forms.MenuStrip> の **\[名前を付けて保存\]** メニューに追加できます。<br /><br /> <xref:System.Windows.Forms.MergeAction> を使用すると、処理を実行しなくてもメニュー構造内を検索できます。  これは、以降の項目を評価する 1 つの方法です。|  
|<xref:System.Windows.Forms.MergeAction>|一致するテキストを検索します。一致するテキストが見つからない場合は <xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A> 値を使用します。次に、ターゲットから項目を削除します。|ターゲットの <xref:System.Windows.Forms.MenuStrip> からメニュー項目を削除します。|  
  
## 手動マージ  
 <xref:System.Windows.Forms.MenuStrip> コントロールのみが自動マージに参加します。  <xref:System.Windows.Forms.ToolStrip> や <xref:System.Windows.Forms.StatusStrip> など、他のコントロールの項目を結合するには、必要に応じて <xref:System.Windows.Forms.ToolStripManager.Merge%2A> メソッドと <xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A> メソッドをコードで呼び出して、手動でマージする必要があります。  
  
## 自動マージ  
 ソース フォームをアクティブにすることで、MDI アプリケーションの自動マージを使用できます。  MDI アプリケーションの <xref:System.Windows.Forms.MenuStrip> を使用するには、<xref:System.Windows.Forms.Form.MainMenuStrip%2A> プロパティをターゲットの <xref:System.Windows.Forms.MenuStrip> に設定します。これは、ソースの <xref:System.Windows.Forms.MenuStrip> で実行するマージ処理が、ターゲットの <xref:System.Windows.Forms.MenuStrip> に反映されるようにするためです。  
  
 MDI ソースで <xref:System.Windows.Forms.MenuStrip> をアクティブにすることで、自動マージをトリガーできます。  アクティブになると、ソース <xref:System.Windows.Forms.MenuStrip> は MDI のターゲットにマージされます。  新しいフォームがアクティブになると、前のフォームではマージが元の状態に戻り、新しいフォームでマージがトリガーされます。  この動作は、必要に応じて各 <xref:System.Windows.Forms.ToolStripItem> で <xref:System.Windows.Forms.ToolStripItem.MergeAction%2A> プロパティを設定する方法、および各 <xref:System.Windows.Forms.MenuStrip> で <xref:System.Windows.Forms.ToolStrip.AllowMerge%2A> プロパティを設定する方法で制御できます。  
  
## 参照  
 <xref:System.Windows.Forms.ToolStripManager>   
 <xref:System.Windows.Forms.MenuStrip>   
 [MenuStrip コントロール](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)   
 [方法 : MenuStrip を使用して MDI ウィンドウの一覧を作成する](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)   
 [方法 : MDI アプリケーションでメニューの自動マージを設定する](../../../../docs/framework/winforms/controls/how-to-set-up-automatic-menu-merging-for-mdi-applications.md)