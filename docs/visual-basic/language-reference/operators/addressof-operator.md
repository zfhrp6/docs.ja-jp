---
title: "AddressOf 演算子 (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- AddressOf
- vb.AddressOf
dev_langs:
- VB
helpviewer_keywords:
- AddressOf operator
- addresses, passing to API procedures
ms.assetid: 8105a59d-60d8-4ab5-b221-5899cdfacbf4
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 04a7c5be9b890faea561c28715093a271cf9eaa8
ms.lasthandoff: 03/13/2017

---
# <a name="addressof-operator-visual-basic"></a>AddressOf 演算子 (Visual Basic)
特定の手順を参照するプロシージャ デリゲート インスタンスを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
  
AddressOf procedurename  
```  
  
## <a name="parts"></a>指定項目  
 `procedurename`  
 必須です。 新しく作成されたプロシージャ デリゲートによって参照されるプロシージャを指定します。  
  
## <a name="remarks"></a>コメント  
 `AddressOf`演算子で指定された関数を指す関数デリゲートを作成する`procedurename`です。 ときに、指定したプロシージャは、インスタンス メソッド、関数デリゲートがインスタンスとメソッドの両方を指してです。 次に、関数デリゲートが呼び出されたときに、指定したインスタンスの指定したメソッドが呼び出されます。  
  
 `AddressOf`デリゲート コンス トラクターのオペランドと演算子を使用できますか、コンパイラによって、デリゲートの型を決定するコンテキストで使用できます。  
  
## <a name="example"></a>例  
 この例では、`AddressOf`を処理するデリゲートを指定する演算子、`Click`ボタンのイベントです。  
  
 [!code-vb[VbVbalrDelegates&#8;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_1.vb)]  
  
## <a name="example"></a>例  
 次の例では、`AddressOf`スレッドのスタートアップ関数を指定する演算子です。  
  
 [!code-vb[VbVbalrDelegates&#9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/addressof-operator_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [デリゲート](../../../visual-basic/programming-guide/language-features/delegates/index.md)
