---
title: "方法 : Visual Basic でシリアル ポートから文字列を受信する"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 500a6c651f6eb991eb9fefef601d0f593a38352f
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a><span data-ttu-id="b6049-102">方法 : Visual Basic でシリアル ポートから文字列を受信する</span><span class="sxs-lookup"><span data-stu-id="b6049-102">How to: Receive Strings From Serial Ports in Visual Basic</span></span>
<span data-ttu-id="b6049-103">このトピックでは、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] で `My.Computer.Ports` を使用して、コンピューターのシリアルポートから文字列を受信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b6049-103">This topic describes how to use `My.Computer.Ports` to receive strings from the computer's serial ports in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
### <a name="to-receive-strings-from-the-serial-port"></a><span data-ttu-id="b6049-104">シリアル ポートから文字列を受信する</span><span class="sxs-lookup"><span data-stu-id="b6049-104">To receive strings from the serial port</span></span>  
  
1.  <span data-ttu-id="b6049-105">戻り値の文字列を初期化します。</span><span class="sxs-lookup"><span data-stu-id="b6049-105">Initialize the return string.</span></span>  
  
     <span data-ttu-id="b6049-106">[!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6049-106">[!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]</span></span>  
  
2.  <span data-ttu-id="b6049-107">どのシリアル ポートから文字列を取得するのかを決定します。</span><span class="sxs-lookup"><span data-stu-id="b6049-107">Determine which serial port should provide the strings.</span></span> <span data-ttu-id="b6049-108">この例では、`COM1` です。</span><span class="sxs-lookup"><span data-stu-id="b6049-108">This example assumes it is `COM1`.</span></span>  
  
3.  <span data-ttu-id="b6049-109">`My.Computer.Ports.OpenSerialPort` メソッドを使用して、ポートへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="b6049-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="b6049-110">詳細については、「<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6049-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="b6049-111">`Try...Catch...Finally` ブロックを使用すると、アプリケーションが例外を生成した場合でも、シリアル ポートを閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="b6049-111">The `Try...Catch...Finally` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="b6049-112">シリアル ポートを操作するコードはすべて、このブロック内に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6049-112">All code that manipulates the serial port should appear within this block.</span></span>  
  
     <span data-ttu-id="b6049-113">[!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6049-113">[!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]</span></span>  
  
4.  <span data-ttu-id="b6049-114">利用可能な行がなくなるまでテキスト行を読み取るための `Do` ループを作成します。</span><span class="sxs-lookup"><span data-stu-id="b6049-114">Create a `Do` loop for reading lines of text until no more lines are available.</span></span>  
  
     <span data-ttu-id="b6049-115">[!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6049-115">[!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]</span></span>  
  
5.  <span data-ttu-id="b6049-116"><xref:System.IO.Ports.SerialPort.ReadLine%2A> メソッドを使用して、次に利用可能なテキスト行をシリアル ポートから読み取ります。</span><span class="sxs-lookup"><span data-stu-id="b6049-116">Use the <xref:System.IO.Ports.SerialPort.ReadLine%2A> method to read the next available line of text from the serial port.</span></span>  
  
     <span data-ttu-id="b6049-117">[!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6049-117">[!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]</span></span>  
  
6.  <span data-ttu-id="b6049-118">`If` ステートメントを使用して、<xref:System.IO.Ports.SerialPort.ReadLine%2A> メソッドが `Nothing` を返す (つまり、利用可能なテキストがこれ以上ない) かどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="b6049-118">Use an `If` statement to determine if the <xref:System.IO.Ports.SerialPort.ReadLine%2A> method returns `Nothing` (which means no more text is available).</span></span> <span data-ttu-id="b6049-119">`Nothing` を返した場合は、`Do` ループを終了します。</span><span class="sxs-lookup"><span data-stu-id="b6049-119">If it does return `Nothing`, exit the `Do` loop.</span></span>  
  
     <span data-ttu-id="b6049-120">[!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6049-120">[!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]</span></span>  
  
7.  <span data-ttu-id="b6049-121">`If` ステートメントに `Else` ブロックを追加して、文字列が実際に読み取られた場合のケースを処理します。</span><span class="sxs-lookup"><span data-stu-id="b6049-121">Add an `Else` block to the `If` statement to handle the case if the string is actually read.</span></span> <span data-ttu-id="b6049-122">このブロックによって、シリアル ポートからの文字列を戻り値の文字列に追加します。</span><span class="sxs-lookup"><span data-stu-id="b6049-122">The block appends the string from the serial port to the return string.</span></span>  
  
     <span data-ttu-id="b6049-123">[!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6049-123">[!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]</span></span>  
  
8.  <span data-ttu-id="b6049-124">文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="b6049-124">Return the string.</span></span>  
  
     <span data-ttu-id="b6049-125">[!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6049-125">[!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6049-126">例</span><span class="sxs-lookup"><span data-stu-id="b6049-126">Example</span></span>  
 <span data-ttu-id="b6049-127">[!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="b6049-127">[!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]</span></span>  
  
 <span data-ttu-id="b6049-128">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="b6049-128">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="b6049-129">コード スニペット ピッカーでは、これは **[接続とネットワーク]** にあります。</span><span class="sxs-lookup"><span data-stu-id="b6049-129">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="b6049-130">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b6049-130">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b6049-131">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b6049-131">Compiling the Code</span></span>  
 <span data-ttu-id="b6049-132">この例では、コンピューターが `COM1` を使用しているものと想定しています。</span><span class="sxs-lookup"><span data-stu-id="b6049-132">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b6049-133">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="b6049-133">Robust Programming</span></span>  
 <span data-ttu-id="b6049-134">この例では、コンピューターが `COM1` を使用しているものと想定しています。</span><span class="sxs-lookup"><span data-stu-id="b6049-134">This example assumes the computer is using `COM1`.</span></span> <span data-ttu-id="b6049-135">柔軟性を高めるためには、利用可能なポートの一覧から目的のシリアル ポートを選択できるようにコードを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b6049-135">For more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="b6049-136">詳しくは、「[方法: 利用可能なシリアル ポートを表示する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b6049-136">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="b6049-137">この例では、アプリケーションによってポートが閉じられ、タイムアウト例外がキャッチされるようにするために、`Try...Catch...Finally` ブロックを使用しています。</span><span class="sxs-lookup"><span data-stu-id="b6049-137">This example uses a `Try...Catch...Finally` block to make sure that the application closes the port and to catch any timeout exceptions.</span></span> <span data-ttu-id="b6049-138">詳しくは、「[Try...Catch...Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="b6049-138">For more information, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6049-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="b6049-139">See Also</span></span>  
 <span data-ttu-id="b6049-140"><xref:Microsoft.VisualBasic.Devices.Ports></span><span class="sxs-lookup"><span data-stu-id="b6049-140"><xref:Microsoft.VisualBasic.Devices.Ports></span></span>   
 <span data-ttu-id="b6049-141"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="b6049-141"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span></span>   
 <span data-ttu-id="b6049-142">[方法: シリアル ポートに接続されているモデムをダイヤルする](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="b6049-142">[How to: Dial Modems Attached to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md) </span></span>  
 <span data-ttu-id="b6049-143">[方法: シリアル ポートに文字列を送信する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="b6049-143">[How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md) </span></span>  
 [<span data-ttu-id="b6049-144">方法 : 利用可能なシリアル ポートを表示する</span><span class="sxs-lookup"><span data-stu-id="b6049-144">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

