---
title: 省略可能なパラメーター型として使用されるジェネリック パラメーターは、クラスの制約がある型でなければなりません。
ms.date: 07/20/2015
f1_keywords:
- vbc32124
- bc32124
helpviewer_keywords:
- BC32124
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
ms.openlocfilehash: 7e2b59f758ef236717a912694576b514e2ae8a60
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590040"
---
# <a name="generic-parameters-used-as-optional-parameter-types-must-be-class-constrained"></a>省略可能なパラメーター型として使用されるジェネリック パラメーターは、クラスの制約がある型でなければなりません。
プロシージャは、参照型に固定されていない型パラメーターを使用する省略可能なパラメーターを指定して宣言されます。  
  
 常に省略可能な各パラメーターの既定値を指定する必要があります。 省略可能な値がある必要があります、パラメーターの場合は、参照型、 `Nothing`、これは任意の参照型の有効な値です。 ただし、パラメーターが値型である場合、その型が定義済みの Visual Basic では基本データ型である必要があります。 これは、ユーザー定義の構造体などの複合値型は有効な既定値があるないためです。  
  
 省略可能なパラメーターの型パラメーターを使用する場合、有効な既定値はありません値型の可能性を回避する参照型であることを保証する必要があります。 つまり、いずれかの型パラメーターを制約する必要があります、`Class`キーワードまたは特定のクラスの名前に置き換えます。  
  
 **エラー ID:** BC32124  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   型パラメーターを参照型のみを受け入れるように制約または省略可能なパラメーターを使用しないでください。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic におけるジェネリック型](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [型リスト](../../../visual-basic/language-reference/statements/type-list.md)  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
 [省略可能なパラメーター](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)  
 [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)
