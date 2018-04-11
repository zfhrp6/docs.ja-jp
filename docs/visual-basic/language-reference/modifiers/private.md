---
title: Private (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Private
helpviewer_keywords:
- Private keyword [Visual Basic]
- Private keyword [Visual Basic], syntax
ms.assetid: aba74a2e-5824-4613-bf63-b9ec7787f4e6
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07450c2a5443bf6bc147cad2cfc779072bfc363b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="private-visual-basic"></a>Private (Visual Basic)
1 つまたは複数の宣言されたプログラミング要素がすべて含まれている型内からなど、宣言のコンテキストからのみアクセスできることを指定します。  
  
## <a name="remarks"></a>コメント  
 プログラミング要素は、独自の機能または機密データを含む、通常する場合、できるだけ厳密にへのアクセスを制限します。 最大の制限は、モジュール、クラス、またはそれへのアクセスを定義する構造体のみを許可することで実現します。 この方法で要素へのアクセスを制限するために宣言できます`Private`です。  
  
## <a name="rules"></a>ルール  
  
-   **宣言コンテキスト。** `Private` は、モジュール レベルでのみ使用できます。 つまりの宣言コンテキスト、`Private`要素は、モジュール、クラス、または構造体にある必要があるあり、ソース ファイル、名前空間、インターフェイス、またはプロシージャにすることはできません。  
  
## <a name="behavior"></a>動作  
  
-   **アクセス レベル。** 宣言コンテキスト内のすべてのコードがアクセスできる、`Private`要素。 これには、入れ子になったクラスまたは列挙型の代入式などの包含の種類の中でコードが含まれます。 宣言コンテキスト以外のコードからもアクセスできない、`Private`要素。  
  
-   **アクセス修飾子。** アクセス レベルを指定するキーワードと呼ばれる*アクセス修飾子*です。 アクセス修飾子の比較を参照してください。 [Visual Basic でのレベルのアクセス](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
 `Private` 修飾子は、次のコンテキストで使用できます。  
  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Enum ステートメント](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [Public](../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)  
 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [手順](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [構造体](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [クラスとオブジェクト](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
