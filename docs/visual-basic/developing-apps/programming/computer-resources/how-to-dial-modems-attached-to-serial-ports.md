---
title: "方法 : Visual Basic で、シリアル ポートに接続されているモデムをダイヤルする"
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
- modems, dialing
- serial ports, dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
caps.latest.revision: 19
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
ms.openlocfilehash: 0daaf35cdebac3d69ddc536124d4c86b96955b11
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a><span data-ttu-id="6735a-102">方法 : Visual Basic で、シリアル ポートに接続されているモデムをダイヤルする</span><span class="sxs-lookup"><span data-stu-id="6735a-102">How to: Dial Modems Attached to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="6735a-103">このトピックでは、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] で `My.Computer.Ports` を使用してモデムをダイヤルする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6735a-103">This topic describes how to use `My.Computer.Ports` to dial a modem in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="6735a-104">通常、モデムはコンピューターのいずれかのシリアル ポートに接続されています。</span><span class="sxs-lookup"><span data-stu-id="6735a-104">Typically, the modem is connected to one of the serial ports on the computer.</span></span> <span data-ttu-id="6735a-105">アプリケーションがモデムとやり取りするには、適切なシリアル ポートにコマンドを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6735a-105">For your application to communicate with the modem, it must send commands to the appropriate serial port.</span></span>  
  
### <a name="to-dial-a-modem"></a><span data-ttu-id="6735a-106">モデムをダイヤルするには</span><span class="sxs-lookup"><span data-stu-id="6735a-106">To dial a modem</span></span>  
  
1.  <span data-ttu-id="6735a-107">モデムが接続されているシリアル ポートを確認します。</span><span class="sxs-lookup"><span data-stu-id="6735a-107">Determine which serial port the modem is connected to.</span></span> <span data-ttu-id="6735a-108">この例では、モデムが COM1 に接続されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="6735a-108">This example assumes the modem is on COM1.</span></span>  
  
2.  <span data-ttu-id="6735a-109">`My.Computer.Ports.OpenSerialPort` メソッドを使用して、ポートへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="6735a-109">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="6735a-110">詳細については、「<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6735a-110">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
     <span data-ttu-id="6735a-111">`Using` ブロックを使用すると、アプリケーションが例外を生成した場合でも、シリアル ポートを閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="6735a-111">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="6735a-112">シリアル ポートを操作するコードはすべて、このブロックまたは `Try...Catch...Finally` ブロック内に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6735a-112">All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.</span></span>  
  
     <span data-ttu-id="6735a-113">[!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="6735a-113">[!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]</span></span>  
  
3.  <span data-ttu-id="6735a-114">コンピューターがモデムからの伝送を受け取る準備ができたことを示しよう `DtrEnable` プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="6735a-114">Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.</span></span>  
  
     <span data-ttu-id="6735a-115">[!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="6735a-115">[!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]</span></span>  
  
4.  <span data-ttu-id="6735a-116"><xref:System.IO.Ports.SerialPort.Write%2A> メソッドを使用して、ダイヤル コマンドと電話番号をシリアル ポート経由でモデムに送信します。</span><span class="sxs-lookup"><span data-stu-id="6735a-116">Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.</span></span>  
  
     <span data-ttu-id="6735a-117">[!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="6735a-117">[!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="6735a-118">例</span><span class="sxs-lookup"><span data-stu-id="6735a-118">Example</span></span>  
 <span data-ttu-id="6735a-119">[!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="6735a-119">[!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]</span></span>  
  
 <span data-ttu-id="6735a-120">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="6735a-120">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="6735a-121">コード スニペット ピッカーでは、これは **[接続とネットワーク]** にあります。</span><span class="sxs-lookup"><span data-stu-id="6735a-121">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="6735a-122">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6735a-122">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6735a-123">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6735a-123">Compiling the Code</span></span>  
 <span data-ttu-id="6735a-124">この例では、<xref:System?displayProperty=fullName> 名前空間への参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="6735a-124">This example requires a reference to the <xref:System?displayProperty=fullName> namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6735a-125">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="6735a-125">Robust Programming</span></span>  
 <span data-ttu-id="6735a-126">この例では、モデムが COM1 に接続されていることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="6735a-126">This example assumes the modem is connected to COM1.</span></span> <span data-ttu-id="6735a-127">コードによって、利用可能なシリアル ポートの一覧から、目的のポートをユーザーが選択できるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6735a-127">We recommend that your code allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="6735a-128">詳細については、「[方法: 利用可能なシリアル ポートを表示する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6735a-128">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="6735a-129">この例では、アプリケーションが例外をスローした場合でもポートを閉じられるよう、`Using` ブロックを使用しています。</span><span class="sxs-lookup"><span data-stu-id="6735a-129">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="6735a-130">詳細については、「[sing ステートメント](../../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6735a-130">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
 <span data-ttu-id="6735a-131">この例では、アプリケーションは、モデムをダイヤルした後でシリアル ポートを切断しています。</span><span class="sxs-lookup"><span data-stu-id="6735a-131">In this example, the application disconnects the serial port after it dials the modem.</span></span> <span data-ttu-id="6735a-132">実際には、モデムとの間でデータの転送が必要となります。</span><span class="sxs-lookup"><span data-stu-id="6735a-132">Realistically, you will want to transfer data to and from the modem.</span></span> <span data-ttu-id="6735a-133">詳細については、「[方法: シリアル ポートから文字列を受信する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6735a-133">For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6735a-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="6735a-134">See Also</span></span>  
 <span data-ttu-id="6735a-135"><xref:Microsoft.VisualBasic.Devices.Ports></span><span class="sxs-lookup"><span data-stu-id="6735a-135"><xref:Microsoft.VisualBasic.Devices.Ports></span></span>   
 <span data-ttu-id="6735a-136"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="6735a-136"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span></span>   
 <span data-ttu-id="6735a-137">[方法 : シリアル ポートに文字列を送信する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="6735a-137">[How to: Send Strings to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md) </span></span>  
 <span data-ttu-id="6735a-138">[方法: シリアル ポートから文字列を受信する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="6735a-138">[How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md) </span></span>  
 [<span data-ttu-id="6735a-139">方法 : 利用可能なシリアル ポートを表示する</span><span class="sxs-lookup"><span data-stu-id="6735a-139">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

