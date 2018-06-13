---
title: '方法: プロシージャに対してパラメーターを定義する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
ms.openlocfilehash: b058f593b8672da449dac250947563c75c8386bf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651114"
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>方法: プロシージャに対してパラメーターを定義する (Visual Basic)
A*パラメーター*に呼び出したときに、プロシージャに値を渡すには、呼び出し元のコードを許可します。 プロシージャの各パラメーターを宣言すると、変数を宣言すると、その名前とデータ型を指定するのと同様にします。 また、渡す方法を指定するパラメーターは省略可能かどうか。  
  
 詳細については、次を参照してください。[プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)です。  
  
### <a name="to-define-a-procedure-parameter"></a>プロシージャ パラメーターを定義するには  
  
1.  プロシージャ宣言では、プロシージャのパラメーター リスト、コンマでその他のパラメーターから分離することをパラメーター名を追加します。  
  
2.  パラメーターのデータ型を決定します。  
  
3.  パラメーター名に続けて、`As`句をデータ型を指定します。  
  
4.  パラメーターの引き渡し方法を決定します。 通常、値は呼び出し元のコードを変更できるようにする手順をしない場合に、値でパラメーターを渡します。  
  
5.  パラメーター名の前に記述しなければ[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)引渡し方法を指定します。 詳細については、次を参照してください。[の相違点の間で値と参照渡しによって引数の渡し](./differences-between-passing-an-argument-by-value-and-by-reference.md)です。  
  
6.  パラメーターが省略可能な場合は、前に渡し[省略可能](../../../../visual-basic/language-reference/modifiers/optional.md)等号 (=) でパラメーターのデータ型に従います (`=`)、既定値は。  
  
     次の例の輪郭の定義、 `Sub` 3 つのパラメーターを持つプロシージャ。 最初の 2 つが必要と 3 つ目は省略可能です。 パラメーターの宣言は、パラメーター リストではコンマで区切られます。  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     最初のパラメーターを受け入れる、`customer`オブジェクト、および`updateCustomer`に渡された変数を直接更新できます`c`引数が渡されるため[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)です。 渡されるために、プロシージャが最後の 2 つの引数の値を変更できません[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)です。  
  
     呼び出し元のコードがの値を指定しないかどうか、`level`パラメーター、Visual Basic 設定が既定値は 0 にします。  
  
     型チェック スイッチの場合 ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`Off`、`As`パラメーターを定義するときに、句は省略可能です。 ただし、すべて 1 つのパラメーターで使用する場合、`As`句、それらのすべて使用する必要の。 場合は、型チェック スイッチ`On`、`As`句がパラメーター定義のそれぞれに必要です。  
  
     すべてのプログラミング要素のデータ型の指定と呼びます*厳密な型指定*です。 設定すると`Option Strict On`、Visual Basic では、厳密な型指定が適用されます。 これを強くお勧め、次の理由。  
  
    -   変数およびパラメーターについての IntelliSense サポートを使用できます。 これにより、コードに入力すると、そのプロパティおよびその他のメンバーを参照してください。  
  
    -   これにより、コンパイラが型チェックを実行できます。 これは、オーバーフローなどのエラーにより実行時に失敗するステートメントを検出するのに役立ちます。 それらをサポートしないオブジェクトに対するメソッドの呼び出しをキャッチします。  
  
    -   コードの実行を高速になります。 理由は、1 つがある場合、プログラミング要素のデータ型を指定しないと、Visual Basic コンパイラが割り当てる、`Object`型です。 コンパイル済みのコードは間を変換する必要があります`Object`およびその他のデータ型は、パフォーマンスが低下します。  
  
## <a name="see-also"></a>関連項目

 [手順](./index.md)  
 [Sub プロシージャ](./sub-procedures.md)  
 [Function プロシージャ](./function-procedures.md)  
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)  
 [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)  
 [再帰プロシージャ](./recursive-procedures.md)  
 [プロシージャのオーバーロード](./procedure-overloading.md)  
 [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [オブジェクト指向プログラミング (Visual Basic)](../../concepts/object-oriented-programming.md)  
