---
title: "関数 &quot;&lt;procedurename&gt;&quot; すべてのコード パスで値が返されない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
dev_langs:
- VB
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: 12
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
ms.openlocfilehash: 288fdf7c4845b20283681d9eb3504ac314f1ddd2
ms.lasthandoff: 03/13/2017

---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a>関数 '&lt;procedurename&gt;' すべてのコード パスで値が返されない
関数 '\<procedurename >' すべてのコード パスで値を返しません。 'Return' ステートメントが不足していますか。  
  
 A`Function`手順では、値を返さないことをコードから少なくとも&1; つの可能なパスです。  
  
 値を返すことができます、`Function`次の方法のいずれかの手順。  
  
-   値を含む、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)します。  
  
-   値を代入します、`Function`プロシージャ名前を指定し、実行、`Exit Function`ステートメントです。  
  
-   値を代入します、`Function`プロシージャ名前を指定し、実行、`End Function`ステートメントです。  
  
 制御が移るかどうか`Exit Function`または`End Function`プロシージャ名に任意の値が割り当てられていないと、プロシージャは、戻り値のデータ型の既定値を返します。 詳細については、「動作」を参照してください[Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)します。  
  
 既定では、このメッセージは警告です。 警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。  
  
 **エラー ID:** BC42105  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   制御フローのロジックを確認し、すべてのステートメントが値を返す前に値を代入するかどうかを確認します。  
  
     常に使用する場合に、プロシージャからリターンごとに値を返すことを保証する方が簡単、`Return`ステートメントです。 この場合、最後のステートメントの前に`End Function`する必要があります、`Return`ステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [Function プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)   
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)   
 [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
