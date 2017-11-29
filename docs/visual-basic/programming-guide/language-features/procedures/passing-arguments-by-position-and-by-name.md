---
title: "位置と名前による引数渡し (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>位置と名前による引数渡し (Visual Basic)
呼び出すと、`Sub`または`Function`プロシージャの引数を渡すことができます*位置によって*— プロシージャの定義に表示される順序で — 渡したりすることができます*名前によって*、なし配置を考慮します。  
  
 宣言されている引数の名前、コロンと等号 (=) を指定する名前で引数を渡す場合 (`:=`)、その後に、引数の値。 任意の順序で名前付き引数を指定することができます。  
  
 たとえば、次`Sub`プロシージャでは、3 つの引数。  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 このプロシージャを呼び出すときは、位置、名、または両方の組み合わせを使用して引数を指定できます。  
  
## <a name="passing-arguments-by-position"></a>位置による引数渡し  
 プロシージャを呼び出すことができます`studentInfo`位置によって渡され、次の例で示すように、コンマで区切り、引数を使用します。  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 位置指定引数リストで省略可能な引数を省略した場合、コンマでは、その場所を保持する必要があります。 次の例では`studentInfo`せず、`age`引数。  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a>名前による引数渡し  
 代わりに、呼び出すことができます`studentInfo`、名前によって渡される引数でもコンマで区切られた、次の例で示すようにします。  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a>位置と名前による引数の混在  
 次の例で示すように、両方の位置と、1 つのプロシージャ呼び出しで名前による引数を指定できます。  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 上記の例では、余分なコンマは省略された場所を保持するために必要な`age`引数、ので`birth`は名前によって渡されます。  
  
 位置と名前、位置指定引数の組み合わせで引数を指定するときのすべてを先にする必要があります。 名前で引数を指定すると、残りの引数すべてがあります名前。  
  
## <a name="supplying-optional-arguments-by-name"></a>省略可能な引数の名前を指定します。  
 名前による引数渡しは、1 つ以上の省略可能な引数を持つプロシージャを呼び出す場合に特に便利です。 名前で引数を指定する場合、引数の位置を示すためにコンマを使用するはありません。 名前による引数渡しもやすく引数を渡し、どれを省略しているを追跡するためです。  
  
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
