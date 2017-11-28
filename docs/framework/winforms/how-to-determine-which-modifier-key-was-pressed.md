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
# <a name="how-to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="99a22-102">方法 : どの修飾子キーが押されたかを判断する</span><span class="sxs-lookup"><span data-stu-id="99a22-102">How to: Determine Which Modifier Key Was Pressed</span></span>
<span data-ttu-id="99a22-103">ユーザーのキー入力を受け付けるアプリケーションを作成するときの SHIFT、alt キーを押し、CTRL キーなどの修飾子キーの監視にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="99a22-103">When you create an application that accepts the user's keystrokes, you may also want to monitor for modifier keys such as the SHIFT, ALT, and CTRL keys.</span></span> <span data-ttu-id="99a22-104">修飾子キーが押されると組み合わせて、その他のキーを持つか、マウスのクリックで、アプリケーションが適切に応答できます。</span><span class="sxs-lookup"><span data-stu-id="99a22-104">When a modifier key is pressed in combination with other keys, or with mouse clicks, your application can respond appropriately.</span></span> <span data-ttu-id="99a22-105">たとえば、s が押された場合、画面に表示する"s"があるだけけれども、ctrl キーを押しながら S キーを押すと、現在のドキュメントが保存されます。</span><span class="sxs-lookup"><span data-stu-id="99a22-105">For example, if the letter S is pressed, this may simply cause an "s" to appear on the screen, but if the keys CTRL+S are pressed, the current document may be saved.</span></span> <span data-ttu-id="99a22-106">処理する場合、<xref:System.Windows.Forms.Control.KeyDown>イベント、<xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A>のプロパティ、<xref:System.Windows.Forms.KeyEventArgs>受信イベントにハンドラーを指定しますどの修飾子キーが押されました。</span><span class="sxs-lookup"><span data-stu-id="99a22-106">If you handle the <xref:System.Windows.Forms.Control.KeyDown> event, the <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A> property of the <xref:System.Windows.Forms.KeyEventArgs> received by the event handler specifies which modifier keys are pressed.</span></span> <span data-ttu-id="99a22-107">または、<xref:System.Windows.Forms.KeyEventArgs.KeyData%2A>プロパティ<xref:System.Windows.Forms.KeyEventArgs>同様のビットごとの OR と組み合わせると修飾子キーが押された文字を指定します。</span><span class="sxs-lookup"><span data-stu-id="99a22-107">Alternatively, the <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A> property of <xref:System.Windows.Forms.KeyEventArgs> specifies the character that was pressed as well as any modifier keys combined with a bitwise OR.</span></span> <span data-ttu-id="99a22-108">ただし、処理している場合、<xref:System.Windows.Forms.Control.KeyPress>イベントまたは、マウス イベント、イベント ハンドラーがこの情報を受け取りません。</span><span class="sxs-lookup"><span data-stu-id="99a22-108">However, if you are handling the <xref:System.Windows.Forms.Control.KeyPress> event or a mouse event, the event handler does not receive this information.</span></span> <span data-ttu-id="99a22-109">この場合、使用する必要があります、<xref:System.Windows.Forms.Control.ModifierKeys%2A>のプロパティ、<xref:System.Windows.Forms.Control>クラスです。</span><span class="sxs-lookup"><span data-stu-id="99a22-109">In this case, you must use the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property of the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="99a22-110">どちらの場合は、適切なビットごとの AND を実行する必要があります<xref:System.Windows.Forms.Keys>値とをテストする値。</span><span class="sxs-lookup"><span data-stu-id="99a22-110">In either case, you must perform a bitwise AND of the appropriate <xref:System.Windows.Forms.Keys> value and the value you are testing.</span></span> <span data-ttu-id="99a22-111"><xref:System.Windows.Forms.Keys>列挙には、演算を実行することが重要であるため、各修飾子キーの値が正しいとのバリエーションが提供しています。</span><span class="sxs-lookup"><span data-stu-id="99a22-111">The <xref:System.Windows.Forms.Keys> enumeration offers variations of each modifier key, so it is important that you perform the bitwise AND with the correct value.</span></span> <span data-ttu-id="99a22-112">たとえば、SHIFT キーがで表される<xref:System.Windows.Forms.Keys.Shift>、 <xref:System.Windows.Forms.Keys.ShiftKey>、<xref:System.Windows.Forms.Keys.RShiftKey>と<xref:System.Windows.Forms.Keys.LShiftKey>修飾子キーと shift キーを押しをテストする正しい値<xref:System.Windows.Forms.Keys.Shift>です。</span><span class="sxs-lookup"><span data-stu-id="99a22-112">For example, the SHIFT key is represented by <xref:System.Windows.Forms.Keys.Shift>, <xref:System.Windows.Forms.Keys.ShiftKey>, <xref:System.Windows.Forms.Keys.RShiftKey> and <xref:System.Windows.Forms.Keys.LShiftKey> The correct value to test SHIFT as a modifier key is <xref:System.Windows.Forms.Keys.Shift>.</span></span> <span data-ttu-id="99a22-113">同様に、する修飾子として ctlr 番号と alt キーをテストする必要がありますを使用して、<xref:System.Windows.Forms.Keys.Control>と<xref:System.Windows.Forms.Keys.Alt>それぞれ値します。</span><span class="sxs-lookup"><span data-stu-id="99a22-113">Similarly, to test for CTLR and ALT as modifiers you should use the <xref:System.Windows.Forms.Keys.Control> and <xref:System.Windows.Forms.Keys.Alt> values, respectively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99a22-114">Visual Basic プログラマは、を通じてキーの情報にもアクセスできます、<xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A>プロパティ</span><span class="sxs-lookup"><span data-stu-id="99a22-114">Visual Basic programmers can also access key information through the <xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A> property</span></span>  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a><span data-ttu-id="99a22-115">どの修飾子キーが押されたを決定するには</span><span class="sxs-lookup"><span data-stu-id="99a22-115">To determine which modifier key was pressed</span></span>  
  
-   <span data-ttu-id="99a22-116">演算を使用して`AND`演算子、<xref:System.Windows.Forms.Control.ModifierKeys%2A>プロパティと値の<xref:System.Windows.Forms.Keys>特定の修飾子キーが押されるかどうかを決定する列挙です。</span><span class="sxs-lookup"><span data-stu-id="99a22-116">Use the bitwise `AND` operator with the <xref:System.Windows.Forms.Control.ModifierKeys%2A> property and a value of the <xref:System.Windows.Forms.Keys> enumeration to determine whether a particular modifier key is pressed.</span></span> <span data-ttu-id="99a22-117">次のコード例で、SHIFT キーが押されたかどうかを確認する方法を示しています、<xref:System.Windows.Forms.Control.KeyPress>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="99a22-117">The following code example shows how to determine whether the SHIFT key is pressed within a <xref:System.Windows.Forms.Control.KeyPress> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="99a22-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="99a22-118">See Also</span></span>  
 <xref:System.Windows.Forms.Keys>  
 <xref:System.Windows.Forms.Control.ModifierKeys%2A>  
 [<span data-ttu-id="99a22-119">Windows フォーム アプリケーションにおけるキーボード入力</span><span class="sxs-lookup"><span data-stu-id="99a22-119">Keyboard Input in a Windows Forms Application</span></span>](../../../docs/framework/winforms/keyboard-input-in-a-windows-forms-application.md)  
 [<span data-ttu-id="99a22-120">方法: Visual basic での CapsLock の判断</span><span class="sxs-lookup"><span data-stu-id="99a22-120">How to: Determine If CapsLock is On in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/91e60f5c-dd61-4222-ba5f-39af803afd8c)
