---
title: 型の上位変換 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- Partial keyword [Visual Basic], unexpected results with type promotion
- scope [Visual Basic], declared elements
- scope [Visual Basic], Visual Basic
- type promotion
- declared elements [Visual Basic], visibility
ms.assetid: 035eeb15-e4c5-4288-ab3c-6bd5d22f7051
ms.openlocfilehash: 104fa906fecc5a5bb8704fe3ab839f9f200cf73b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649426"
---
# <a name="type-promotion-visual-basic"></a>型の上位変換 (Visual Basic)
モジュール内のプログラミング要素を宣言する場合、Visual Basic は、モジュールを含む名前空間には、そのスコープを昇格します。 これは呼ば*プロモーションを入力*です。  
  
 次の例では、モジュールのスケルトン定義し、そのモジュールの 2 つのメンバーを示します。  
  
 [!code-vb[VbVbalrDeclaredElements#1](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_1.vb)]  
  
 内で`projModule`プログラミング、モジュール レベルで宣言された要素に昇格`projNamespace`です。 前の例で`basicEnum`と`innerClass`昇格されますが、`numberSub`モジュール レベルで宣言されていないためにではありません。  
  
## <a name="effect-of-type-promotion"></a>型の昇格の効果  
 型の昇格の効果は、修飾文字列は、モジュール名を含めるには必要ありません。 次の例では、前の例で、プロシージャに 2 つの呼び出しをさせます。  
  
 [!code-vb[VbVbalrDeclaredElements#2](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_2.vb)]  
  
 前の例では、最初の呼び出しは、完全修飾文字列を使用します。 ただし、これはいないために必要な型の昇格のためです。 2 番目せずに呼び出すもアクセス モジュールのメンバーを含む`projModule`修飾文字列にします。  
  
## <a name="defeat-of-type-promotion"></a>型の上位変換の無効化  
 名前空間は、モジュール メンバーと同じ名前のメンバーを既に持っている場合の型の昇格がそのモジュール メンバーの無効化します。 次の例は、列挙体と同じ名前空間内のモジュールのスケルトン定義を示しています。  
  
 [!code-vb[VbVbalrDeclaredElements#3](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_3.vb)]  
  
 前の例では、Visual Basic がクラスを昇格できません`abc`に`thisNameSpace`名前空間レベルで同じ名前を持つ列挙型が既に存在します。 アクセスする`abcSub`、完全修飾文字列を使用する必要があります`thisNamespace.thisModule.abc.abcSub`です。 ただし、クラス`xyz`がまだ昇格し、アクセスできる`xyzSub`短い修飾文字列`thisNamespace.xyz.xyzSub`です。  
  
### <a name="defeat-of-type-promotion-for-partial-types"></a>部分型の型の上位変換の無効化  
 クラスまたはモジュール内の構造体で使用する場合、[部分](../../../../visual-basic/language-reference/modifiers/partial.md)キーワード、型の上位変換が自動的に無効化のクラスまたは構造体、名前空間を持つ同じ名前のメンバーであるかどうか。 モジュールの他の要素は、型の昇格も対象です。  
  
 **影響します。** 部分定義の型の上位変換の無効化には、予期しない結果とコンパイラ エラーも可能性があります。 次の例では、モジュール内の 1 つは、クラスのスケルトンの部分定義を示します。  
  
 [!code-vb[VbVbalrDeclaredElements#4](../../../../visual-basic/programming-guide/language-features/declared-elements/codesnippet/VisualBasic/type-promotion_4.vb)]  
  
 前の例では、開発者は、コンパイラの 2 つの部分定義をマージする`sampleClass`です。 ただし、コンパイラが部分定義内の昇格を考慮されません`sampleModule`です。 2 つの独立したクラスをコンパイルしようとしてという名前をその結果、`sampleClass`ですが、パスのさまざまな修飾します。  
  
 コンパイラは、完全修飾されたパスがまったく同じ場合にのみ、部分定義をマージします。  
  
## <a name="recommendations"></a>推奨事項  
 次の推奨事項は、適切なプログラミング手法を表します。  
  
-   **一意の名前。** プログラミング要素の名前付けを完全に制御がある場合は、は常に一意の名前をあらゆる場所で使用することをお勧めします。 同じ名前では、余分な修飾子が必要し、読みにくく、コードを行うことができます。 微妙なエラーと予期しない結果になることができますも。  
  
-   **完全に修飾します。** モジュールと同じ名前空間の他の要素を使用している、最も安全な手法はすべてのプログラミング要素の完全修飾を常に使用することです。 型の昇格がモジュール メンバーの無効化、そのメンバーを完全に指定していない場合は、誤って別のプログラミング要素にアクセスするでした。  
  
## <a name="see-also"></a>関連項目  
 [Module ステートメント](../../../../visual-basic/language-reference/statements/module-statement.md)  
 [Namespace ステートメント](../../../../visual-basic/language-reference/statements/namespace-statement.md)  
 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [方法: 変数のスコープを制御する](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [宣言された要素の参照](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
