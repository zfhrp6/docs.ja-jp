---
title: "Windows フォーム アプリケーションにおけるユーザー入力 | Microsoft Docs"
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
  - "Windows フォーム, ユーザー入力"
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# Windows フォーム アプリケーションにおけるユーザー入力
Windows フォームでのユーザー入力は、Windows メッセージの形式でアプリケーションに送られます。  これらのメッセージは、オーバーライドできる一連のメソッドにより、アプリケーション、フォーム、コントロールの各レベルで処理されます。  これらのメソッドがマウス メッセージやキーボード メッセージを受け取るとイベントが発生し、このイベントを処理することで、マウス入力やキーボード入力に関する情報を取得できます。  多くの場合、Windows フォーム アプリケーションは、これらのイベントを処理するだけですべてのユーザー入力を処理できますが、  アプリケーションによっては、アプリケーション、フォーム、またはコントロールよりも前に特定のメッセージを受け取ることができるように、メッセージを処理するメソッドのいずれかをオーバーライドする必要がある場合もあります。  
  
## マウス イベントとキーボード イベント  
 すべての Windows フォーム コントロールは、マウス入力とキーボード入力に関連するイベント セットを継承します。  たとえば、コントロールは、<xref:System.Windows.Forms.Control.KeyPress> イベントを処理して、押されたキーの文字コードを判別したり、<xref:System.Windows.Forms.Control.MouseClick> イベントを処理して、マウス クリックの位置を特定したりできます。  マウス イベントとキーボード イベントの詳細については、「[キーボード イベントの使用](../../../docs/framework/winforms/using-keyboard-events.md)」および「[Windows フォームにおけるマウス イベント](../../../docs/framework/winforms/mouse-events-in-windows-forms.md)」を参照してください。  
  
## ユーザー入力メッセージを処理するメソッド  
 フォームとコントロールは、<xref:System.Windows.Forms.IMessageFilter> インターフェイスと、メッセージ キュー内のさまざまな位置で Windows メッセージを処理する、オーバーライドできる一連のメソッドにアクセスできます。  これらのメソッドはすべて、Windows メッセージの下位の詳細情報をカプセル化する <xref:System.Windows.Forms.Message> パラメーターを使用します。  これらのメソッドを実装またはオーバーライドしてメッセージを調べてから、メッセージを使用したり、メッセージ キュー内の次のコンシューマーにメッセージを渡したりできます。  Windows フォームですべての Windows メッセージを処理するメソッドを次の表に示します。  
  
|メソッド|説明|  
|----------|--------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|キューに追加された \(またはポストされた\) Windows メッセージをアプリケーション レベルで受け取ります。|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|Windows メッセージが処理される前に、フォーム レベルまたはコントロール レベルでメッセージを受け取ります。|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|Windows メッセージをフォーム レベルまたはコントロール レベルで処理します。|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|Windows メッセージの既定の処理をフォーム レベルまたはコントロール レベルで実行します。  ウィンドウの最小限の機能を提供します。|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|メッセージが処理された後に、フォーム レベルまたはコントロール レベルでメッセージを受け取ります。  このメソッドが呼び出されるようにするには、<xref:System.Windows.Forms.ControlStyles> スタイル ビットを設定する必要があります。|  
  
 キーボード メッセージとマウス メッセージは、これらのメッセージの種類に固有の、オーバーライドできる追加のメソッドによっても処理されます。  詳細については、「[キーボード入力のしくみ](../../../docs/framework/winforms/how-keyboard-input-works.md)」および「[Windows フォームにおけるマウス入力のしくみ](../../../docs/framework/winforms/how-mouse-input-works-in-windows-forms.md)」を参照してください。  
  
## 参照  
 [Windows フォームでのユーザー入力](../../../docs/framework/winforms/user-input-in-windows-forms.md)   
 [Windows フォーム アプリケーションにおけるキーボード入力](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)   
 [Windows フォーム アプリケーションにおけるマウス入力](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)