---
title: "方法: つまみを使用してキャンバスのサイズを変更する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- resizing Canvas control [WPF]
- controls [WPF], Thumb
- controls [WPF], Canvas
- Thumb control [WPF]
- Canvas control [WPF]
ms.assetid: 7dc9f435-726c-4d4d-be41-eb24cfe17bef
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 757745b24c8e9e281d243cd15a5351b01d3479ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resize-a-canvas-by-using-a-thumb"></a>方法: つまみを使用してキャンバスのサイズを変更する
この例を使用する方法を示しています、<xref:System.Windows.Controls.Primitives.Thumb>コントロール サイズを変更する、<xref:System.Windows.Controls.Canvas>コントロール。  
  
## <a name="example"></a>例  
 <xref:System.Windows.Controls.Primitives.Thumb>コントロールに移動または監視することによってコントロールをサイズ変更に使用できるドラッグ機能が用意されています、 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>、<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>と<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>のイベント、<xref:System.Windows.Controls.Primitives.Thumb>です。  
  
 ボタンを押して、マウスの左上にマウス ポインターが一時停止すると、ユーザーがドラッグ操作を開始、<xref:System.Windows.Controls.Primitives.Thumb>コントロール。 マウスの左ボタンが押されている限り、ドラッグ操作が続行します。 ドラッグ操作中に、<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>複数回出現することができます。 これが発生するたびに、<xref:System.Windows.Controls.Primitives.DragDeltaEventArgs>クラスには、マウスの位置の変更に対応する位置の変更が用意されています。 ユーザーがマウスの左ボタンを離したときに、ドラッグ操作が完了しました。 ドラッグ操作を提供するだけ新しい座標です。自動的に再配置されない、<xref:System.Windows.Controls.Primitives.Thumb>です。  
  
 次の例は、<xref:System.Windows.Controls.Primitives.Thumb>であるコントロールの子要素、<xref:System.Windows.Controls.Canvas>コントロール。 イベント ハンドラーの<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>イベントに移動するロジックを提供する、<xref:System.Windows.Controls.Primitives.Thumb>サイズを変更して、<xref:System.Windows.Controls.Canvas>です。 対応するイベント ハンドラー、<xref:System.Windows.Controls.Primitives.Thumb.DragStarted>と<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>の色を変更するイベント、<xref:System.Windows.Controls.Primitives.Thumb>ドラッグ操作中にします。 次の例では定義、<xref:System.Windows.Controls.Primitives.Thumb>です。  
  
 [!code-xaml[Thumb#thumb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml#thumb)]  
  
 例を次に、<xref:System.Windows.Controls.Primitives.Thumb.DragDelta>を移動するイベント ハンドラー、<xref:System.Windows.Controls.Primitives.Thumb>のサイズを変更し、<xref:System.Windows.Controls.Canvas>マウスの動きに応答します。  
  
 [!code-csharp[Thumb#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#2)]  
  
 次の例は、<xref:System.Windows.Controls.Primitives.Thumb.DragStarted>イベント ハンドラー。  
  
 [!code-csharp[Thumb#DragStartedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragstartedhandler)]
 [!code-vb[Thumb#DragStartedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragstartedhandler)]  
  
 次の例は、<xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>イベント ハンドラー。  
  
 [!code-csharp[Thumb#DragCompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Thumb/CSharp/Pane1.xaml.cs#dragcompletedhandler)]
 [!code-vb[Thumb#DragCompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Thumb/VisualBasic/Pane1.xaml.vb#dragcompletedhandler)]  
  
 サンプル全体については、次を参照してください。 [Thumb ドラッグ機能のサンプル](http://go.microsoft.com/fwlink/?LinkID=160042)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.Primitives.Thumb>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragStarted>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragDelta>  
 <xref:System.Windows.Controls.Primitives.Thumb.DragCompleted>
