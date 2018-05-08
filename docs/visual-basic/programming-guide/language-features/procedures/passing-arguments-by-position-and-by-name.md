---
title: 位置と名前による引数渡し (Visual Basic)
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49e313b2d5aa8302ea4b99e643e09f7b43659785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>位置と名前による引数渡し (Visual Basic)
呼び出すと、`Sub`または`Function`プロシージャの引数を渡すことができます*位置によって*— プロシージャの定義に表示される順序で — 渡したりすることができます*名前によって*、なし配置を考慮します。  
  
 宣言されている引数の名前、コロンと等号 (=) を指定する名前で引数を渡す場合 (`:=`)、その後に、引数の値。 任意の順序で名前付き引数を指定することができます。  
  
 たとえば、次`Sub`プロシージャでは、3 つの引数。  
  
 [!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]  
  
 このプロシージャを呼び出すときは、位置、名、または両方の組み合わせを使用して引数を指定できます。  
  
## <a name="passing-arguments-by-position"></a>位置による引数渡し  
 呼び出すことができます、`Display`その引数を持つメソッドが位置によって渡され、次の例に示すように、コンマで区切られます。  
  
[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)] 
  
 位置指定引数リストで省略可能な引数を省略した場合、コンマでは、その場所を保持する必要があります。 次の例では、`Display`メソッドなし、`age`引数。  
  
[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)] 
  
## <a name="passing-arguments-by-name"></a>名前による引数渡し  
 代わりに、呼び出すことができます`Display`、名前によって渡される引数でもコンマで区切られた、次の例で示すようにします。  
  
[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)] 

 この方法で名前による引数渡しは、1 つ以上の省略可能な引数を持つプロシージャを呼び出す場合に特に便利です。 名前で引数を指定する場合、引数の位置を示すためにコンマを使用するはありません。 名前による引数渡しもやすく引数を渡し、どれを省略しているを追跡するためです。  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>位置と名前による引数の混在  

次の例で示すように、両方の位置と、1 つのプロシージャ呼び出しで名前による引数を指定できます。  
  
[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)] 
  
 上記の例では、余分なコンマは省略された場所を保持するために必要な`age`引数、ので`birth`は名前によって渡されます。  
  
15.5 前に、のバージョンの Visual Basic での位置と名前、位置指定引数の組み合わせで引数を指定するときにする必要がありますすべて先に指定します。 名前で引数を指定すると、残りの引数必要がありますすべてで渡される名前。  たとえば、次の呼び出し、`Display`メソッドには、コンパイラ エラーが表示されます。 [BC30241: 名前付き引数が期待どおり](../../../misc/bc30241.md)です。

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)] 

Visual Basic 15.5 から始めて、位置指定引数は、名前付き引数終了の位置指定引数が正しい位置にある場合。 Visual Basic 15.5、前の呼び出しでコンパイルされた場合、`Display`メソッドが正常にコンパイルし、コンパイラ エラーが発生しなく[BC30241](../../../misc/bc30241.md)です。  

混在させるし、任意の順序で名前付きおよび位置指定引数を照合するには、この機能は、コードを読みやすくする名前付き引数を使用するときに特に便利です。 たとえば、次`Person`クラスのコンス トラクターには、型の 2 つの引数が必要です。 `Person`、どちらも指定できます`Nothing`です。 

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)] 

ときに、コードの意図を作成するために役立ちますオフ、混合の名前付きおよび位置指定引数を使用しての値、`father`と`mother`引数は`Nothing`:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)] 

名前付き引数による位置指定引数を次に、Visual Basic プロジェクトに次の要素を追加する必要があります (\*.vbproj) ファイル。

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

## <a name="restrictions-on-supplying-arguments-by-name"></a>名前による引数渡しに関する制限事項  

必須の引数を入力せずに名前で引数を渡すことはできません。 省略可能な引数だけを省略できます。  
  
名前で、パラメーター配列を渡すことはできません。 これは、プロシージャを呼び出すときのパラメーター配列に対してコンマで区切った不特定数を指定して、コンパイラは、単一の名前を 1 つ以上の引数を関連付けることはできませんです。  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)  
 [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)  
 [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)  
 [省略可能なパラメーター](./optional-parameters.md)  
 [パラメーター配列](./parameter-arrays.md)  
 [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
