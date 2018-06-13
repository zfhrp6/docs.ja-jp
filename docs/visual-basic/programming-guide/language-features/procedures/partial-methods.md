---
title: 部分メソッド (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.PartialMethod
- PartialMethod
helpviewer_keywords:
- custom logic into code [Visual Basic]
- partial methods [Visual Basic]
- partial [Visual Basic], methods [Visual Basic]
- methods [Visual Basic], partial methods
- inserting custom logic into code
ms.assetid: 74b3368b-b348-44a0-a326-7d7dc646f4e9
ms.openlocfilehash: a1708c1d953a60429c1bd87fd858da5c50a3e759
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651597"
---
# <a name="partial-methods-visual-basic"></a>部分メソッド (Visual Basic)
部分メソッドでは、開発者はカスタム ロジックをコードに挿入を有効にします。 通常、コードは、デザイナーで生成されたクラスの一部です。 部分メソッドはコード ジェネレーターによって作成される部分クラスで定義され、何かが変更されたことを通知によく使用されます。 開発者は、変更に応じて、カスタム動作を指定できます。  
  
 コード ジェネレーターのデザイナーは、メソッドのシグネチャのみと 1 つまたは複数のメソッドの呼び出しを定義します。 開発者は、生成されたコードの動作をカスタマイズする場合は、メソッドの実装を提供し、できます。 実装を指定しない場合、メソッドの呼び出しは、追加のパフォーマンスのオーバーヘッドなしでその結果、コンパイラによって削除されます。  
  
## <a name="declaration"></a>宣言  
 キーワードを配置することによって、生成されたコードは部分メソッドの定義をマーク`Partial`シグネチャ行の開始時にします。  
  
```vb  
Partial Private Sub QuantityChanged()  
End Sub  
```  
  
 定義には、次の条件を満たす必要があります。  
  
-   メソッドである必要があります、`Sub`ではなく、`Function`です。  
  
-   メソッドの本文は空のままにする必要があります。  
  
-   アクセス修飾子がある必要があります`Private`です。  
  
## <a name="implementation"></a>実装  
 実装では、主に、部分メソッドの本体に入力します。 実装は、定義から別個の部分クラスでは、通常れ、生成されたコードを拡張する必要が開発者によって書き込まれます。  
  
```vb  
Private Sub QuantityChanged()  
'    Code for executing the desired action.  
End Sub  
```  
  
 前の例が、宣言内の署名を正確に複製がバリエーションが可能です。 具体的には、その他の修飾子を追加できるように`Overloads`または`Overrides`です。 1 つだけ`Overrides`修飾子を使用します。 メソッドの修飾子の詳細については、次を参照してください。 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)です。  
  
## <a name="use"></a>使用  
 同じように呼び出します、他の部分メソッドを呼び出す`Sub`プロシージャです。 メソッドが実装されている場合、引数が評価され、メソッドの本体が実行されます。 ただし、部分メソッドの実装が省略可能なことに注意してください。 メソッドが実装されていない場合それへの呼び出しも何も起こりません、およびメソッドに引数として渡された式は評価されません。  
  
## <a name="example"></a>例  
 Product.Designer.vb をという名前のファイル、定義、`Product`を持つクラス、`Quantity`プロパティです。  
  
 [!code-vb[VbVbalrPartialMeths#4](./codesnippet/VisualBasic/partial-methods_1.vb)]  
  
 実装を提供 Product.vb をという名前のファイル、`QuantityChanged`です。  
  
 [!code-vb[VbVbalrPartialMeths#5](./codesnippet/VisualBasic/partial-methods_2.vb)]  
  
 最後に、プロジェクトの Main メソッドで次のように宣言します。、`Product`インスタンスとの初期値を提供、`Quantity`プロパティです。  
  
 [!code-vb[VbVbalrPartialMeths#6](./codesnippet/VisualBasic/partial-methods_3.vb)]  
  
 このメッセージが表示されるメッセージ ボックスが表示されます。  
  
 `Quantity was changed to 100`  
  
## <a name="see-also"></a>関連項目  
 [Sub ステートメント](../../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Sub プロシージャ](./sub-procedures.md)  
 [省略可能なパラメーター](./optional-parameters.md)  
 [Partial](../../../../visual-basic/language-reference/modifiers/partial.md)  
 [LINQ to SQL でのコード生成](../../../../framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [部分メソッドによるビジネス ロジックの追加](../../../../framework/data/adonet/sql/linq/adding-business-logic-by-using-partial-methods.md)
