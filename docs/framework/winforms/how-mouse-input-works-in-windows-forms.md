---
title: "Windows フォームにおけるマウス入力のしくみ | Microsoft Docs"
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
  - "マウス, 入力"
  - "Windows フォーム, マウス入力"
ms.assetid: 48fc5240-75a6-44bf-9fce-6aa21b49705a
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Windows フォームにおけるマウス入力のしくみ
マウス入力の受け取りと処理は、どの Windows アプリケーションでも重要です。  マウス イベントを処理してアプリケーションのアクションを実行したり、マウスの位置情報を使用してヒット テストなどのアクションを実行したりできます。  また、アプリケーションのコントロールがマウス入力を処理する方法を変更することもできます。  ここでは、マウス イベントの詳細と、マウスのシステム設定を取得して変更する方法について説明します。  マウス イベントで提供されるデータおよびマウスのクリック イベントの発生順序の詳細については、「[Windows フォームにおけるマウス イベント](../../../docs/framework/winforms/mouse-events-in-windows-forms.md)」を参照してください。  
  
## マウスの位置とヒット テスト  
 ユーザーがマウスを動かすと、オペレーティング システムによってマウス ポインターが移動します。  マウス ポインターには "ホット スポット" と呼ばれる単一ピクセルの領域が含まれます。オペレーティング システムは、この領域を追跡することによってポインターの位置を認識します。  ユーザーがマウスを動かすか、マウス ボタンを押すと、<xref:System.Windows.Forms.Cursor.HotSpot%2A> を含む <xref:System.Windows.Forms.Control> が適切なマウス イベントを発生させます。  現在のマウスの位置を取得するには、マウス イベントの処理時に <xref:System.Windows.Forms.MouseEventArgs> の <xref:System.Windows.Forms.MouseEventArgs.Location%2A> プロパティを使用するか、<xref:System.Windows.Forms.Cursor> クラスの <xref:System.Windows.Forms.Cursor.Position%2A> プロパティを使用します。  その後、マウスの位置情報を使用してヒット テストを実行し、マウスの位置に基づいてアクションを実行できます。  ヒット テスト機能は、Windows フォームの複数のコントロール \(<xref:System.Windows.Forms.ListView>、<xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.MonthCalendar>、および <xref:System.Windows.Forms.DataGridView>\) に組み込まれています。  ヒット テストを適切なマウス イベント \(たとえば、<xref:System.Windows.Forms.Control.MouseHover> など\) と組み合わせて使用すると、特定のアクションをアプリケーションがいつ実行するかを決定する上で便利です。  
  
## マウス イベント  
 マウス入力に応答する主な方法は、マウス イベントを処理することです。  マウス イベントの一覧と各マウス イベントの発生タイミングを次の表に示します。  
  
