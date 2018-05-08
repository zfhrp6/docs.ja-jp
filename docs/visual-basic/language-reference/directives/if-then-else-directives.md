---
title: '#もし。。。Then... #Else ディレクティブ'
ms.date: 04/11/2018
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69ce56d770de5f004f204b1764fd51d948ba92c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
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

条件付きコンパイル ブロック内のステートメントは、完全な論理ステートメントである必要があります。 たとえば、条件付きで、関数の属性だけをコンパイルすることはできませんが、条件付きでその属性と共に、関数を宣言することができます。

```vb
   #If DEBUG Then
   <WebMethod()>
   Public Function SomeFunction() As String
   #Else
   <WebMethod(CacheDuration:=86400)>
   Public Function SomeFunction() As String
   #End If
```

## <a name="example"></a>例
 この例では、`#If...Then...#Else`コンストラクトを特定のステートメントをコンパイルするかどうかを判断します。  
  
 [!code-vb[VbVbalrConditionalComp#1](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/if-then-else-directives_1.vb)]  
  
## <a name="see-also"></a>関連項目  
[#Const ディレクティブ](../../../visual-basic/language-reference/directives/const-directive.md)  
[If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
[条件付きコンパイル](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)   
<xref:System.Diagnostics.ConditionalAttribute?displayProperty=nameWithType>   


