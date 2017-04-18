---
title: "プロパティ &quot;&lt;propertyname&gt;&quot; すべてのコード パスで値が返されない |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
dev_langs:
- VB
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 7
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
ms.openlocfilehash: e7c94d827761ad26d517b44a06734c5db4480a62
ms.lasthandoff: 03/13/2017

---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a>プロパティ '&lt;propertyname&gt;' すべてのコード パスで値が返されない
プロパティ '\<propertyname >' すべてのコード パスで値を返しません。 この結果が使用されると、実行時に Null 参照例外が生じる可能性があります。  
  
 プロパティ`Get`手順では、値を返さないことをコードから少なくとも&1; つの可能なパスです。  
  
 プロパティから値を返すことができます`Get`次の方法のいずれかの手順。  
  
-   プロパティ名に値を代入し、実行、`Exit Property`ステートメントです。  
  
-   プロパティ名に値を代入し、実行、`End Get`ステートメントです。  
  
-   値を含む、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)します。  
  
 制御が移るかどうか`Exit Property`または`End Get`プロパティ名に任意の値が割り当てられていないと、`Get`プロパティのデータ型の既定値を返します。 詳細については、「動作」を参照してください[Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)します。  
  
 既定では、このメッセージは警告です。 警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。  
  
 **エラー ID:** BC42107  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   制御フローのロジックを確認し、すべてのステートメントが値を返す前に値を代入するかどうかを確認します。  
  
     常に使用する場合に、プロシージャからリターンごとに値を返すことを保証する方が簡単、`Return`ステートメントです。 この場合、最後のステートメントの前に`End Get`する必要があります、`Return`ステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [プロパティ プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)   
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)   
 [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)
