---
title: "方法: 値 (Visual Basic) を返さないプロシージャを呼び出す |Microsoft ドキュメント"
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
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: 17
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 17b2b902f3ee6ab79b2614b7742aa08fefab2420
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a>方法: 値を返さないプロシージャを呼び出す (Visual Basic)
A`Sub`プロシージャが呼び出し元のコードに値を返しません。 これを明示的に呼び出すスタンドアロンの呼び出し元ステートメントを使用します。 単に式の中で名前を使用して呼び出すことはできません。  
  
### <a name="to-call-a-sub-procedure"></a>Sub プロシージャを呼び出す  
  
1.  名前を指定、`Sub`プロシージャです。  
  
2.  次のプロシージャ名の引数リストを囲むかっこを使用します。 引数がない場合は、かっこを省略することができます。 ただし、かっこを使用して、コードを読みやすくします。  
  
3.  コンマで区切り、かっこで囲まれた引数のリストに、引数を配置します。 同じ順序で引数を指定する必要があります`Sub`プロシージャは、対応するパラメーターを定義します。  
  
     次の例では、 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>アプリケーション ウィンドウにアクティブにします</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>。 <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>単一の引数として、ウィンドウのタイトルを取得します。</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> 呼び出し元のコードに値を返すことはできません。 例では、スロー <xref:System.ArgumentException>。</xref:System.ArgumentException>でメモ帳のプロセスが実行されていない場合 `Shell`プロシージャでは、アプリケーションは、指定されたパスに前提としています。  
  
     [!code-vb[VbVbalrCatRef&#11;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.Interaction.Shell%2A></xref:Microsoft.VisualBasic.Interaction.Shell%2A>   
 <xref:System.ArgumentException></xref:System.ArgumentException>   
 [手順](./index.md)   
 [Sub プロシージャ](./sub-procedures.md)   
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)   
 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)   
 [方法: プロシージャを作成します。](./how-to-create-a-procedure.md)   
 [方法: 値を返すプロシージャを呼び出す](./how-to-call-a-procedure-that-returns-a-value.md)   
 [方法: Visual Basic でイベント ハンドラーを呼び出す](./how-to-call-an-event-handler.md)
