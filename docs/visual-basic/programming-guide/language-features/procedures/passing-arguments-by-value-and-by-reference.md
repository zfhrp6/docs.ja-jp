---
title: 引数の値渡しと参照渡し (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- ByRef keyword [Visual Basic], passing arguments by reference
- Visual Basic code, procedures
- passing arguments [Visual Basic], by value or by reference
- ByVal keyword [Visual Basic], passing arguments by value
- arguments [Visual Basic], passing by value or by reference
- argument passing [Visual Basic], by value or by reference
ms.assetid: fd8a9de6-7178-44d5-a9bf-458d4ad907c2
ms.openlocfilehash: 2d333bc873ba055d7a7b53c50fcfeec4cc0f9491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654178"
---
# <a name="passing-arguments-by-value-and-by-reference-visual-basic"></a>引数の値渡しと参照渡し (Visual Basic)
Visual basic では、プロシージャに引数を渡すことができます*値によって*または*参照によって*です。 これと呼ばれますが、*渡し*プロシージャが呼び出し元のコードで引数の基になるプログラミング要素を変更できるかどうかを判定します。 プロシージャ宣言では、各パラメーターの引き渡し方法を決定を指定して、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード。  
  
## <a name="distinctions"></a>相違点  
 プロシージャに引数を渡すときの相互作用をいくつかの違いに注意してください。  
  
-   基になるプログラミング要素が変更可能または変更不可能なのかどうか  
  
-   引数自体が変更可能または変更不可能なのかどうか  
  
-   値渡しまたは参照渡しの引数が渡されるかどうか  
  
-   引数のデータ型は、値型または参照型かどうか  
  
 詳細については、次を参照してください。[の相違点の間で変更可能なと変更できない引数](./differences-between-modifiable-and-nonmodifiable-arguments.md)と[の相違点の間で値と参照渡しによって引数の渡し](./differences-between-passing-an-argument-by-value-and-by-reference.md)です。  
  
## <a name="choice-of-passing-mechanism"></a>引き渡し方法の選択  
 各引数の慎重に引き渡し方法を選択してください。  
  
-   **保護**です。 引数を渡す方法を選択すると、最も重要な条件を変更する変数を呼び出すことの公開です。 引数を渡す場合の利点`ByRef`は、プロシージャがその引数を呼び出し元のコードに値を返すことができます。 引数を渡す場合の利点`ByVal`プロシージャによって変更されない変数を防ぐことができます。  
  
-   **パフォーマンス**です。 引き渡し方法が、コードのパフォーマンスに影響を与えることができますが、違いは通常意味ではありません。 1 つの例外は、渡された値の型`ByVal`です。 この場合、Visual Basic では、引数の内容が全体がコピーされます。 そのため、構造体などの大きな値型のだということを渡す方が効率的`ByRef`です。  
  
     参照型の場合は、データへのポインターのみ、コピーした (4 バイト 32 ビット プラットフォームでは、64 ビット プラットフォームでは 8 バイト) です。 そのため、型の引数を渡すことができます`String`または`Object`パフォーマンスに悪影響を与えない値。  
  
## <a name="determination-of-the-passing-mechanism"></a>引き渡し方法の決定  
 プロシージャ宣言では、各パラメーターの引き渡し方法を指定します。 呼び出し元のコードがオーバーライドすることはできません、`ByVal`メカニズムです。  
  
 パラメーターが宣言されている場合`ByRef`、呼び出し元のコードにするためのメカニズムを強制できます`ByVal`を呼び出しでは、かっこで囲み、引数名によってです。 詳細については、次を参照してください。[する方法: 引数を値渡しを強制](./how-to-force-an-argument-to-be-passed-by-value.md)です。  
  
 Visual Basic では既定では、引数の値渡しです。  
  
## <a name="when-to-pass-an-argument-by-value"></a>引数の値渡しする場合  
  
-   引数の基になる呼び出し元のコード要素が変更できない要素の場合は、対応するパラメーターを宣言[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)です。 変更不可能な要素の値は、コードでは変更されません。  
  
-   基になる要素は変更できますが、その値を変更できるようにする手順をしたくない場合、パラメーターを宣言`ByVal`です。 呼び出し元のコードだけでは、値渡し変更可能な要素の値を変更できます。  
  
## <a name="when-to-pass-an-argument-by-reference"></a>参照引数を渡す場合  
  
-   プロシージャに呼び出し元のコード内の基になる要素を変更する正規品である必要がある場合は、対応するパラメーターを宣言[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)です。  
  
-   正しいコードの実行は、呼び出し元のコード内の基になる要素を変更するプロシージャに依存している場合に、パラメーター宣言`ByRef`です。 値で渡す場合、または呼び出し元のコードをオーバーライドする場合、`ByRef`引数をかっこで囲んで、プロシージャの呼び出しが予期しない結果を生じる可能性があります。  
  
## <a name="example"></a>例  
  
### <a name="description"></a>説明  
 引数の値渡しと参照渡しする次の例を示しています。 プロシージャ`Calculate`両方を持つ、`ByVal`と`ByRef`パラメーター。 利率、指定された`rate`と合計金額、 `debt`、プロシージャのタスクはの新しい値を計算する`debt`の元の値を利率を適用した結果は`debt`します。 `debt`は、`ByRef`パラメーター、呼び出し元のコードに対応する引数の値で、新しい合計を反映`debt`です。 パラメーター`rate`は、`ByVal`パラメーターのため`Calculate`その値を変更しないでください。  
  
### <a name="code"></a>コード  
 [!code-vb[VbVbcnProcedures#74](./codesnippet/VisualBasic/passing-arguments-by-value-and-by-reference_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)  
 [方法: プロシージャ引数の値を変更する](./how-to-change-the-value-of-a-procedure-argument.md)  
 [方法: プロシージャ引数の値が変化しないようにする](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [方法: 引数の値渡しを強制する](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
