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
# <a name="how-to-start-an-application-and-send-it-keystrokes-visual-basic"></a>方法: アプリケーションを起動してキーストロークを送る (Visual Basic)
この例では、`Shell` 関数を使用して電卓アプリケーションを起動し、`My.Computer.Keyboard.SendKeys` メソッドを使用してキーストロークを送って、2 つの数値を乗算します。  
  
## <a name="example"></a>例  
 [!code-vb[VbVbalrMyComputer#25](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-start-an-application-and-send-it-keystrokes_1.vb)]  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 要求されたプロセス ID のアプリケーションが見つからない場合には、<xref:System.ArgumentException> 例外が発生します。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 `Shell` 関数の呼び出しには完全な信頼が必要です (<xref:System.Security.SecurityException> クラス)。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Devices.Keyboard.SendKeys%2A>   
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>   
 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>

