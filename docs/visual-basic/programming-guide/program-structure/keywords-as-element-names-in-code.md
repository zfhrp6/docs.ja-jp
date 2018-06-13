---
title: コード内の要素名としてのキーワード (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
ms.openlocfilehash: 53c3172e8518115d001c23be2430fbc87ae1b60f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652579"
---
# <a name="keywords-as-element-names-in-code-visual-basic"></a>コード内の要素名としてのキーワード (Visual Basic)
すべてのプログラム要素 — 変数、クラス、またはメンバーなど、予約されたキーワードと同じ名前を持つことができます。 たとえば、という名前の変数を作成することができます`Loop`です。 ただし、そのバージョンを参照する —、制限と同じ名前を持つ`Loop`キーワード — 完全修飾文字列を付けますか、角かっこで囲んでする必要があります (`[ ]`) 次の例に示すように、します。  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/keywords-as-element-names-in-code_1.vb)]  
  
 これらのうち、どちらも行わないかどうかは、Visual Basic は、組み込みの使用を想定しています`Loop`キーワードと、次の例のように、エラーが発生します。  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 角かっこを使用するには、フォームとコントロールを参照するとき、および変数を宣言するか、予約されたキーワードとして同じ名前のプロシージャを定義します。 忘れがち名を修飾するまたは角かっこを含めるため、コードにエラーが発生し読み取るが難しくなります。 このため、プログラム要素の名前として予約キーワードを使用しないことをお勧めします。 ただし、将来のバージョンの Visual Basic では、既存のフォームまたはコントロールの名前と競合している新しいキーワードを定義する場合、できる方法を使用するこのコードを更新するときに、新しいバージョンを使用します。  
  
> [!NOTE]
>  また、プログラムは、他の参照先アセンブリによって提供される要素名をなどがあります。 これらの名前は、制限付きのキーワードと競合している場合、角かっこで囲むことにすると Visual Basic では定義された要素として解釈します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic の名前付け規則](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)
