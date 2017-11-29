---
title: "#<a name=\"ifthenelse-directives\"></a>もし。。。Then... #Else ディレクティブ"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.#EndIf
- '#End If'
- '#Then'
- '#ElseIf'
- vb.#ElseIf
- vb.#Else
- vb.#If
helpviewer_keywords:
- Visual Basic code, compiling
- '#If directive [Visual Basic]'
- conditional compilation [Visual Basic], directives
- '#End if directive [Visual Basic]'
- selective compiling
- else directive (#else)
- '#Else directive [Visual Basic]'
ms.assetid: 10bba104-e3fd-451b-b672-faa472530502
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 77757e441ae937aa86122f237e839d1005644409
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ifthenelse-directives"></a>#If...Then...#Else ディレクティブ
条件付きで選択した Visual Basic コード ブロックをコンパイルします。  
  
## <a name="syntax"></a>構文  
  
```  
#If expression Then  
   statements  
[ #ElseIf expression Then  
   [ statements ]  
...  
#ElseIf expression Then  
   [ statements ] ]  
[ #Else  
   [ statements ] ]  
#End If  
```  
  
## <a name="parts"></a>指定項目  
 `expression`  
 必要な`#If`と`#ElseIf`ステートメント、省略可能な他の場所。 1 つまたは複数の条件付きコンパイラ定数、リテラル、およびに評価される演算子だけで構成される、任意の式`True`または`False`です。  
  
 `statements`  
 必要な`#If`ステートメント ブロック、省略可能な他の場所。 Visual Basic プログラム行またはに関連付けられた式が評価された場合にコンパイルされているコンパイラ ディレクティブ`True`です。  
  
 `#End If`  
 終了、`#If`ステートメント ブロックします。  
  
## <a name="remarks"></a>コメント  
 画面の動作で、`#If...Then...#Else`ディレクティブが同じのように見える、`If...Then...Else`ステートメントです。 ただし、`#If...Then...#Else`ディレクティブ、コンパイラによってどのようなコンパイルが一方の評価、`If...Then...Else`ステートメントが実行時に条件を評価します。  
  
 条件付きコンパイルは通常、さまざまなプラットフォームの同じプログラムのコンパイルに使用されます。 防ぐためにも使用する実行可能ファイルに表示されないコードをデバッグします。 条件付きコンパイル中に除外されたコードを完全に省略すると、最終的な実行可能ファイルからサイズやパフォーマンスに影響があるないようにします。  
  
 使用して、任意の評価の結果に関係なくすべての式が評価は`Option Compare Binary`します。 `Option Compare`ステートメントでは内の式には影響しません`#If`と`#ElseIf`ステートメントです。  
  
> [!NOTE]
>  単一行形式、 `#If`、 `#Else`、 `#ElseIf`、および`#End If`ディレクティブが存在しません。 他のコードは、ディレクティブのいずれかと同じ行に表示できません。  
  
## <a name="example"></a>例  
 この例では、`#If...Then...#Else`コンストラクトを特定のステートメントをコンパイルするかどうかを判断します。  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [#Const ディレクティブ](../../../visual-basic/language-reference/directives/const-directive.md)  
 [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
