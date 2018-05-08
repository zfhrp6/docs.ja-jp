---
title: '方法: 変数内で複数の値を保持する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 783c75ed4577831b7ca444870c97063e8a057346
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>方法: 変数内で複数の値を保持する (Visual Basic)
変数を宣言する必要がある場合は、複数の値を保持する*複合データ型*です。  
  
 [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)構造体、配列、およびクラスが含まれます。 複合データ型の変数は、基本データ型とその他の複合型の組み合わせを保持できます。 構造体とクラスは、コードだけではなく、データを保持できます。  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a>変数に 1 つ以上の値を保持するには  
  
1.  変数を使用する複合データ型を確認します。  
  
2.  複合データ型が既に定義されていない場合、変数が使用できるように定義します。  
  
    -   含む構造体を定義、 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)です。  
  
    -   格納された配列を定義、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)です。  
  
    -   クラスを定義、[クラス ステートメント](../../../../visual-basic/language-reference/statements/class-statement.md)です。  
  
3.  使用して変数を宣言、`Dim`ステートメントです。  
  
4.  変数名に続けて、`As`句。  
  
5.  以下の`As`キーワード、適切な複合データ型の名前に置き換えます。  
  
## <a name="see-also"></a>関連項目  
 [データの種類](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [クラスとオブジェクト](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
