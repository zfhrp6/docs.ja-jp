---
title: "方法: アプリケーションを起動してキーストロークを送る (Visual Basic)"
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
- keystrokes, sending
- Shell command example [Visual Basic]
- processes, starting and sending keystrokes
- SendKeys.SendWait examples
ms.assetid: f1303184-fce4-44fb-88b4-aac5f42d5d77
caps.latest.revision: 15
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
ms.openlocfilehash: 142db417b6b61724ad80bd3f8e5083dd420b3aeb
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a><span data-ttu-id="fbad9-102">方法: アプリケーションを起動してキーストロークを送る (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fbad9-102">How to: Start an Application and Send it Keystrokes (Visual Basic)</span></span>
<span data-ttu-id="fbad9-103">この例では、`Shell` 関数を使用して電卓アプリケーションを起動し、`My.Computer.Keyboard.SendKeys` メソッドを使用してキーストロークを送って、2 つの数値を乗算します。</span><span class="sxs-lookup"><span data-stu-id="fbad9-103">This example uses the `Shell` function to start the calculator application and then multiplies two numbers by sending keystrokes using the `My.Computer.Keyboard.SendKeys` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fbad9-104">例</span><span class="sxs-lookup"><span data-stu-id="fbad9-104">Example</span></span>  
 <span data-ttu-id="fbad9-105">[!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fbad9-105">[!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fbad9-106">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="fbad9-106">Robust Programming</span></span>  
 <span data-ttu-id="fbad9-107">要求されたプロセス ID のアプリケーションが見つからない場合には、<xref:System.ArgumentException> 例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="fbad9-107">A <xref:System.ArgumentException> exception is raised if an application with the requested process identifier cannot be found.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="fbad9-108">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="fbad9-108">.NET Framework Security</span></span>  
 <span data-ttu-id="fbad9-109">`Shell` 関数の呼び出しには完全な信頼が必要です (<xref:System.Security.SecurityException> クラス)。</span><span class="sxs-lookup"><span data-stu-id="fbad9-109">The call to the `Shell` function requires full trust (<xref:System.Security.SecurityException> class).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbad9-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="fbad9-110">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>   
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>   
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>

