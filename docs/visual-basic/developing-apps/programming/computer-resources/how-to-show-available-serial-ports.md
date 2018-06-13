---
title: '方法 : Visual Basic で利用可能なシリアル ポートを表示する'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: c13682ddca69d782ea519e0df703c211df8d12c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586726"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="934ca-102">方法 : Visual Basic で利用可能なシリアル ポートを表示する</span><span class="sxs-lookup"><span data-stu-id="934ca-102">How to: Show Available Serial Ports in Visual Basic</span></span>
<span data-ttu-id="934ca-103">このトピックでは、`My.Computer.Ports` を使用して、コンピューターで利用可能なシリアルポートを Visual Basic で表示する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="934ca-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="934ca-104">使用するポートをユーザーが選択可能とするために、シリアル ポートの名前を <xref:System.Windows.Forms.ListBox> コントロールに格納します。</span><span class="sxs-lookup"><span data-stu-id="934ca-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="934ca-105">例</span><span class="sxs-lookup"><span data-stu-id="934ca-105">Example</span></span>  
 <span data-ttu-id="934ca-106">次の例では、`My.Computer.Ports.SerialPortNames` プロパティが返す文字列のすべてについてループします。</span><span class="sxs-lookup"><span data-stu-id="934ca-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="934ca-107">これらの文字列は、コンピューターで利用可能なシリアル ポートの名前です。</span><span class="sxs-lookup"><span data-stu-id="934ca-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="934ca-108">通常、利用可能なポートの一覧から、アプリケーションで使用するシリアル ポートをユーザーが選択します。</span><span class="sxs-lookup"><span data-stu-id="934ca-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="934ca-109">この例では、シリアル ポート名は <xref:System.Windows.Forms.ListBox> コントロールに格納されます。</span><span class="sxs-lookup"><span data-stu-id="934ca-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="934ca-110">詳細については、「[ListBox コントロール](../../../../framework/winforms/controls/listbox-control-windows-forms.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="934ca-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]  
  
 <span data-ttu-id="934ca-111">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="934ca-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="934ca-112">コード スニペット ピッカーでは、これは **[接続とネットワーク]** にあります。</span><span class="sxs-lookup"><span data-stu-id="934ca-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="934ca-113">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="934ca-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="934ca-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="934ca-114">Compiling the Code</span></span>  
 <span data-ttu-id="934ca-115">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="934ca-115">This example requires:</span></span>  
  
-   <span data-ttu-id="934ca-116">System.Windows.Forms.dll へのプロジェクト参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="934ca-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
-   <span data-ttu-id="934ca-117"><xref:System.Windows.Forms> 名前空間のメンバーへのアクセス許可。</span><span class="sxs-lookup"><span data-stu-id="934ca-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="934ca-118">コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="934ca-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="934ca-119">詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="934ca-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
-   <span data-ttu-id="934ca-120">`ListBox1` という名前の <xref:System.Windows.Forms.ListBox> コントロールを持つフォーム。</span><span class="sxs-lookup"><span data-stu-id="934ca-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="934ca-121">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="934ca-121">Robust Programming</span></span>  
 <span data-ttu-id="934ca-122">利用可能なシリアル ポートの名前を表示するために、<xref:System.Windows.Forms.ListBox> コントロールを使用する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="934ca-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="934ca-123">代わりに、<xref:System.Windows.Forms.ComboBox> やその他のコントロールを使用できます。</span><span class="sxs-lookup"><span data-stu-id="934ca-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="934ca-124">ユーザーからの応答が不要なアプリケーションの場合、<xref:System.Windows.Forms.TextBox> コントロールを使用して情報を表示できます。</span><span class="sxs-lookup"><span data-stu-id="934ca-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="934ca-125">Windows 98 の実行時には、`My.Computer.Ports.SerialPortNames` が返すポート名が正しくない場合があります。</span><span class="sxs-lookup"><span data-stu-id="934ca-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="934ca-126">アプリケーション エラーを防ぐには、ポート名を使用してポートを開くときに、`Try...Catch...Finally` ステートメントや `Using` ステートメントなどの例外処理を使用します。</span><span class="sxs-lookup"><span data-stu-id="934ca-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934ca-127">参照</span><span class="sxs-lookup"><span data-stu-id="934ca-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [<span data-ttu-id="934ca-128">方法 : シリアル ポートに接続されているモデムをダイヤルする</span><span class="sxs-lookup"><span data-stu-id="934ca-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [<span data-ttu-id="934ca-129">方法 : シリアル ポートに文字列を送信する</span><span class="sxs-lookup"><span data-stu-id="934ca-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [<span data-ttu-id="934ca-130">方法 : シリアル ポートから文字列を受信する</span><span class="sxs-lookup"><span data-stu-id="934ca-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
