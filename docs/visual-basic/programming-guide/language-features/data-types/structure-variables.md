---
title: 構造体の変数 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- structures [Visual Basic], variables
- structures [Visual Basic], structure variables
- variables [Visual Basic], structure variables
- structure variables [Visual Basic]
ms.assetid: 156872f8-aabc-4454-8e2d-f2253c3c13c9
ms.openlocfilehash: 0dad7bdcac5428753e252f3b26ca0a127c293a7f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648500"
---
# <a name="structure-variables-visual-basic"></a>構造体の変数 (Visual Basic)
構造体を作成した後は、その型としてプロシージャ レベルとモジュール レベル変数を宣言できます。 たとえば、コンピューター システムに関する情報を記録する構造体を作成できます。 次に例を示します。  
  
```  
Public Structure systemInfo  
    Public cPU As String  
    Public memory As Long  
    Public purchaseDate As Date  
End Structure  
```  
  
 その型の変数を宣言できます。 次の例を示します。  
  
```  
Dim mySystem, yourSystem As systemInfo  
```  
  
> [!NOTE]
>  クラスやモジュールで宣言された構造体を使用して、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)既定でパブリック アクセスです。 構造体をプライベートにする場合を使用して宣言を確認してください、[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワード。  
  
## <a name="access-to-structure-values"></a>構造体の値へのアクセス  
 割り当てるし、構造体変数の要素から値を取得、設定し、オブジェクトのプロパティの取得に使用すると同じ構文を使用します。 メンバー アクセス演算子を配置する (`.`) 構造体の変数名と要素名の間です。 次の例では、要素型として以前に宣言された変数の`systemInfo`します。  
  
```  
mySystem.cPU = "486"  
Dim tooOld As Boolean  
If yourSystem.purchaseDate < #1/1/1992# Then tooOld = True  
```  
  
## <a name="assigning-structure-variables"></a>構造体の変数を割り当てる  
 どちらも、同じ構造体型の場合、別に 1 つの変数を割り当てることができます。 これにより、1 つの構造体のすべての要素が、他の対応する要素にコピーします。 次の例を示します。  
  
```  
yourSystem = mySystem  
```  
  
 構造体の要素が、参照型など、 `String`、 `Object`、またはデータへのポインターの配列をコピーします。 前の例では場合、`systemInfo`のポインターが前の例をコピーしたが、オブジェクト変数が含まれていた`mySystem`に`yourSystem`、アクセスするときに、1 つの構造を使用して、オブジェクトのデータへの変更が有効にすると、を介して、他の構造体。  
  
## <a name="see-also"></a>関連項目  
 [データの種類](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [複合データ型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [構造体](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [方法 : 構造体を宣言する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [構造体とその他のプログラミング要素](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [構造体とクラス](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)
