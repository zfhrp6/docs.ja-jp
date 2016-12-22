---
title: "Imports Statement (.NET Namespace and Type) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Imports"
  - "imports"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declared element names [Visual Basic], qualification"
  - "imports [Visual Basic]"
  - "Imports statement [Visual Basic]"
  - "aliases [Visual Basic], Imports statement"
  - "container elements [Visual Basic]"
  - "namespaces [Visual Basic], importing"
  - "Imports statement [Visual Basic], syntax"
  - "import aliases [Visual Basic]"
  - "aliases [Visual Basic], import"
  - "declared elements [Visual Basic], container elements"
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
caps.latest.revision: 40
caps.handback.revision: 40
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Imports Statement (.NET Namespace and Type)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

名前空間による修飾なしで型名を参照できるようにします。  
  
## 構文  
  
```  
Imports [ aliasname = ] namespace  
-or-  
Imports [ aliasname = ] namespace.element  
```  
  
## 指定項目  
  
|||  
|-|-|  
|語句|定義|  
|`aliasname`|省略可能です。  コードが `namespace` を参照するために、完全修飾文字列の代わりに使用する*インポート エイリアス*または名前です。  「[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。|  
|`namespace`|必ず指定します。  インポートされる名前空間の完全修飾名を指定します。  入れ子構造のどのレベルにある名前空間の文字列でも指定できます。|  
|`element`|省略可能です。  名前空間に宣言されているプログラミング要素の名前を指定します。  任意のコンテナー 要素を指定できます。|  
  
## 解説  
 `Imports`  ステートメントを使用すると、指定された名前空間に含まれる型を直接参照できます。  
  
 入れ子になった名前空間の名前空間名または文字列を 1 つで指定できます。  より高いレベルの名前空間から入れ子にされた名前空間を区切るには、ピリオド \(`.`\) を使います。次に例を示します。  
  
 `Imports System.Collections.Generic`  
  
 1 つのファイルで使用できる `Imports` ステートメントの数に制限はありません。  このステートメントの前には、`Option Strict` ステートメントなどの任意のオプションを宣言する必要があり、後には `Module` ステートメントや `Class` ステートメントなどの任意のプログラミング要素を宣言する必要があります。  
  
 `Imports` を使用できるのはファイル レベルだけです。  つまり、インポートの宣言コンテキストは、ソース ファイルである必要があり、名前空間、クラス、構造体、モジュール、インターフェイス、プロシージャ、またはブロックでは宣言できません。  
  
 `Imports` ステートメントを指定しても、他のプロジェクトとアセンブリの要素を自分のプロジェクトで使用できるようになるわけではありません。  インポートは参照を設定する代わりには使用できません。  もともとプロジェクトで利用可能な名前を修飾する必要がなくなるだけです。  詳細については、「[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」の「コンテナー要素のインポート」を参照してください。  
  
> [!NOTE]
>  [\[参照設定\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](../Topic/References%20Page,%20Project%20Designer%20\(Visual%20Basic\).md) を使用して、暗黙的な `Imports` ステートメントを定義できます。  詳細については、「[方法 : インポートした名前空間を追加または削除する \(Visual Basic\)](../Topic/How%20to:%20Add%20or%20Remove%20Imported%20Namespaces%20\(Visual%20Basic\).md)」を参照してください。  
  
## インポート エイリアス  
 *インポート エイリアス*は、名前空間または型のエイリアスを定義します。  1 つ以上の名前空間で宣言されているのと同名の項目を使用する必要がある場合は、インポート エイリアスが便利です。  詳細と使用例については、「[References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)」の「要素名の修飾」を参照してください。  
  
 `aliasname` と同じ名前のモジュールのレベルでメンバーを宣言することはできません。  宣言した場合、Visual Basic コンパイラは宣言されたメンバーにのみ `aliasname` を使用し、これをインポート エイリアスとして認識しなくなります。  
  
 インポート エイリアスの宣言に使用される構文は、XML 名前空間プレフィックスのインポートに使用される構文と似ていますが、結果は異なります。  インポート エイリアスはコード内で式として使用できるのに対して、XML 名前空間プレフィックスは XML リテラルまたは XML 軸プロパティで、修飾された要素名または属性名のプレフィックスとしてのみ使用できます。  
  
### 要素名  
 `element` を指定する場合、その要素は*コンテナー要素*であることが必要です。つまり、他の要素を格納できるプログラミング要素を指定する必要があります。  コンテナー要素にはクラス、構造体、モジュール、インターフェイス、および列挙体が含まれます。  
  
 `Imports` ステートメントによって利用可能になる要素のスコープは、`element` を指定するかどうかによって変わります。  `namespace` だけを指定した場合、その名前空間の一意な名前を持つすべてのメンバー、およびその名前空間に含まれるコンテナー要素のメンバーを、修飾子なしで使用できます。  `namespace` と `element` を指定した場合は、その要素のメンバーだけを修飾子なしで使用できます。  
  
## 使用例  
 次の例では、<xref:System.IO.DirectoryInfo> クラスを使用して、C:\\ ディレクトリ内のすべてのフォルダーを返します。  
  
 ファイルの先頭に `Imports` ステートメントがありません。  そのため、`DirectoryInfo`、<xref:System.Text.StringBuilder>、および <xref:Microsoft.VisualBasic.ControlChars.CrLf> の各参照は、すべて名前空間で完全に修飾されています。  
  
 [!code-vb[VbVbalrStatements#152](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_1.vb)]  
  
## 使用例  
 次の例では、参照される名前空間に対する `Imports` ステートメントを使用しています。  そのため、型を名前空間で完全に修飾する必要はありません。  
  
 [!code-vb[VbVbalrStatements#153](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_2.vb)]  
  
 [!code-vb[VbVbalrStatements#154](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_3.vb)]  
  
## 使用例  
 次の例では、参照される名前空間のエイリアスを作成する `Imports` ステートメントを使用しています。  型はエイリアスで修飾されています。  
  
 [!code-vb[VbVbalrStatements#155](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_4.vb)]  
  
 [!code-vb[VbVbalrStatements#156](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_5.vb)]  
  
## 使用例  
 次の例では、参照される型のエイリアスを作成する `Imports` ステートメントを使用しています。  エイリアスを使用して型が指定されています。  
  
 [!code-vb[VbVbalrStatements#157](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_6.vb)]  
  
 [!code-vb[VbVbalrStatements#158](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/imports-statement-net-namespace-and-type_7.vb)]  
  
## 参照  
 [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md)   
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)   
 [References to Declared Elements](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)