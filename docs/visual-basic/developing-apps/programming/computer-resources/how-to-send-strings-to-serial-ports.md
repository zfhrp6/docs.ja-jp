---
title: "方法 : Visual Basic でシリアル ポートに文字列を送信する"
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
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: 13
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
ms.openlocfilehash: 602b249d01252bbb1853ed02d9af86697d54b0a5
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="55084-102">方法 : Visual Basic でシリアル ポートに文字列を送信する</span><span class="sxs-lookup"><span data-stu-id="55084-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="55084-103">このトピックでは、`My.Computer.Ports` を使用して、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] でコンピュータのシリアルポートに文字列を送信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="55084-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="55084-104">例</span><span class="sxs-lookup"><span data-stu-id="55084-104">Example</span></span>  
 <span data-ttu-id="55084-105">この例では、COM1 シリアル ポートに文字列を送信します。</span><span class="sxs-lookup"><span data-stu-id="55084-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="55084-106">コンピューターによっては、別のシリアル ポートを使用する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="55084-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="55084-107">`My.Computer.Ports.OpenSerialPort` メソッドを使用して、ポートへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="55084-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="55084-108">詳細については、「<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55084-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="55084-109">`Using` ブロックを使用すると、アプリケーションが例外を生成した場合でも、シリアル ポートを閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="55084-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="55084-110">シリアル ポートを操作するコードはすべて、このブロックまたは `Try...Catch...Finally` ブロック内に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="55084-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="55084-111"><xref:System.IO.Ports.SerialPort.WriteLine%2A> メソッドで、データをシリアル ポートに送信しています。</span><span class="sxs-lookup"><span data-stu-id="55084-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 <span data-ttu-id="55084-112">[!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="55084-112">[!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="55084-113">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="55084-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="55084-114">この例では、コンピューターが `COM1` を使用しているものと想定しています。</span><span class="sxs-lookup"><span data-stu-id="55084-114">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="55084-115">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="55084-115">Robust Programming</span></span>  
 <span data-ttu-id="55084-116">この例では、コンピューターが `COM1` を使用しているものと想定しています。実際に作成するコードでは、柔軟性を高めるために、利用可能なポートの一覧から目的のシリアル ポートを選択できるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="55084-116">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="55084-117">詳細については、「[方法: 利用可能なシリアル ポートを表示する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55084-117">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="55084-118">この例では、アプリケーションが例外をスローした場合でもポートを閉じられるよう、`Using` ブロックを使用しています。</span><span class="sxs-lookup"><span data-stu-id="55084-118">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="55084-119">詳細については、「[Using ステートメント](../../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55084-119">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55084-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="55084-120">See Also</span></span>  
 <span data-ttu-id="55084-121"><xref:Microsoft.VisualBasic.Devices.Ports></span><span class="sxs-lookup"><span data-stu-id="55084-121"><xref:Microsoft.VisualBasic.Devices.Ports></span></span>   
 <span data-ttu-id="55084-122"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="55084-122"><xref:System.IO.Ports.SerialPort?displayProperty=fullName></span></span>   
 <span data-ttu-id="55084-123">[方法: シリアル ポートに接続されているモデムをダイヤルする](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md) </span><span class="sxs-lookup"><span data-stu-id="55084-123">[How to: Dial Modems Attached to Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md) </span></span>  
 [<span data-ttu-id="55084-124">方法 : 利用可能なシリアル ポートを表示する</span><span class="sxs-lookup"><span data-stu-id="55084-124">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)

