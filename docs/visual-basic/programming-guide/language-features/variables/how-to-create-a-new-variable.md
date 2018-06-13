---
title: '方法: 新しい変数を作成する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Dim statement [Visual Basic]
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
ms.openlocfilehash: f2e6a97e78bc42ebea9519eb0aa4411e9aec24cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651545"
---
# <a name="how-to-create-a-new-variable-visual-basic"></a>方法: 新しい変数を作成する (Visual Basic)
変数を作成する、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)です。  
  
### <a name="to-create-a-new-variable"></a>新しい変数を作成するには  
  
1.  変数を宣言、`Dim`ステートメントです。  
  
    ```  
    Dim newCustomer  
    ```  
  
2.  など、変数の特性の仕様を含める[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)、[静的](../../../../visual-basic/language-reference/modifiers/static.md)、 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)、または[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)です。 詳細については、次を参照してください。[宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)です。  
  
    ```  
    Public Static newCustomer  
    ```  
  
     必要としない、`Dim`の宣言でその他のキーワードを使用する場合は、キーワード。  
  
3.  変数の名前は、Visual Basic の規則と規則に従う必要がありますの仕様に従ってください。 詳細については、次を参照してください。[宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)です。  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  名に続けて、[として](../../../../visual-basic/language-reference/statements/as-clause.md)句を変数のデータ型を指定します。  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     既定値を使用して、データ型を指定しない場合:`Object`です。  
  
5.  以下の`As`等号 (=) を含む句 (`=`) し、変数の初期値を等号 (=) に従います。  
  
     実行するたびに Visual Basic に変数に指定された値が割り当てられます、`Dim`ステートメントです。 Visual Basic を含むコードを最初に切り替わったときに、変数のデータ型の既定の初期値が割り当てられます、初期値を指定しない場合、`Dim`ステートメントです。  
  
     含めることによって、このクラスのインスタンスを作成するには、変数が参照型である場合、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)キーワード、`As`句。 使用しない場合`New`、変数の初期値は[Nothing](../../../../visual-basic/language-reference/nothing.md)です。  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>関連項目  
 [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [ステートメント](../../../../visual-basic/language-reference/statements/index.md)  
 [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
