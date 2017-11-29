---
title: "方法: オブジェクト変数がインスタンスを参照しないようにする (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b33aef06300bf35b7138ec5b40747532a77140a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a>方法: オブジェクト変数がインスタンスを参照しないようにする (Visual Basic)
設定するすべてのオブジェクトのインスタンスからオブジェクト変数の関連付けを解除することができます[Nothing](../../../../visual-basic/language-reference/nothing.md)です。  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a>すべてのオブジェクトのインスタンスからオブジェクト変数の関連付けを解除するには  
  
-   変数を設定`Nothing`代入ステートメントでします。  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 設定されているオブジェクト変数のメンバーにアクセスしようとすると、コード`Nothing`、<xref:System.NullReferenceException>に発生します。 オブジェクト変数を設定する場合`Nothing`多くの場合、またはのメンバー アクセスで囲むことをお勧め、変数が初期化されていませんが可能ですが場合、は、`Try...Catch...Finally`ブロックします。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 機密情報や機密データを格納するオブジェクトをオブジェクト変数を使用する場合、変数に設定することができます`Nothing`ときアクティブに処理するいないとそれらのオブジェクトのいずれか。 これにより、データにアクセスする悪意のあるコードが発生する可能性が減少します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.NullReferenceException>  
 [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [オブジェクト変数の代入](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Nothing](../../../../visual-basic/language-reference/nothing.md)  
 [Try...Catch...Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [例外のトラブルシューティング : System.NullReferenceException](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
