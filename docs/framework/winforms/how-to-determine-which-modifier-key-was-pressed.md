---
title: "方法 : どの修飾子キーが押されたかを判断する"
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
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6fdc93063bbc8c9428f2f01c6cd5c0578e77ab01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>方法 : どの修飾子キーが押されたかを判断する
ユーザーのキー入力を受け付けるアプリケーションを作成するときの SHIFT、alt キーを押し、CTRL キーなどの修飾子キーの監視にすることもできます。 修飾子キーが押されると組み合わせて、その他のキーを持つか、マウスのクリックで、アプリケーションが適切に応答できます。 たとえば、s が押された場合、画面に表示する"s"があるだけけれども、ctrl キーを押しながら S キーを押すと、現在のドキュメントが保存されます。 処理する場合、<xref:System.Windows.Forms.Control.KeyDown>イベント、<xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A>のプロパティ、<xref:System.Windows.Forms.KeyEventArgs>受信イベントにハンドラーを指定しますどの修飾子キーが押されました。 または、<xref:System.Windows.Forms.KeyEventArgs.KeyData%2A>プロパティ<xref:System.Windows.Forms.KeyEventArgs>同様のビットごとの OR と組み合わせると修飾子キーが押された文字を指定します。 ただし、処理している場合、<xref:System.Windows.Forms.Control.KeyPress>イベントまたは、マウス イベント、イベント ハンドラーがこの情報を受け取りません。 この場合、使用する必要があります、<xref:System.Windows.Forms.Control.ModifierKeys%2A>のプロパティ、<xref:System.Windows.Forms.Control>クラスです。 どちらの場合は、適切なビットごとの AND を実行する必要があります<xref:System.Windows.Forms.Keys>値とをテストする値。 <xref:System.Windows.Forms.Keys>列挙には、演算を実行することが重要であるため、各修飾子キーの値が正しいとのバリエーションが提供しています。 たとえば、SHIFT キーがで表される<xref:System.Windows.Forms.Keys.Shift>、 <xref:System.Windows.Forms.Keys.ShiftKey>、<xref:System.Windows.Forms.Keys.RShiftKey>と<xref:System.Windows.Forms.Keys.LShiftKey>修飾子キーと shift キーを押しをテストする正しい値<xref:System.Windows.Forms.Keys.Shift>です。 同様に、する修飾子として ctlr 番号と alt キーをテストする必要がありますを使用して、<xref:System.Windows.Forms.Keys.Control>と<xref:System.Windows.Forms.Keys.Alt>それぞれ値します。  
  
> [!NOTE]
>  Visual Basic プログラマは、を通じてキーの情報にもアクセスできます、<xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A>プロパティ  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>どの修飾子キーが押されたを決定するには  
  
-   演算を使用して`AND`演算子、<xref:System.Windows.Forms.Control.ModifierKeys%2A>プロパティと値の<xref:System.Windows.Forms.Keys>特定の修飾子キーが押されるかどうかを決定する列挙です。 次のコード例で、SHIFT キーが押されたかどうかを確認する方法を示しています、<xref:System.Windows.Forms.Control.KeyPress>イベント ハンドラー。  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>  
 [Windows フォーム アプリケーションにおけるキーボード入力](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [方法: Visual basic での CapsLock の判断](http://msdn.microsoft.com/en-us/91e60f5c-dd61-4222-ba5f-39af803afd8c)
