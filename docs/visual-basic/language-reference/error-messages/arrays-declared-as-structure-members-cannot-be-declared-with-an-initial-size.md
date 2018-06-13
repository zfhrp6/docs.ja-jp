---
title: 構造体メンバーとして宣言された配列を初期サイズで宣言することはできません。
ms.date: 07/20/2015
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords:
- BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
ms.openlocfilehash: 0a7424e5dbfadd78c4071ba5b76086b7f6c9b94a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585854"
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a>構造体メンバーとして宣言された配列を初期サイズで宣言することはできません。
構造体の配列は、初期サイズで宣言されます。 どの構造体の要素を初期化することはできず、初期化の 1 つの形式は、配列のサイズを宣言することです。  
  
 **エラー ID:** BC31043  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
1.  動的 (初期サイズがありません)、構造内の配列を定義します。  
  
2.  動的配列の次元を変更できる配列の特定のサイズを必要とする場合、 [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)コードが実行されています。 次に例を示します。  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a>関連項目  
 [配列](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [方法 : 構造体を宣言する](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
