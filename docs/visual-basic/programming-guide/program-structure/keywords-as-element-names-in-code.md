---
title: "コード内の要素名としてのキーワード (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, naming conventions
- keywords [Visual Basic], in code
- name conflicts [Visual Basic]
- element names [Visual Basic], in code
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f410a0eaac0dcc034d406a89ed1d01a8f228a583
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
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
