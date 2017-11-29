---
title: "プロパティ &#39;&lt;propertyname&gt;&#39; しません &#39; t のすべてのコード パスで値を返しません"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords: BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c9ef5b2ac62412f5684cbc78ab6bebf6bc7b6752
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a>プロパティ &#39;&lt;propertyname&gt;&#39; しません &#39; t のすべてのコード パスで値を返しません
プロパティ '\<propertyname >' は、すべてのコード パスで値を返しません。 この結果が使用されると、実行時に Null 参照例外が生じる可能性があります。  
  
 プロパティ`Get`手順では、値を返さないコードに少なくとも 1 つの可能なパスです。  
  
 プロパティから値を返すことができます`Get`次の方法のいずれかの手順。  
  
-   プロパティ名に値を代入し、実行、`Exit Property`ステートメントです。  
  
-   プロパティ名に値を代入し、実行、`End Get`ステートメントです。  
  
-   値を含む、 [Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md)です。  
  
 コントロールに渡します`Exit Property`または`End Get`プロパティ名の後に任意の値が割り当てられていないと、`Get`プロシージャ、プロパティのデータ型の既定値を返します。 詳細については、「動作」を参照してください[関数ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)です。  
  
 既定では、このメッセージは警告です。 警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。  
  
 **エラー ID:** BC42107  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   制御フローのロジックを確認し、戻り値の原因となるすべてのステートメントの前に値を代入するかどうかを確認します。  
  
     すべてを返すプロシージャが常に使用する場合に、値を返すことを保証しやすく、`Return`ステートメントです。 この場合、最後のステートメントの前に`End Get`する必要があります、`Return`ステートメントです。  
  
## <a name="see-also"></a>関連項目  
 [Property プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Get ステートメント](../../../visual-basic/language-reference/statements/get-statement.md)
