---
title: "方法 : Windows フォーム ContextMenu コンポーネントのメニュー項目を追加および削除する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コンテキスト メニュー, 追加 (アイテムを)"
  - "コンテキスト メニュー, 例"
  - "コンテキスト メニュー, 削除 (項目を)"
  - "ContextMenu コンポーネント [Windows フォーム], 追加 (アイテムを)"
  - "ContextMenu コンポーネント [Windows フォーム], 削除 (項目を)"
  - "例 [Windows フォーム], コンテキスト メニュー"
  - "ショートカット メニュー, 追加 (アイテムを)"
  - "ショートカット メニュー, 例"
  - "ショートカット メニュー, 削除 (項目を)"
ms.assetid: 426d1eaf-7fb8-4b0b-8a33-5e8721786ea4
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# 方法 : Windows フォーム ContextMenu コンポーネントのメニュー項目を追加および削除する
Windows フォームのショートカット メニューの項目を追加する方法および削除する方法を説明します。  
  
 Windows フォームの <xref:System.Windows.Forms.ContextMenu> コンポーネントには、選択したオブジェクトに関連付けられたコマンドのうち、頻繁に使用されるコマンドを簡単に実行するためのメニューが用意されています。  ショートカット メニューに項目を追加するには、<xref:System.Windows.Forms.MenuItem> オブジェクトを <xref:System.Windows.Forms.Menu.MenuItems%2A> コレクションに追加します。  
  
 ショートカット メニューから項目を完全に削除することもできますが、実行時にメニューを非表示または無効にした方がより適切です。  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.MenuStrip> と <xref:System.Windows.Forms.ContextMenuStrip> は、以前のバージョンの <xref:System.Windows.Forms.MainMenu> コントロールおよび <xref:System.Windows.Forms.ContextMenu> コントロールに代わると共に追加の機能を提供しますが、<xref:System.Windows.Forms.MainMenu> および <xref:System.Windows.Forms.ContextMenu> は、下位互換性を保つ目的および将来使用する目的で、必要に応じて保持できます。  
  
### ショートカット メニューから項目を削除するには  
  
1.  特定のメニュー項目を削除するには、<xref:System.Windows.Forms.ContextMenu> コンポーネントの <xref:System.Windows.Forms.Menu.MenuItems%2A> コレクションから、<xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A> メソッドまたは <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A> メソッドを使用します。  
  
    ```vb  
    ' Removes the first item in the shortcut menu.  
    ContextMenu1.MenuItems.RemoveAt(0)  
    ' Removes a particular object from the shortcut menu.  
    ContextMenu1.MenuItems.Remove(mnuItemNew)  
  
    ```  
  
    ```csharp  
    // Removes the first item in the shortcut menu.  
    contextMenu1.MenuItems.RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1.MenuItems.Remove(mnuItemNew);  
  
    ```  
  
    ```cpp  
    // Removes the first item in the shortcut menu.  
    contextMenu1->MenuItems->RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1->MenuItems->Remove(mnuItemNew);  
    ```  
  
     または  
  
2.  メニューからすべての項目を削除するには、<xref:System.Windows.Forms.ContextMenu> コンポーネントの `MenuItems` コレクションから、`Clear` メソッドを使用します。  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## 参照  
 <xref:System.Windows.Forms.ContextMenu>   
 [ContextMenu コンポーネント](../../../../docs/framework/winforms/controls/contextmenu-component-windows-forms.md)   
 [ContextMenu コンポーネントの概要](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md)