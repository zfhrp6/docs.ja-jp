---
title: "方法: つまみを使用してキャンバスのサイズを変更する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Canvas コントロール"
  - "コントロール, Canvas"
  - "コントロール, つまみ"
  - "サイズ変更 (キャンバス コントロールの)"
  - "つまみコントロール"
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法: つまみを使用してキャンバスのサイズを変更する
この例では、<xref:System.Windows.Controls.Primitives.Thumb> コントロールを使用して <xref:System.Windows.Controls.Canvas> コントロールのサイズを変更する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Controls.Primitives.Thumb> は、ドラッグ機能を実現するためのコントロールです。このコントロールを使用してコントロールを移動したりサイズを変更したりするには、<xref:System.Windows.Controls.Primitives.Thumb> の <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> イベント、<xref:System.Windows.Controls.Primitives.Thumb.DragDelta> イベント、および <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> イベントを監視します。  
  
 ユーザーがドラッグ操作を開始するときは、<xref:System.Windows.Controls.Primitives.Thumb> コントロール上にマウス ポインターを置いてマウスの左ボタンを押します。  ドラッグ操作は、マウスの左ボタンが押されている間続きます。  ドラッグ操作中に、<xref:System.Windows.Controls.Primitives.Thumb.DragDelta> が 2 回以上発生する可能性があります。  このイベントが発生するたびに、マウス位置の変化に対応するコントロール位置の変化の情報が <xref:System.Windows.Controls.Primitives.DragDeltaEventArgs> クラスに格納されます。  ユーザーがマウスの左ボタンを離すと、ドラッグ操作は終了します。  ドラッグ操作は新しい座標を示すだけで、<xref:System.Windows.Controls.Primitives.Thumb> の位置を自動的に変更することはありません。  
  
 <xref:System.Windows.Controls.Canvas> コントロールの子要素である <xref:System.Windows.Controls.Primitives.Thumb> コントロールの例を次に示します。  このコントロールの <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> イベントのイベント ハンドラーの中で、<xref:System.Windows.Controls.Primitives.Thumb> の移動や <xref:System.Windows.Controls.Canvas> のサイズ変更を行います。  <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> および <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> イベントのイベント ハンドラーによって、ドラッグ操作中の <xref:System.Windows.Controls.Primitives.Thumb> の色を変更します。  次の例では、<xref:System.Windows.Controls.Primitives.Thumb> を定義しています。  
  
 [!code-xml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 マウスの動きに応じて <xref:System.Windows.Controls.Primitives.Thumb> の移動や <xref:System.Windows.Controls.Canvas> のサイズ変更を行う <xref:System.Windows.Controls.Primitives.Thumb.DragDelta> イベント ハンドラーの例を次に示します。  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted> イベント ハンドラーの例を次に示します。  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted> イベント ハンドラーの例を次に示します。  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 サンプル全体については、[サム ドラッグ機能のサンプル](http://go.microsoft.com/fwlink/?LinkID=160042)を参照してください。  
  
## 参照  
 <xref:System.Windows.Controls.Primitives.Thumb>   
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>   
 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>   
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>