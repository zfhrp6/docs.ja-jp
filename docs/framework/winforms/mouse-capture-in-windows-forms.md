---
title: "Windows フォームにおけるマウスのキャプチャ | Microsoft Docs"
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
  - "マウス, キャプチャ"
ms.assetid: 8911d4b0-a4f8-4f93-8246-371aebd27d0c
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# Windows フォームにおけるマウスのキャプチャ
*マウスのキャプチャ*とは、コントロールがすべてのマウス入力のコマンドを受け取ることを意味します。  コントロールがマウスをキャプチャしている場合は、マウス ポインターが境界内にあるかどうかにかかわらず、マウス入力を受け取ります。  
  
## マウスのキャプチャの設定  
 Windows フォーム内では、マウスは、ユーザーがコントロール上でマウス ボタンを押した時にコントロールによってキャプチャされ、ユーザーがマウス ボタンを離したときにコントロールによって解放されます。  
  
 <xref:System.Windows.Forms.Control> クラスの <xref:System.Windows.Forms.Control.Capture%2A> プロパティは、コントロールがマウスをキャプチャしているかどうかを指定します。  コントロールがマウスのキャプチャをいつ失ったかを判断するには、<xref:System.Windows.Forms.Control.MouseCaptureChanged> イベントを処理します。  
  
 手前のウィンドウだけがマウスをキャプチャできます。  背面のウィンドウがマウスをキャプチャしようとすると、ウィンドウは、マウス ポインターがウィンドウの表示部分内にあるときに発生したマウス イベントのメッセージだけを受け取ります。  また、前面のウィンドウがマウスをキャプチャした場合でも、ユーザーは別のウィンドウをクリックすると、そのウィンドウを前面に表示できます。  マウスがキャプチャされると、ショートカット キーは動作しません。  
  
## 参照  
 [Windows フォーム アプリケーションにおけるマウス入力](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)