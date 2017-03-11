---
title: "Visual Basic Limitations | Microsoft Docs"
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
  - "limits"
  - "limitations, Visual Basic"
  - "limitations"
  - "limits, Visual Basic code"
  - "Visual Basic code, limitations"
ms.assetid: cf1646b7-5d24-48c6-9616-bda8a4849d91
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Visual Basic Limitations
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

以前のバージョンの [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] では、コードに対して、変数名の長さ、モジュールで許可される変数の数、モジュール サイズなどの制限が課されていました。  [!INCLUDE[vbprvblong](../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong-md.md)] ではこれらの制限が緩和され、コードの記述と配置がより自由になりました。  
  
 物理的な制限は、コンパイル時の環境よりも実行時のメモリに左右される部分が大きくなりました。  慎重なプログラミング習慣に従い、大きなアプリケーションを複数のクラスとモジュールに分割していれば、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] の内部的な制限にぶつかることはほとんどありません。  
  
 極端なケースで遭遇し得るいくつかの制限を次に示します。  
  
-   **名前の長さ。**すべての宣言されるプログラミング要素には、名前の文字数に上限があります。  要素名が修飾されている場合は、修飾された文字列全体に対して制限が適用されます。  「[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。  
  
-   **行の長さ。**ソース コードの物理行の最大文字数は 65535 文字です。  行連結文字を使用すると、それよりも長い論理ソース コード行を記述できます。  「[方法 : コード内でステートメントを分割および連結する](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)」を参照してください。  
  
-   **配列の次元。**配列で宣言できる次元の数には上限があります。  これにより、配列要素を指定するときに使用できるインデックスの数が制限されます。  「[Array Dimensions in Visual Basic](../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)」を参照してください。  
  
-   **文字列の長さ。**1 つの文字列に格納できる Unicode 文字数には上限があります。  「[String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md)」を参照してください。  
  
-   **環境文字列の長さ。**コマンド ライン引数として使用される環境文字列の最大文字数は 32768 文字です。  これは全プラットフォームにおける制限です。  
  
## 参照  
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)