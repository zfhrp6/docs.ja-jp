---
title: 変数 &#39;&lt;variablename&gt;&#39; は、値が割り当てられる前に使用
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 201667c250e15bb9af73e64e2d8c924c1952d1be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a>変数 &#39;&lt;variablename&gt;&#39; は、値が割り当てられる前に使用
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
