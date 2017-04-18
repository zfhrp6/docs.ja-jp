---
title: "変数 &quot;&lt;variablename&gt;&quot; 値が割り当てられる前に使われる |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
dev_langs:
- VB
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 10
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
ms.openlocfilehash: 7ad1f392fae2f90e366277b7b531d96011648866
ms.lasthandoff: 03/13/2017

---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a>変数 '&lt;variablename&gt;' 値が割り当てられる前に使われる
変数 '\<variablename >' 値が割り当てられる前に使用します。 結果として、実行時に null 参照の例外が発生する可能性があります。  
  
 アプリケーションには、少なくとも&1; つのパスをそのコードを任意の値が割り当てられる前に、変数を読み込むことがあります。  
  
 変数に値が割り当てられていない場合、変数はそのデータ型の既定値を保持します。 参照データ型では、その既定値は[Nothing](../../../visual-basic/language-reference/nothing.md)します。 値を持つ参照変数を読み取り`Nothing`が発生することができます、<xref:System.NullReferenceException>状況によって</xref:System.NullReferenceException>。  
  
 既定では、このメッセージは警告です。 警告を非表示や警告をエラーとして扱う方法の詳細については、次を参照してください。 [Visual Basic での警告の構成](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)します。  
  
 **エラー ID:** bc42104 を生成します  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   制御フローのロジックを確認し、変数が読み取られると、ステートメントに制御が渡される前に有効な値を持つかどうかを確認します。  
  
-   変数が常に有効な値を持つことを保証するために&1; つの方法では、その宣言の一部として初期化します。 「初期化」を参照してください[Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)します。  
  
## <a name="see-also"></a>関連項目  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [変数宣言](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [変数のトラブルシューティング](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
