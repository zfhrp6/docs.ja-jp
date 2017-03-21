---
title: "上位変換 (Visual Basic) を入力 |Microsoft ドキュメント"
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
- declared elements, scope
- visibility, declared elements
- Partial keyword, unexpected results with type promotion
- scope, declared elements
- scope, Visual Basic
- type promotion
- declared elements, visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
caps.latest.revision: 17
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
ms.openlocfilehash: d732e765fc28eaedc0deab477dbf9955a40e97c9
ms.lasthandoff: 03/13/2017

---
# <a name="type-promotion-visual-basic"></a>型の上位変換 (Visual Basic)
モジュールでのプログラミング要素を宣言するときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]モジュールを含む名前空間には、そのスコープを昇格させます。 これと呼ばれます。*の上位変換の入力*します。  
  
 次の例では、モジュールのスケルトンの定義とモジュールの&2; つのメンバーを示します。  
  
 [!code-vb[VbVbalrDeclaredElements&#1;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 内で`projModule`プログラミング、モジュール レベルで宣言されている要素に昇格`projNamespace`します。 前の例で`basicEnum`と`innerClass`昇格されますが、`numberSub`モジュール レベルで宣言されていないためにではありません。  
  
## <a name="effect-of-type-promotion"></a>型の上位変換の効果  
 型の上位変換の効果は、修飾文字列がモジュール名を含める必要がないことです。 次の例では、前の例では、手順&2; つの呼び出しをでいます。  
  
 [!code-vb[VbVbalrDeclaredElements&#2;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 前の例では、最初の呼び出しは、完全な修飾文字列を使用します。 ただし、これはないために必要な型の上位変換のためです。 もう&1; つを呼び出すもアクセス モジュールのメンバーを含めずに`projModule`修飾文字列。  
  
## <a name="defeat-of-type-promotion"></a>型の上位変換の無効化  
 名前空間には、モジュール メンバーと同じ名前のメンバーが既に、型の上位変換は、モジュール メンバーの無効化です。 次の例では、列挙型と同じ名前空間内のモジュールのスケルトンの定義を示します。  
  
 [!code-vb[VbVbalrDeclaredElements&#3;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 前の例で[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]クラスに昇格できません`abc`に`thisNameSpace`名前空間レベルで同じ名前の列挙型が既に存在します。 アクセスする`abcSub`、完全修飾文字列を使用する必要があります`thisNamespace.thisModule.abc.abcSub`します。 ただし、クラス`xyz`はまだ昇格し、アクセスできる`xyzSub`短い修飾文字列`thisNamespace.xyz.xyzSub`します。  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>部分型の型の上位変換の無効化  
 クラスまたは構造体、モジュールの中で使用する場合、[部分](../../../../visual-basic/language-reference/modifiers/partial.md)キーワード、型の上位変換が自動的に無効化にそのクラスまたは構造体、名前空間には同じ名前のメンバーであるかどうか。 モジュールの他の要素は現在の型の上位変換します。  
  
 **結果。** 部分的な定義の型の上位変換の無効化には、予期しない結果とさらにコンパイル エラーがあります。 次の例では、うちの&1; つは、モジュール内のクラスのスケルトンの部分的な定義を示します。  
  
 [!code-vb[VbVbalrDeclaredElements&4;](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 前の例では、開発者は、コンパイラの&2; つの部分定義をマージする`sampleClass`です。 ただし、コンパイラが部分定義内のプロモーションを考慮されません`sampleModule`します。 その結果、2 つの個別のクラスをコンパイルしようという名前を`sampleClass`ですが、パスのさまざまな修飾します。  
  
 コンパイラは、完全修飾されたパスがまったく同じ場合にのみ、部分定義をマージします。  
  
## <a name="recommendations"></a>推奨事項  
 次の推奨事項は、プログラミング習慣を表します。  
  
-   **一意の名前。** プログラミングの要素の名前付けを完全に制御がある場合は常には一意の名前をすべての場所で使用します。 同じ名前では、余分に修飾が必要し、するコードが読みにくくします。 微妙なエラーと予期しない結果になることもします。  
  
-   **完全に修飾されます。** モジュールと同じ名前空間の他の要素を使用している、最も安全な方法が、常にすべてのプログラミング要素を完全に修飾を使用します。 型の上位変換がモジュール メンバーの無効化すると、そのメンバーを完全修飾せず、別のプログラミング要素をアクセスしてしまう可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [Module ステートメント](../../../../visual-basic/language-reference/statements/module-statement.md)   
 [Namespace ステートメント](../../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [部分的です](../../../../visual-basic/language-reference/modifiers/partial.md)   
 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)   
 [方法: 変数のスコープを制御します。](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)   
 [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
