---
title: "関数 & #39;&lt;procedurename&gt;& #39; しません & #39; t のすべてのコード パスで値を返しません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords: BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5244d97a79f2450f44fe05f63510369914375912
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a>関数 & #39;&lt;procedurename&gt;& #39; しません & #39; t のすべてのコード パスで値を返しません
関数 '\<procedurename >' は、すべてのコード パスで値を返しません。 'Return' ステートメントが見当たりませんか。  
  
 A`Function`手順では、値を返さないコードに少なくとも 1 つの可能なパスです。  
  
 値を返すことができます、`Function`次の方法のいずれかの手順。  
  
-   値を含む、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)です。  
  
-   値を割り当てる、`Function`プロシージャ名前を指定しを実行して、`Exit Function`ステートメントです。  
  
-   値を割り当てる、`Function`プロシージャ名前を指定しを実行して、`End Function`ステートメントです。  
  
 コントロールに渡します`Exit Function`または`End Function`プロシージャの名前を任意の値が割り当てられていないと、プロシージャは、戻り値のデータ型の既定値を返します。 詳細については、「動作」を参照してください[関数ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)です。  
  
 既定では、このメッセージは警告です。 警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。  
  
 **エラー ID:** BC42105  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   制御フローのロジックを確認し、戻り値の原因となるすべてのステートメントの前に値を代入するかどうかを確認します。  
  
     すべてを返すプロシージャが常に使用する場合に、値を返すことを保証しやすく、`Return`ステートメントです。 この場合、最後のステートメントの前に`End Function`する必要があります、`Return`ステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [Function プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
 [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
