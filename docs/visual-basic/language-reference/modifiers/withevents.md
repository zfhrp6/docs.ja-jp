---
title: "WithEvents (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
dev_langs:
- VB
helpviewer_keywords:
- WithEvents keyword
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
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
ms.openlocfilehash: 708cf6fec78faf2c7a5959a3a2694d237d728882
ms.lasthandoff: 03/13/2017

---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
1 つまたは複数の宣言されたメンバー変数がイベントを発生させるクラスのインスタンスを参照しているかを指定します。  
  
## <a name="remarks"></a>コメント  
 使用して変数を定義すると`WithEvents`、メソッドを使用して、変数のイベントを処理する宣言によって指定できます、`Handles`キーワードです。  
  
 使用する`WithEvents`クラスまたはモジュール レベルでのみです。 つまりの宣言コンテキスト、`WithEvents`変数がクラスまたはモジュールにする必要があり、ソース ファイル、名前空間、構造体、またはプロシージャにすることはできません。  
  
 使用することはできません`WithEvents`構造体のメンバーにします。  
  
 それぞれの変数を宣言することができます-配列ではない — と`WithEvents`です。  
  
## <a name="rules"></a>ルール  
  
-   **要素の型。** 宣言する必要があります`WithEvents`変数受け付けることができるため、オブジェクト変数をクラスのインスタンス。 ただし、そのままは宣言できません`Object`します。 それをイベントを発生させる特定のクラスとして宣言する必要があります。  
  
 `WithEvents`修飾子は、このコンテキストで使用できます: [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [ハンドル](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)   
 [イベント](../../../visual-basic/programming-guide/language-features/events/index.md)
