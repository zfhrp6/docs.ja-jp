---
title: Erase ステートメント (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a2b439cf5ad04d59cea59bb21d345d0057b322
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="erase-statement-visual-basic"></a>Erase ステートメント (Visual Basic)
配列変数を解放し、その要素に使用するメモリの割り当てを解除するために使用します。  
  
## <a name="syntax"></a>構文  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a>指定項目  
 `arraylist`  
 必須です。 消去する配列変数の一覧です。 複数の変数を指定するときは、コンマで区切ります。  
  
## <a name="remarks"></a>コメント  
 `Erase`ステートメントはプロシージャ レベルでのみ表示できます。 これは、プロシージャ内でクラスまたはモジュール レベルではなくは配列を解放することを意味します。  
  
 `Erase`ステートメントは、割り当てることに相当`Nothing`を各配列変数にします。  
  
## <a name="example"></a>例  
 次の例では、 `Erase` 2 つの配列を消去して自らのメモリを解放するステートメント (1,000 と 100 の記憶域要素では、それぞれ)。 `ReDim`ステートメントは、3 次元の配列に、新しい配列のインスタンスが割り当てられます。  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Nothing](../../../visual-basic/language-reference/nothing.md)  
 [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)
