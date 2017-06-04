---
title: "イベント ハンドラーの概要 (Windows フォーム) | Microsoft Docs"
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
  - "イベント ハンドラー, イベント ハンドラーの概要"
  - "イベント処理, Windows フォーム"
  - "Windows フォーム, イベント処理"
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# イベント ハンドラーの概要 (Windows フォーム)
イベント ハンドラーは、イベントに関連付けられたメソッドです。  イベントが発生すると、イベント ハンドラーのコードが実行されます。  各イベント ハンドラーには、イベントを適切に処理するためのパラメーターが 2 つ用意されています。  <xref:System.Windows.Forms.Button> コントロールの <xref:System.Windows.Forms.Control.Click> イベントのイベント ハンドラーの例を次に示します。  
  
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
  
 最初のパラメーターは`sender`イベントを発生させたオブジェクトへの参照を提供します。  2 番目のパラメーター `e`では、処理されるイベントに応じた特定のオブジェクトを渡します。  このオブジェクトのプロパティ \(場合によってはメソッド\) を参照すると、マウス イベントのマウスの位置や、ドラッグ アンド ドロップ イベントで転送されるデータなどの情報を取得できます。  
  
 通常、イベントごとに生成されるイベント ハンドラーでは、2 番目に指定されるイベント オブジェクトの種類がそれぞれ異なります。  <xref:System.Windows.Forms.Control.MouseDown> イベントや <xref:System.Windows.Forms.Control.MouseUp> イベントなどのイベント ハンドラーでは、2 番目のパラメーターが同じオブジェクト型になっています。  この種類のイベントでは、同じイベント ハンドラーを使用して両方のイベントを処理できます。  
  
 また、同じイベント ハンドラーを使用して、異なるコントロールに対する同じイベントを処理することもできます。  たとえば、フォームに <xref:System.Windows.Forms.RadioButton> コントロールのグループがある場合は、<xref:System.Windows.Forms.Control.Click> イベントに対して 1 つのイベント ハンドラーを作成し、各コントロールの <xref:System.Windows.Forms.Control.Click> イベントをこの単独のイベント ハンドラーにバインドできます。  詳細については、「[方法 : Windows フォームの 1 つのイベント ハンドラーに複数のイベントを関連付ける](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)」を参照してください。  
  
## 参照  
 [Windows フォーム内でのイベント ハンドラーの作成](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)   
 [イベントの概要](../../../docs/framework/winforms/events-overview-windows-forms.md)