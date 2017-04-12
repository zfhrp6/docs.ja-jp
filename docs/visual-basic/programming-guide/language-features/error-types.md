---
title: "エラーの種類 (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors, Visual Basic
- run-time errors, types of errors
- syntax errors, Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d48756b74baf757f043e68124d8b65c2f613e595
ms.lasthandoff: 03/13/2017

---
# <a name="error-types-visual-basic"></a>エラーの種類 (Visual Basic)
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]、エラー (とも呼ばれます*例外*) は&3; つのカテゴリに分類します。 構文エラー、実行時エラー、および論理エラーです。  
  
## <a name="syntax-errors"></a>構文エラー  
 *構文エラー*はコードを記述するときに表示されます。 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]入力して、コードを確認、**コード エディター**ウィンドウなど、word のスペルが間違ってまたは言語要素を正しく使用して、操作を誤った場合、アラートが生成されます。 構文エラーは、エラーの最も一般的な種類です。 簡単に修正できますコーディング環境で発生するとすぐにします。  
  
> [!NOTE]
>  `Option Explicit`ステートメントが構文エラーを回避する&1; つのことを意味します。 アプリケーションで使用するすべての変数を事前に宣言するように強制します。 したがって、コードでそれらの変数を使用している場合、入力ミスがすぐに検出され、修正することができます。  
  
## <a name="run-time-errors"></a>実行時エラー  
 *実行時エラー*をコンパイルして、コードを実行するまでは表示されません。 これらには、構文エラーがないのに実行できない点で、正しいように表示されるコードが含まれます。 たとえば、ファイルを開くコード行を正しく記述できます。 ファイルが壊れている場合は、アプリケーションを実行できませんが、`Open`関数、およびその実行を停止します。 問題のあるコードの書き直しを再コンパイルし、再実行することで、ほとんどの実行時エラーを修正できます。  
  
## <a name="logic-errors"></a>論理エラー  
 *論理エラー*は、アプリケーションが使用すると表示されます。 ユーザー操作に応じてほとんどの多くの場合望ましくないか予期しない結果が表示されます。 たとえば、入力の間違いキーまたはなどの外的要因があります、アプリケーションで予測されるパラメーター内での作業を停止するなったりします。 論理エラーは、通常ではないため常に明確ではないを解決する最も困難な型です。  
  
## <a name="see-also"></a>関連項目  
 [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)   
 [デバッガーの基本事項](https://docs.microsoft.com/visualstudio/debugger/debugger-basics)
