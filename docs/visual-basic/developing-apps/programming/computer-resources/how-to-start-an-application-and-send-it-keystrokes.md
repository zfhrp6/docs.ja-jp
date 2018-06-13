---
title: '方法: アプリケーションを起動してキーストロークを送る (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
ms.openlocfilehash: 716c88153ad01c7b225f31948c8aaaa2694dc512
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582149"
---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="08313-102">方法: アプリケーションを起動してキーストロークを送る (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08313-102">How to: Start an Application and Send it Keystrokes (Visual Basic)</span></span>
<span data-ttu-id="08313-103">この例では、`Shell` 関数を使用して電卓アプリケーションを起動し、`My.Computer.Keyboard.SendKeys` メソッドを使用してキーストロークを送って、2 つの数値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="08313-103">This example uses the `Shell` function to start the calculator application and then multiplies two numbers by sending keystrokes using the `My.Computer.Keyboard.SendKeys` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08313-104">例</span><span class="sxs-lookup"><span data-stu-id="08313-104">Example</span></span>  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="08313-105">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="08313-105">Robust Programming</span></span>  
 <span data-ttu-id="08313-106">要求されたプロセス ID のアプリケーションが見つからない場合には、<xref:System.ArgumentException> 例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="08313-106">A <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="08313-107">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="08313-107">.NET Framework Security</span></span>  
 <span data-ttu-id="08313-108">`Shell` 関数の呼び出しには完全な信頼が必要です (<xref:System.Security.SecurityException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="08313-108">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08313-109">参照</span><span class="sxs-lookup"><span data-stu-id="08313-109">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>
