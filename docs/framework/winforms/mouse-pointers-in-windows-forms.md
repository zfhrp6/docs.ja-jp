---
title: "Windows フォームにおけるマウス ポインター | Microsoft Docs"
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
  - "カーソル, 設定 [Windows フォーム]"
  - "マウス カーソル"
  - "マウス ポインター"
  - "マウス ポインター, 設定 [Windows フォーム]"
  - "マウス, カーソル"
  - "ポインター, 設定 [Windows フォーム]"
ms.assetid: c3400d85-de5b-42e8-abc3-d6088d69ee53
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# Windows フォームにおけるマウス ポインター
カーソルとも呼ばれるマウス *ポインター*は、マウスでユーザー入力できるように画面上のフォーカス ポイントを指定するビットマップです。  ここでは、Windows フォームにおけるマウス ポインターについて概説し、マウス ポインターを変更および制御する方法をいくつか示します。  
  
## マウス ポインターへのアクセス  
 マウス ポインターは <xref:System.Windows.Forms.Cursor> クラスで表され、各 <xref:System.Windows.Forms.Control> にはそのコントロールのポインターを指定する <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=fullName> プロパティがあります。  <xref:System.Windows.Forms.Cursor> クラスには、ポインターを記述するプロパティ \(<xref:System.Windows.Forms.Cursor.Position%2A> プロパティや <xref:System.Windows.Forms.Cursor.HotSpot%2A> プロパティなど\) およびポインターの外観を変更できるメソッド \(<xref:System.Windows.Forms.Cursor.Show%2A> メソッド、<xref:System.Windows.Forms.Cursor.Hide%2A> メソッド、および <xref:System.Windows.Forms.Cursor.DrawStretched%2A> メソッドなど\) が含まれます。  
  
## マウス ポインターの制御  
 マウス ポインターの使用領域の制限やマウスの位置の変更が必要になることがあります。  <xref:System.Windows.Forms.Cursor> の <xref:System.Windows.Forms.Cursor.Position%2A> プロパティを使用すると、マウスの現在位置を取得または設定できます。  また、<xref:System.Windows.Forms.Cursor.Clip%2A> プロパティを設定することにより、マウス ポインターの使用領域を制限することもできます。  既定では、クリップ領域は画面全体です。  
  
## マウス ポインターの変更  
 マウス ポインターの変更は、ユーザーにフィードバックを提供するための重要な手段です。  たとえば、<xref:System.Windows.Forms.Control.MouseEnter> イベントおよび <xref:System.Windows.Forms.Control.MouseLeave> イベントのハンドラー内でマウス ポインターを変更することにより、計算を実行中であることをユーザーに通知し、コントロールでのユーザー操作を制限できます。  アプリケーションに対してドラッグ アンド ドロップ操作が行われた場合など、システム イベントによってマウス ポインターが変更されることもあります。  
  
 マウス ポインターを変更するための主な方法は、コントロールの <xref:System.Windows.Forms.Control.Cursor%2A?displayProperty=fullName> プロパティまたは <xref:System.Windows.Forms.Control.DefaultCursor%2A> プロパティを新しい <xref:System.Windows.Forms.Cursor> に設定することです。  マウス ポインターの変更例については、<xref:System.Windows.Forms.Cursor> クラスのコード例を参照してください。  また、<xref:System.Windows.Forms.Cursors> クラスでは、手の形をしたポインターなど、さまざまな種類のポインターを表す <xref:System.Windows.Forms.Cursor> オブジェクトのセットが公開されています。  マウス ポインターがコントロール上にあるときに砂時計の形をした待機ポインターを表示するには、<xref:System.Windows.Forms.Control> クラスの <xref:System.Windows.Forms.Control.UseWaitCursor%2A> プロパティを使用します。  
  
## 参照  
 <xref:System.Windows.Forms.Cursor>   
 [Windows フォーム アプリケーションにおけるマウス入力](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)   
 [Windows フォームにおけるドラッグ アンド ドロップ機能](../../../docs/framework/winforms/drag-and-drop-functionality-in-windows-forms.md)