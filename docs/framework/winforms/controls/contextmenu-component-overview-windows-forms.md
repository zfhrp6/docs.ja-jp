---
title: "ContextMenu コンポーネントの概要 (Windows フォーム) | Microsoft Docs"
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
  - "ContextMenu"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "コンテキスト メニュー, ContextMenu コンポーネント"
  - "ContextMenu コンポーネント [Windows フォーム], ContextMenu コンポーネントの概要"
  - "ショートカット メニュー, ContextMenu コンポーネント"
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# ContextMenu コンポーネントの概要 (Windows フォーム)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.MenuStrip> と <xref:System.Windows.Forms.ContextMenuStrip> は、以前のバージョンの <xref:System.Windows.Forms.MainMenu> コントロールおよび <xref:System.Windows.Forms.ContextMenu> コントロールに代わると共に追加の機能を提供しますが、<xref:System.Windows.Forms.MainMenu> および <xref:System.Windows.Forms.ContextMenu> は、下位互換性を保つ目的および将来使用する目的で、必要に応じて保持できます。  
  
 Windows フォームの <xref:System.Windows.Forms.ContextMenu> コンポーネントには、選択したオブジェクトに関連付けられたコマンドのうち、頻繁に使用されるコマンドを簡単に実行するためのメニューが用意されています。  ショートカット メニューの項目は、多くの場合、アプリケーションの他の場所に表示されるメイン メニューの項目のサブセットです。  ユーザーは、通常、マウスを右クリックしてショートカット メニューにアクセスします。  Windows フォームでは、ショートカット メニューはコントロールに関連付けられています。  
  
## 主要なプロパティ  
 ショートカット メニューをコントロールに関連付けるには、コントロールの <xref:System.Windows.Forms.Control.ContextMenu%2A> プロパティに <xref:System.Windows.Forms.ContextMenu> コンポーネントを設定します。  1 つのショートカット メニューを複数のコントロールに関連付けることができますが、各コントロールに設定できるショートカット メニューは 1 つだけです。  
  
 <xref:System.Windows.Forms.ContextMenu> コンポーネントの主要なプロパティは、<xref:System.Windows.Forms.Menu.MenuItems%2A> プロパティです。  メニュー項目を作成するには、プログラムで <xref:System.Windows.Forms.MenuItem> オブジェクトを作成し、これらのオブジェクトをショートカット メニューの <xref:System.Windows.Forms.Menu.MenuItemCollection> に追加します。  ショートカット メニューの項目は、通常、他のメニューを基に作成するため、他のメニュー項目をコピーしてショートカット メニューに追加するのが一般的な方法です。  
  
## 参照  
 <xref:System.Windows.Forms.ContextMenu>   
 <xref:System.Windows.Forms.MenuStrip>   
 <xref:System.Windows.Forms.ContextMenuStrip>