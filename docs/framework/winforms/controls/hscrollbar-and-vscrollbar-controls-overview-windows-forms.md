---
title: "HScrollBar コントロールと VScrollBar コントロールの概要 (Windows フォーム) | Microsoft Docs"
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
  - "HScrollBar"
  - "VScrollBar"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "HScrollBar コントロール [Windows フォーム], HScrollBar の概要"
  - "スクロール バー, スクロール バーの概要"
  - "ScrollBar コントロール [Windows フォーム]"
  - "ScrollBar コントロール [Windows フォーム], ScrollBar コントロールの概要"
  - "VScrollBar コントロール [Windows フォーム], VScrollBar コントロールの概要"
ms.assetid: 8b307679-1cae-41d8-99aa-3d1efd207cd6
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# HScrollBar コントロールと VScrollBar コントロールの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.ScrollBar> コントロールを使用すると、アプリケーションまたはコントロール内で水平または垂直にスクロールすることにより、項目の長い一覧や大量の情報を簡単に見ることができるようになります。  スクロール バーは Windows インターフェイスの一般的な要素であるため、<xref:System.Windows.Forms.ScrollBar> コントロールは多くの場合、<xref:System.Windows.Forms.ScrollableControl> クラスから派生していないコントロールと共に使用されます。  同様に、多くの開発者は、独自のユーザー コントロールを作成するときに <xref:System.Windows.Forms.ScrollBar> コントロールを使用します。  
  
 <xref:System.Windows.Forms.HScrollBar> \(水平\) コントロールおよび <xref:System.Windows.Forms.VScrollBar> \(垂直\) コントロールは他のコントロールとは独立して動作し、独自のイベント、プロパティ、およびメソッドのセットを備えています。  <xref:System.Windows.Forms.ScrollBar> コントロールは、テキスト ボックス、リスト ボックス、コンボ ボックス、または MDI フォームに結び付けられている組み込みのスクロール バーとは異なります。<xref:System.Windows.Forms.TextBox> コントロールには、コントロールに結び付けられているスクロール バーを表示または非表示にするための <xref:System.Windows.Forms.TextBox.ScrollBars%2A> プロパティがあります。  
  
 <xref:System.Windows.Forms.ScrollBar> コントロールは、<xref:System.Windows.Forms.ScrollBar.Scroll> イベントを使用して、スクロール バーに沿ったスクロール ボックスの動きを監視します。スクロール ボックスは、"つまみ" とも呼ばれます。  <xref:System.Windows.Forms.ScrollBar.Scroll> イベントを使用すると、スクロール バーがドラッグされているときにスクロール バーの値にアクセスできます。  
  
## Value プロパティ  
 <xref:System.Windows.Forms.ScrollBar.Value%2A> プロパティ \(既定では 0\) は、スクロール バー内でのスクロール ボックスの位置に対応する `integer` 値です。  スクロール ボックスの値が最小の場合、スクロール ボックスは水平スクロール バーの左端、または垂直スクロール バーの上端に移動します。  スクロール ボックスの値が最大の場合、スクロール ボックスは右端または下端に移動します。  同様に、最大と最小の中間の値では、スクロール ボックスの先端はスクロール バーの中央に位置します。  
  
 マウスをクリックしてスクロール バーの値を変更する以外に、ユーザーはスクロール ボックスをバー上の任意の位置にドラッグすることもできます。  結果の値はスクロール ボックスの位置によって決まりますが、常にユーザーによって設定された <xref:System.Windows.Forms.ScrollBar.Minimum%2A> プロパティから <xref:System.Windows.Forms.ScrollBar.Maximum%2A> プロパティまでの範囲内にあります。  
  
## LargeChange プロパティおよび SmallChange プロパティ  
 ユーザーが PageUp キーか PageDown キーを押すか、またはスクロール ボックスのどちらかの側でスクロール バー領域をクリックすると、<xref:System.Windows.Forms.ScrollBar.LargeChange%2A> プロパティに設定された値に従って <xref:System.Windows.Forms.ScrollBar.Value%2A> プロパティが変化します。  
  
 ユーザーがいずれかの方向キーを押すか、またはスクロール バーのいずれかのボタンをクリックすると、<xref:System.Windows.Forms.ScrollBar.SmallChange%2A> プロパティに設定された値に従って <xref:System.Windows.Forms.ScrollBar.Value%2A> プロパティが変化します。  
  
## 参照  
 <xref:System.Windows.Forms.HScrollBar>   
 <xref:System.Windows.Forms.VScrollBar>   
 [Additions to Windows Forms for the .NET Framework 2.0](http://msdn.microsoft.com/ja-jp/c61a923d-3d6a-4c8c-820c-e94c83f3f9a8)   
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)