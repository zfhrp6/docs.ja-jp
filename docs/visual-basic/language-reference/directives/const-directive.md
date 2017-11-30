---
title: "#<a name=\"const-directive\"></a>#Const ディレクティブ"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#Const
- '#vb.Const'
- '#Const'
helpviewer_keywords:
- '#Const directive'
- conditional compilation [Visual Basic], directives
- Const directive (#Const)
- Visual Basic compiler, compiler directives
- constants [Visual Basic], Const directive
- constants [Visual Basic], declaring
- Const statement [Visual Basic], directive (#Const)
- 'declaring constants [Visual Basic], #const directive'
ms.assetid: 707669e5-23f9-4f17-8622-a0d534429386
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a6e162b01dc5c99fb7708337d259f9e66ddd6b64
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="const-directive"></a>#Const ディレクティブ
Visual basic の場合は、条件付きコンパイラ定数を定義します。  
  
## <a name="syntax"></a>構文  
  
```  
#Const constname = expression  
```  
  
## <a name="parts"></a>指定項目  
 `constname`  
 必須です。 定義されている定数の名前です。  
  
 `expression`  
 必須です。 リテラルやその他の条件付きコンパイラ定数を除くいずれかまたはすべて算術演算または論理演算子を含む任意の組み合わせ`Is`です。  
  
## <a name="remarks"></a>コメント  
 条件付きコンパイラ定数は常に表示されるファイルにプライベートです。 使用してパブリック コンパイラ定数を作成することはできません、`#Const`ディレクティブです。 または、ユーザー インターフェイスでのみ作成できます、`/define`コンパイラ オプション。  
  
 使用できるは、条件付きコンパイラ定数とリテラルのみ`expression`です。 定義された標準の定数を使用して`Const`エラーが発生します。 逆で定義された定数を使用することができます、`#Const`のみ条件付きコンパイルのキーワードです。 定数できますもで定義されていない場合の値がある`Nothing`です。  
  
## <a name="example"></a>例  
 `#Const` ディレクティブの使用例を次に示します。  
  
 [!code-vb[VbVbalrConditionalComp#3](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/const-directive_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [/define (Visual Basic)](../../../visual-basic/reference/command-line-compiler/define.md)  
 [#If...Then...#Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [Const ステートメント](../../../visual-basic/language-reference/statements/const-statement.md)  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
