---
title: 変数&#39; &lt;variablename&gt; &#39;は、値が割り当てられる前に使用
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: d314f952bd6e11adaac642ba63ed292f48cda805
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596920"
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a>変数&#39; &lt;variablename&gt; &#39;は、値が割り当てられる前に使用
変数 '\<variablename >' は、値が割り当てられる前に使用します。 結果として、実行時に null 参照の例外が発生する可能性があります。  
  
 アプリケーションが任意の値を割り当てる前に、変数を読み取るをコードに少なくとも 1 つの可能なパスがあります。  
  
 変数に値が割り当てられていない場合、変数はそのデータ型の既定値を保持します。 参照データ型では、その既定値は[Nothing](../../../visual-basic/language-reference/nothing.md)です。 値が `Nothing` である参照変数を読み取ると、状況によって <xref:System.NullReferenceException> が発生する可能性があります。  
  
 既定では、このメッセージは警告です。 警告を非表示や、警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](/visualstudio/ide/configuring-warnings-in-visual-basic)です。  
  
 **エラー ID:** bc42104 を生成します  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   制御フローのロジックを確認し、によって読み取られる任意のステートメントに制御が渡される前に、変数が有効な値を持つかどうかを確認します。  
  
-   変数が常に有効な値を持つことを保証するために 1 つの方法では、その宣言の一部として初期化します。 「初期化」を参照してください[Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)です。  
  
## <a name="see-also"></a>関連項目  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [変数のトラブルシューティング](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
