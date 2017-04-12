---
title: "方法: 新しい変数 (Visual Basic) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Dim statement
- variables [Visual Basic], creating
ms.assetid: 35300be3-77b0-4bef-a156-034d3cdedde0
caps.latest.revision: 29
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
ms.openlocfilehash: 2856fe19ddc48a14385aaae7b1c331fcb96c0554
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-a-new-variable-visual-basic"></a>方法: 新しい変数を作成する (Visual Basic)
変数を作成する、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)します。  
  
### <a name="to-create-a-new-variable"></a>新しい変数を作成するには  
  
1.  変数を宣言、`Dim`ステートメントです。  
  
    ```  
  
    Dim newCustomer  
    ```  
  
2.  変数の特性の仕様を含める[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)、[静的](../../../../visual-basic/language-reference/modifiers/static.md)、[シャドウ](../../../../visual-basic/language-reference/modifiers/shadows.md)、または[WithEvents](../../../../visual-basic/language-reference/modifiers/withevents.md)します。 詳細については、次を参照してください。[宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)します。  
  
    ```  
    Public Static newCustomer  
    ```  
  
     必要としない、`Dim`の宣言でその他のキーワードを使用する場合は、キーワード。  
  
3.  従う必要があります変数の名前の仕様に従う[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]規則と規約。 詳細については、次を参照してください。[宣言された要素の名前](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)します。  
  
    ```  
    Public Static newCustomer  
    ```  
  
4.  名に続けて、[として](../../../../visual-basic/language-reference/statements/as-clause.md)句、変数のデータ型を指定します。  
  
    ```  
    Public Static newCustomer As Customer  
    ```  
  
     既定値を使用して、データ型を指定しない場合:`Object`です。  
  
5.  次の`As`等号 (=) を含む句 (`=`) 変数の初期値を等号 (=) に従います。  
  
     [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]実行するたびに、指定した値を変数に代入、`Dim`ステートメントです。 初期値を指定しなかった場合[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]を含むコードが最初に入ると、変数のデータ型の既定の初期値を割り当てる、`Dim`ステートメントです。  
  
     含めることによって、クラスのインスタンスを作成するには、変数が参照型である場合、 [New 演算子](../../../../visual-basic/language-reference/operators/new-operator.md)のキーワード、`As`句。 使用しない場合`New`、変数の初期値は[Nothing](../../../../visual-basic/language-reference/nothing.md)します。  
  
    ```  
    Public Static newCustomer As New Customer  
    ```  
  
## <a name="see-also"></a>関連項目  
 [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)   
 [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [宣言された要素名](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [宣言された要素の特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)   
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [ステートメント](../../../../visual-basic/language-reference/statements/index.md)   
 [ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
