---
title: "方法: 値を返さないプロシージャを呼び出す (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure calls [Visual Basic], returning values
- Visual Basic code, procedures
- procedures [Visual Basic], calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bbea50132d1110b38bf9b01397795a2cd51f86d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>方法: 値を返さないプロシージャを呼び出す (Visual Basic)
A`Sub`プロシージャが呼び出し元のコードに値を返しません。 これを明示的に呼び出すスタンドアロンの呼び出し元ステートメントを使用します。 単に式の中で名前を使用して呼び出すことはできません。  
  
### <a name="to-call-a-sub-procedure"></a>Sub プロシージャを呼び出しています  
  
1.  名前を指定、`Sub`プロシージャです。  
  
2.  プロシージャ名を引数リストを囲むかっこに従ってください。 引数がない場合は、かっこを省略することができます。 ただし、かっこを使用して、コードを読みやすくします。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 同じ順序で引数を指定する必要がありますする、`Sub`プロシージャが、対応するパラメーターを定義します。  
  
     次の例では、 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>アプリケーション ウィンドウにアクティブにします。 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>その唯一の引数として、ウィンドウのタイトルを使用します。 値を返さない呼び出しコードにします。 メモ帳のプロセスが実行されていない場合がスローされます、<xref:System.ArgumentException>です。 `Shell`プロシージャでは、アプリケーションは、指定されたパスに前提としています。  
  
     [!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A>  
 <xref:System.ArgumentException>  
 [手順](./index.md)  
 [Sub プロシージャ](./sub-procedures.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [方法 : プロシージャを作成する](./how-to-create-a-procedure.md)  
 [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)  
 [方法: Visual Basic では、イベント ハンドラーを呼び出します](./how-to-call-an-event-handler.md)
