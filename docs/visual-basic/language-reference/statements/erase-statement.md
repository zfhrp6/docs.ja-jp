---
title: Erase ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 317e2a7dc5facb08388f3a3e635734e4daed5eac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601794"
---
# <a name="erase-statement-visual-basic"></a>Erase ステートメント (Visual Basic)
配列変数を解放し、その要素に使用するメモリの割り当てを解除するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a>指定項目  
 `arraylist`  
 必須。 消去する配列変数の一覧です。 複数の変数を指定するときは、コンマで区切ります。  
  
## <a name="remarks"></a>コメント  
 `Erase`ステートメントはプロシージャ レベルでのみ表示できます。 これは、プロシージャ内でクラスまたはモジュール レベルではなくは配列を解放することを意味します。  
  
 `Erase`ステートメントは、割り当てることに相当`Nothing`を各配列変数にします。  
  
## <a name="example"></a>例  
 次の例では、 `Erase` 2 つの配列を消去して自らのメモリを解放するステートメント (1,000 と 100 の記憶域要素では、それぞれ)。 `ReDim`ステートメントは、3 次元の配列に、新しい配列のインスタンスが割り当てられます。  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Nothing](../../../visual-basic/language-reference/nothing.md)  
 [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)