|マウス イベント|Description|  
|--------------|-----------------|  
|<xref:System.Windows.Forms.Control.Click>|このイベントは、マウス ボタンが離されると発生します。通常は、<xref:System.Windows.Forms.Control.MouseUp> イベントの前に発生します。  このイベントのハンドラーは、<xref:System.EventArgs> 型の引数を受け取ります。  クリックがいつ発生したかだけを判断する必要がある場合は、このイベントを処理します。|  
|<xref:System.Windows.Forms.Control.MouseClick>|このイベントは、ユーザーがマウスでコントロールをクリックすると発生します。  このイベントのハンドラーは、<xref:System.Windows.Forms.MouseEventArgs> 型の引数を受け取ります。  クリック発生時のマウスに関する情報を取得する必要がある場合は、このイベントを処理します。|  
|<xref:System.Windows.Forms.Control.DoubleClick>|このイベントは、コントロールがダブルクリックされると発生します。  このイベントのハンドラーは、<xref:System.EventArgs> 型の引数を受け取ります。  ダブルクリックがいつ発生したかだけを判断する必要がある場合は、このイベントを処理します。|  
|<xref:System.Windows.Forms.Control.MouseDoubleClick>|このイベントは、ユーザーがマウスでコントロールをダブルクリックすると発生します。  このイベントのハンドラーは、<xref:System.Windows.Forms.MouseEventArgs> 型の引数を受け取ります。  ダブルクリック発生時のマウスに関する情報を取得する必要がある場合は、このイベントを処理します。|  
|<xref:System.Windows.Forms.Control.MouseDown>|このイベントは、マウス ポインターがコントロール上にあるときに、ユーザーがマウス ボタンを押すと発生します。  このイベントのハンドラーは、<xref:System.Windows.Forms.MouseEventArgs> 型の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseEnter>|このイベントは、コントロールの種類に応じて、マウス ポインターがコントロールの境界またはクライアント領域に入ると発生します。  このイベントのハンドラーは、<xref:System.EventArgs> 型の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseHover>|このイベントは、マウス ポインターがコントロール上で停止したままになると発生します。  このイベントのハンドラーは、<xref:System.EventArgs> 型の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseLeave>|このイベントは、コントロールの種類に応じて、マウス ポインターがコントロールの境界またはクライアント領域から出ると発生します。  このイベントのハンドラーは、<xref:System.EventArgs> 型の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseMove>|このイベントは、マウス ポインターがコントロール上にあるときに移動すると発生します。  このイベントのハンドラーは、<xref:System.Windows.Forms.MouseEventArgs> 型の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseUp>|このイベントは、マウス ポインターがコントロール上にあるときに、ユーザーがマウス ボタンを離すと発生します。  このイベントのハンドラーは、<xref:System.Windows.Forms.MouseEventArgs> 型の引数を受け取ります。|  
|<xref:System.Windows.Forms.Control.MouseWheel>|このイベントは、コントロールにフォーカスがあるときに、ユーザーがマウス ホイールを回転させると発生します。  このイベントのハンドラーは、<xref:System.Windows.Forms.MouseEventArgs> 型の引数を受け取ります。  <xref:System.Windows.Forms.MouseEventArgs> の <xref:System.Windows.Forms.MouseEventArgs.Delta%2A> プロパティを使用して、マウスでどれだけスクロールしたかを判断できます。|  
  
## マウス入力の変更とシステム設定の検出  
 コントロールがマウス入力を処理する方法を検出して変更するには、コントロールから派生させ、<xref:System.Windows.Forms.Control.GetStyle%2A> メソッドと <xref:System.Windows.Forms.Control.SetStyle%2A> メソッドを使用します。  <xref:System.Windows.Forms.Control.SetStyle%2A> メソッドは、<xref:System.Windows.Forms.ControlStyles> 値のビットごとの組み合わせを受け取り、コントロールが標準のクリック動作とダブルクリック動作のどちらを行うか、またはコントロールが独自のマウス処理を行うかどうかを決定します。  また、<xref:System.Windows.Forms.SystemInformation> クラスは、マウスの機能を記述したプロパティを含み、マウスとオペレーティング システムの対話方法を指定します。  これらのプロパティの概要を次の表に示します。  
  
|プロパティ|Description|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>|2 回のクリックがオペレーティング システムによってダブルクリックであると認識されるために、ユーザーが 2 回クリックする必要がある領域の大きさ \(ピクセル単位\) を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A>|オペレーティング システムによってマウス操作がダブルクリックであると認識されるための、1 回目のクリックと 2 回目のクリックの間の最大経過時間 \(ミリ秒単位\) を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtons%2A>|マウスのボタンの数を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseButtonsSwapped%2A>|左右のマウス ボタンの機能が入れ替わっているかどうかを示す値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverSize%2A>|マウス静止メッセージが生成されるためにマウス静止時間が経過するまでマウス ポインターをとどめておく必要がある四角形の領域の大きさ \(ピクセル単位\) を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseHoverTime%2A>|マウス静止メッセージが生成されるために静止領域内にマウス ポインターをとどめておく必要がある時間 \(ミリ秒単位\) を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MousePresent%2A>|マウスが取り付けられているかどうかを示す値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseSpeed%2A>|現在のマウス速度を示す値 \(1 ～ 20\) を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelPresent%2A>|マウス ホイール付きのマウスが取り付けられているかどうかを示す値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollDelta%2A>|マウス ホイールの 1 目盛りの回転で増分される差分値を取得します。|  
|<xref:System.Windows.Forms.SystemInformation.MouseWheelScrollLines%2A>|マウス ホイールを回転したときにスクロールする行数を取得します。|  
  
## 参照  
 [Windows フォーム アプリケーションにおけるマウス入力](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)   
 [Windows フォームにおけるマウスのキャプチャ](../../../docs/framework/winforms/mouse-capture-in-windows-forms.md)   
 [Windows フォームにおけるマウス ポインター](../../../docs/framework/winforms/mouse-pointers-in-windows-forms.md)