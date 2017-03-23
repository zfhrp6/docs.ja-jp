---
title: "文字データ型 (Visual Basic) |Microsoft ドキュメント"
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
- data types [Visual Basic], character
- String data type, character data types
- character data types [Visual Basic]
- Char data type, character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
caps.latest.revision: 23
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 7ce600fe188c94593e4c07e37883ca11f90d9ae5
ms.lasthandoff: 03/13/2017

---
# <a name="character-data-types-visual-basic"></a>文字データ型 (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供*文字データ型*文字や表示可能な文字を処理します。 Unicode 文字を扱う、どちらも、`Char`が単一の文字を保持して`String`不特定数文字にはが含まれています。  
  
 サイド バイ サイドの比較を表示するテーブルの[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]データ型を参照してください[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)します。  
  
## <a name="char-type"></a>Char 型  
 `Char`データ型は、1 つの&2; バイト (16 ビット) Unicode 文字。 変数は、常に正確に&1; つの文字を保存する場合のように宣言`Char`します。 例:  
  
 [!code-vb[VbVbalrCharTypes&#1;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_1.vb)]  
  
 使用可能な各値、`Char`または`String`変数は、*コード ポイントが*、または Unicode 文字セット内の文字コード。 Unicode 文字には、基本的な ASCII 文字セット、さまざまなその他のアルファベット文字、アクセント記号、通貨記号、分数、分音文字、および数学と技術的な記号が含まれます。  
  
> [!NOTE]
>  Unicode 文字セットは、コード ポイント D800 ~ DFFF (55551 を通じて 55296) の*サロゲート ペア*、2 つの 16 ビット値が 1 つのコード ポイントを表す必要があります。 A`Char`変数は、サロゲート ペアを保持できません、`String`は、2 つの位置を使用して、そのような組み合わせを保持します。  
  
 詳細については、次を参照してください。 [Char データ型](../../../../visual-basic/language-reference/data-types/char-data-type.md)します。  
  
## <a name="string-type"></a>文字列型  
 `String`データ型は、0 個以上の&2; バイト (16 ビット) の Unicode 文字のシーケンス。 変数が、不特定数の文字を含んでいる可能性がある場合として宣言`String`します。 例:  
  
 [!code-vb[VbVbalrCharTypes&#2;](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/character-data-types_2.vb)]  
  
 詳細については、次を参照してください。[文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)します。  
  
## <a name="see-also"></a>関連項目  
 [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)   
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Visual Basic における型変換](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
