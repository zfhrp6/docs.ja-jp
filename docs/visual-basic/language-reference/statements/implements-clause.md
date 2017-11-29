---
title: "Implements 句 (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73f66eda29e37fda15b4c838da5a0458684131da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="implements-clause-visual-basic"></a>Implements 句 (Visual Basic)
クラスまたは構造体のメンバーがインターフェイスで定義されているメンバーの実装を提供していることを示します。  
  
## <a name="remarks"></a>コメント  
`Implements`キーワードと同じではない、 [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)です。 使用する、`Implements`クラスまたは構造体は、1 つまたは複数のインターフェイスを実装して、各メンバーを使用することを指定するステートメント、`Implements`どのインターフェイスとメンバーを指定するキーワードを実装します。

クラスまたは構造体、インターフェイスを実装する場合は含める必要があります、`Implements`ステートメントの直後に、[クラス ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)または[Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)、およびすべてのメンバーを実装する必要がありますインターフェイスによって定義されます。

## <a name="reimplementation"></a>再実装が必要  
派生クラスでは、基本クラスが実装済みインターフェイスのメンバーを再実装できます。 これは、次の点で基底クラスのメンバーをオーバーライドすると異なります。

- 基底クラスのメンバーがする必要がない[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)実装するためにします。
- 別の名前を持つメンバーを再実装できます。

`Implements`キーワードは、次のコンテキストで使用できます。
- [Event ステートメント](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>関連項目  
 [Implements ステートメント](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Class ステートメント](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Structure ステートメント](../../../visual-basic/language-reference/statements/structure-statement.md)
