---
title: "方法: プロシージャ (Visual Basic) のパラメーターを定義する |Microsoft ドキュメント"
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
- procedure parameters, defining data types for
- procedures, parameters
- procedures, defining
- Visual Basic code, procedures
- procedure parameters, defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: 15
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
ms.openlocfilehash: 9fb9ad244499039c1768ff97f071168e0a0842e4
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>方法: プロシージャに対してパラメーターを定義する (Visual Basic)
A*パラメーター*呼び出し元コードを呼び出すときに、プロシージャに値を渡すことができます。 手順については、各パラメーター、変数を宣言すると、その名前とデータ型を指定するのと同じ方法を宣言します。 また引き渡し方法を指定するパラメーターは省略可能かどうか。  
  
 詳細については、次を参照してください。[プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)します。  
  
### <a name="to-define-a-procedure-parameter"></a>プロシージャのパラメーターを定義するには  
  
1.  プロシージャの宣言では、プロシージャのパラメーター リストをコンマでの他のパラメーターから分離するパラメーター名を追加します。  
  
2.  パラメーターのデータ型を決定します。  
  
3.  パラメーター名に続けて、`As`句データ型を指定します。  
  
4.  パラメーターの引き渡し方法を決定します。 通常を呼び出し元のコードにはその値を変更できるようにする手順をしない場合に、値でパラメーターを渡します。  
  
5.  パラメーター名の前に[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)引き渡し方法を指定します。 詳細については、次を参照してください。[の相違点の間の値と参照渡しによって引数の渡し](./differences-between-passing-an-argument-by-value-and-by-reference.md)します。  
  
6.  渡しのパラメーターが省略可能な場合は、前に[オプション](../../../../visual-basic/language-reference/modifiers/optional.md)は等号でパラメーターのデータ型に従います (`=`) および既定値です。  
  
     次の例のアウトラインを定義する、 `Sub`&3; つのパラメーターを持つプロシージャ。 最初の&2; つは要求され、3 つ目は省略可能。 パラメーターの宣言は、パラメーター リストにコンマで区切られます。  
  
     [!code-vb[VbVbcnProcedures #&33;](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     最初のパラメーターを受け入れる、`customer`オブジェクト、および`updateCustomer`に渡された変数を直接更新`c`引数が渡されるため[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)します。 渡されるために、プロシージャが最後の&2; つの引数の値を変更できません[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)します。  
  
     呼び出し元のコードがの値を指定しないかどうか、`level`パラメーター、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]既定値は 0 に設定します。  
  
     型チェック スイッチの場合 ([Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) は`Off`、`As`パラメーターを定義するときに、句は省略可能です。 ただし、1 つのパラメーターを使用している場合、`As`句はすべての使用する必要です。 型チェック スイッチが場合`On`、`As`句はすべてのパラメーターの定義の必須です。  
  
     プログラミングのすべての要素のデータ型の指定と呼ばれます*厳密な型指定*します。 設定すると`Option Strict On`、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]厳密な型指定が適用されます。 これが強く推奨します、次の理由。  
  
    -   これにより、IntelliSense で変数とパラメーターをサポートできます。 これにより、コードに入力すると、そのプロパティおよびその他のメンバーを参照してください。  
  
    -   これにより、コンパイラが型チェックを実行できます。 これは、実行時のオーバーフローなどのエラーにより失敗するステートメントを検出するのに役立ちます。 サポートしていないオブジェクトに対するメソッドの呼び出しをキャッチします。  
  
    -   コードの実行を高速になります。 これを&1; つの理由は、プログラミングの要素のデータ型が指定されていない場合、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]コンパイラが割り当てる、`Object`型です。 コンパイル済みのコードは、間を変換する必要があります`Object`およびその他のデータ型は、パフォーマンスが低下します。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)   
 [Sub プロシージャ](./sub-procedures.md)   
 [Function プロシージャ](./function-procedures.md)   
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)   
 [値渡しと参照による引数渡し](./passing-arguments-by-value-and-by-reference.md)   
 [再帰プロシージャ](./recursive-procedures.md)   
 [プロシージャのオーバー ロード](./procedure-overloading.md)   
 [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [オブジェクト指向プログラミング](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
