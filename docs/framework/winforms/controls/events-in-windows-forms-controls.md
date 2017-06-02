---
title: "Windows フォーム コントロールのイベント | Microsoft Docs"
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
  - "カスタム コントロール [Windows フォーム], イベントの概要 (コードを使用)"
  - "イベント [Windows フォーム], カスタム コントロール (コードを使用した)"
ms.assetid: 7e3d1379-87aa-437c-afce-c99454eff30e
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Windows フォーム コントロールのイベント
Windows フォーム コントロールは、<xref:System.Windows.Forms.Control?displayProperty=fullName> から 60 を越えるイベントを継承します。  これらには、コントロールを描画する <xref:System.Windows.Forms.Control.Paint> イベント、ウィンドウの表示に関連するイベント \(<xref:System.Windows.Forms.Control.Resize> イベントや <xref:System.Windows.Forms.Control.Layout> イベントなど\)、下位のマウス イベントやキーボード イベントなどがあります。  <xref:System.Windows.Forms.Control> は、いくつかの下位のイベントを合成して <xref:System.Windows.Forms.Control.Click> や <xref:System.Windows.Forms.Control.DoubleClick> などの意味イベントを作成します。  継承されるイベントの詳細については、<xref:System.Windows.Forms.Control> に関するトピックを参照してください。  
  
 カスタム コントロールが継承したイベントの機能をオーバーライドする必要がある場合は、デリゲートを割り当てる代わりに継承した `On`*EventName* メソッドをオーバーライドします。  .NET Framework のイベント モデルの詳細については、「[コンポーネントからのイベントの生成](../Topic/Raising%20Events%20from%20a%20Component.md)」を参照してください。  
  
## 参照  
 [OnPaint メソッドのオーバーライド](../../../../docs/framework/winforms/controls/overriding-the-onpaint-method.md)   
 [ユーザーの入力の処理](../../../../docs/framework/winforms/controls/handling-user-input.md)   
 [イベントの定義](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)   
 [イベント](../../../../docs/standard/events/index.md)