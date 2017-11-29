---
title: "イベント ハンドラーの概要 (Windows フォーム)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7353f3ab4513d8331b1d38cb01ad16c7d3cde165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="event-handlers-overview-windows-forms"></a>イベント ハンドラーの概要 (Windows フォーム)
イベント ハンドラーは、イベントにバインドされている方法です。 このイベントは、イベント ハンドラー内のコードが実行されます。 各イベント ハンドラーは、イベントを正しく処理することは 2 つのパラメーターを提供します。 次の例は、イベント ハンドラーを<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント。  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 最初のパラメーターでは、`sender`イベントを発生させたオブジェクトへの参照を提供します。 2 番目のパラメーターでは、 `e`、上記の例では、オブジェクトを渡します特定イベントを処理していることにします。 オブジェクトのプロパティ (および場合によっては、そのメソッド) を参照する、マウス イベントやドラッグ アンド ドロップのイベントで転送されるデータのマウスの位置などの情報を取得できます。  
  
 通常の各イベントには、2 番目のパラメーターの異なるイベント オブジェクト型を持つイベント ハンドラーが生成されます。 場合など、いくつかのイベント ハンドラー、<xref:System.Windows.Forms.Control.MouseDown>と<xref:System.Windows.Forms.Control.MouseUp>イベントを同じ型であるオブジェクトが 2 番目のパラメーターです。 この種のイベントでは、両方のイベントを処理するのに同じイベント ハンドラーを使用することができます。  
  
 同じイベント ハンドラーを使用して、異なるコントロールに同じイベントを処理することができますも。 グループがある場合など、<xref:System.Windows.Forms.RadioButton>フォーム上のコントロールの 1 つのイベント ハンドラーを作成する可能性があります、<xref:System.Windows.Forms.Control.Click>イベントにある各コントロールの<xref:System.Windows.Forms.Control.Click>イベントが 1 つのイベント ハンドラーにバインドします。 詳細については、次を参照してください。[する方法: Windows フォームの 1 つのイベント ハンドラーの複数のイベントを接続](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Windows フォーム内でのイベント ハンドラーの作成](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [イベントの概要](../../../docs/framework/winforms/events-overview-windows-forms.md)
