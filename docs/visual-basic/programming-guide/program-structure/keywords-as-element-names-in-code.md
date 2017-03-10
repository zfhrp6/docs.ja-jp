---
title: "Keywords as Element Names in Code (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, naming conventions"
  - "keywords [Visual Basic], in code"
  - "name conflicts"
  - "element names, in code"
ms.assetid: 2e4e8e02-23f7-49b9-a1c8-2b0402b6b525
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# Keywords as Element Names in Code (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

変数、クラス、メンバーなどのプログラム要素には、予約キーワードと同じ名前を付けることができます。  たとえば、`Loop` という名前の変数を作成できます。  ただし、予約された `Loop` キーワードと同じ名前を持つ別の `Loop` を指すには、次の例に示すように、先頭に完全な修飾文字列を付けるか、角かっこ \(`[ ]`\) で囲む必要があります。  
  
 [!code-vb[VbVbcnConventions#8](../../../visual-basic/programming-guide/language-features/codesnippet/visualbasic/keywords-as-element-name_1.vb)]  
  
 このどちらも行わない場合、次の例に示すように、Visual Basic では組み込みの `Loop` キーワードを使用していると想定し、エラーを生成します。  
  
 `' The following statement causes a compiler error.`  
  
 `Loop.Visible = True`  
  
 フォームやコントロールを参照するとき、予約キーワードと同じ名前の変数を宣言するとき、または予約キーワードと同じ名前のプロシージャを定義するときには角かっこを使用できます。  修飾名を使用しなかったり、名前を角かっこで囲むことを忘れると、コードにエラーが組み込まれたり、コードが読みにくくなったりします。  このため、プログラム要素の名前と同じ予約キーワードは使用しないことをお勧めします。  ただし、既存のフォーム名またはコントロール名と競合する新規キーワードが将来の Visual Basic のバージョンで定義された場合は、新しいバージョンで動作するようにコードを更新するときにこの技法を使用できます。  
  
> [!NOTE]
>  参照される他のアセンブリから提供される要素名をプログラムに含めることもできます。  これらの要素名が予約キーワードと競合する場合は、名前を角かっこで囲むことによって、Visual Basic は定義された要素として解釈するようになります。  
  
## 参照  
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [キーワード](../../../visual-basic/language-reference/keywords/index.md)