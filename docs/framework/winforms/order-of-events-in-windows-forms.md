---
title: "Windows フォームのイベントの順序 | Microsoft Docs"
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
  - "アプリケーション終了イベントの順序"
  - "アプリケーション起動イベントの順序"
  - "イベント [Windows フォーム], 順序"
  - "フォーカス イベントの順序"
  - "手順, イベントの"
  - "検証イベント, 順序"
ms.assetid: e81db09b-4453-437f-b78a-62d7cd5c9829
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# Windows フォームのイベントの順序
Windows フォーム アプリケーションでイベントが発生する順序は、各イベントを順番に処理する必要がある開発者にとって重要な問題です。  フォームの構成要素を再描画するときなど、イベント処理に細心の注意が必要な状況では、実行時におけるイベントの正確な発生順序に気を配る必要があります。  このトピックでは、アプリケーションとコントロールの有効期間におけるいくつかの重要な段階での、イベントの順序について詳しく説明します。  マウス入力イベントの順序の詳細については、「[Windows フォームにおけるマウス イベント](../../../docs/framework/winforms/mouse-events-in-windows-forms.md)」を参照してください。  Windows フォームのイベントの概要については、「[イベントの概要](../../../docs/framework/winforms/events-overview-windows-forms.md)」を参照してください。  イベント ハンドラーの構成の詳細については、「[イベント ハンドラーの概要](../../../docs/framework/winforms/event-handlers-overview-windows-forms.md)」を参照してください。  
  
## アプリケーションのスタートアップ イベントとシャットダウン イベント。  
 <xref:System.Windows.Forms.Form> クラスおよび <xref:System.Windows.Forms.Control> クラスは、アプリケーションのスタートアップおよびシャットダウンに関連する一連のイベントを公開しています。  Windows フォーム アプリケーションが起動すると、メイン フォームのスタートアップ イベントが次の順序で発生します。  
  
-   <xref:System.Windows.Forms.Control.HandleCreated?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Control.BindingContextChanged?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Load?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Control.VisibleChanged?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Activated?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Shown?displayProperty=fullName>  
  
 アプリケーションを閉じると、メイン フォームのシャットダウン イベントが次の順序で発生します。  
  
-   <xref:System.Windows.Forms.Form.Closing?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.FormClosing?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Closed?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.FormClosed?displayProperty=fullName>  
  
-   <xref:System.Windows.Forms.Form.Deactivate?displayProperty=fullName>  
  
 <xref:System.Windows.Forms.Application> クラスの <xref:System.Windows.Forms.Application.ApplicationExit> イベントは、メイン フォームのシャットダウン イベントの後に発生します。  
  
> [!NOTE]
>  Visual Basic 2005 には、追加のアプリケーション イベント \(<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Startup?displayProperty=fullName> や <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.Shutdown?displayProperty=fullName> など\) があります。  
  
## フォーカス イベントと検証イベント  
 キーボード \(Tab、Shift \+ Tab など\) を使用するか、<xref:System.Windows.Forms.Control.Select%2A> メソッドまたは <xref:System.Windows.Forms.Control.SelectNextControl%2A> メソッドを呼び出すか、<xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> プロパティを現在のフォームに設定してフォーカスを変更すると、次の順序で <xref:System.Windows.Forms.Control> クラスのフォーカス イベントが発生します。  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
 マウスの使用、または <xref:System.Windows.Forms.Control.Focus%2A> メソッドの呼び出しによってフォーカスを変更すると、次の順序で <xref:System.Windows.Forms.Control> クラスのフォーカス イベントが発生します。  
  
-   <xref:System.Windows.Forms.Control.Enter>  
  
-   <xref:System.Windows.Forms.Control.GotFocus>  
  
-   <xref:System.Windows.Forms.Control.LostFocus>  
  
-   <xref:System.Windows.Forms.Control.Leave>  
  
-   <xref:System.Windows.Forms.Control.Validating>  
  
-   <xref:System.Windows.Forms.Control.Validated>  
  
## 参照  
 [Windows フォーム内でのイベント ハンドラーの作成](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)