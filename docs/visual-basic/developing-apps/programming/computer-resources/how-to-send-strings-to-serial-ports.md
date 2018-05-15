---
title: '方法 : Visual Basic でシリアル ポートに文字列を送信する'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d796f2d581188fd3753bf3d18b04b2fbeb901945
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="6d3cf-102">方法 : Visual Basic でシリアル ポートに文字列を送信する</span><span class="sxs-lookup"><span data-stu-id="6d3cf-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="6d3cf-103">このトピックでは、`My.Computer.Ports` を使用して、Visual Basic でコンピューターのシリアルポートに文字列を送信する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="6d3cf-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in Visual Basic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d3cf-104">例</span><span class="sxs-lookup"><span data-stu-id="6d3cf-104">Example</span></span>  
 <span data-ttu-id="6d3cf-105">この例では、COM1 シリアル ポートに文字列を送信します。</span><span class="sxs-lookup"><span data-stu-id="6d3cf-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="6d3cf-106">コンピューターによっては、別のシリアル ポートを使用する必要が生じる場合があります。</span><span class="sxs-lookup"><span data-stu-id="6d3cf-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="6d3cf-107">`My.Computer.Ports.OpenSerialPort` メソッドを使用して、ポートへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="6d3cf-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="6d3cf-108">詳細については、「<xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d3cf-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="6d3cf-109">`Using` ブロックを使用すると、アプリケーションが例外を生成した場合でも、シリアル ポートを閉じることができます。</span><span class="sxs-lookup"><span data-stu-id="6d3cf-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="6d3cf-110">シリアル ポートを操作するコードはすべて、このブロックまたは `Try...Catch...Finally` ブロック内に記述する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d3cf-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="6d3cf-111"><xref:System.IO.Ports.SerialPort.WriteLine%2A> メソッドで、データをシリアル ポートに送信しています。</span><span class="sxs-lookup"><span data-stu-id="6d3cf-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6d3cf-112">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="6d3cf-112">Compiling the Code</span></span>  
  
-   <span data-ttu-id="6d3cf-113">この例では、コンピューターが `COM1` を使用しているものと想定しています。</span><span class="sxs-lookup"><span data-stu-id="6d3cf-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6d3cf-114">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="6d3cf-114">Robust Programming</span></span>  
 <span data-ttu-id="6d3cf-115">この例では、コンピューターが `COM1` を使用しているものと想定しています。実際に作成するコードでは、柔軟性を高めるために、利用可能なポートの一覧から目的のシリアル ポートを選択できるようにすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="6d3cf-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="6d3cf-116">詳しくは、「[方法: 利用可能なシリアル ポートを表示する](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="6d3cf-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="6d3cf-117">この例では、アプリケーションが例外をスローした場合でもポートを閉じられるよう、`Using` ブロックを使用しています。</span><span class="sxs-lookup"><span data-stu-id="6d3cf-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="6d3cf-118">詳細については、「[Using ステートメント](../../../../visual-basic/language-reference/statements/using-statement.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d3cf-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3cf-119">参照</span><span class="sxs-lookup"><span data-stu-id="6d3cf-119">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [<span data-ttu-id="6d3cf-120">方法 : シリアル ポートに接続されているモデムをダイヤルする</span><span class="sxs-lookup"><span data-stu-id="6d3cf-120">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [<span data-ttu-id="6d3cf-121">方法 : 利用可能なシリアル ポートを表示する</span><span class="sxs-lookup"><span data-stu-id="6d3cf-121">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
