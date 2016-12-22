---
title: "Special Characters in Code (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.)"
  - "vb.("
  - "vb.colon"
  - "vb.!"
  - "vb.."
  - "vb.:"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "special characters, in code"
  - "parentheses, using in code"
  - "colons (:)"
  - "period character in code"
  - "dot operator (.)"
  - "dictionary access operator"
  - "concatenation operators, special characters in code"
  - "concatenation operators, vs. addition operator"
  - "! operator"
  - "separators, using in code"
  - "operators [Visual Basic], dictionary access"
  - ": separator character"
  - "member access operator"
  - "addition operator"
  - "operators [Visual Basic], member access"
  - ". operator"
  - "exclamation points"
  - "separators"
  - "exclamation point operator (!)"
  - "Visual Basic code, special characters"
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Special Characters in Code (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

コードに、英数字ではない特殊文字の使用が必要な場合があります。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] の文字セットに含まれる区切り記号と特殊文字には、プログラム テキストの整理から、コンパイラやコンパイル済みプログラムが実行するタスクの定義まで、さまざまな用途があります。  実行するオペレーションを指定するのには使用されません。  
  
## かっこ  
 `Sub` や `Function` などのプロシージャを定義するときはかっこを使用します。  すべてのプロシージャの引数リストは、かっこで囲む必要があります。  また、かっこは変数や引数を論理グループに含める場合にも使用します。具体的には、複合式の中で演算子の既定の優先順位をオーバーライドする場合にかっこが必要になります。  次に例を示します。  
  
 [!code-vb[VbVbcnConventions#11](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/special-characters-in-code_1.vb)]  
  
 このコードを実行すると、`d` の値は 8.225、`e` の値は 3 になります。  `d` の計算では、`/` の優先順位は既定で `+` よりも高いため、`d = b + (c / a)` を実行しても結果は同じになります。  `e` の計算に使用されているかっこは、既定の優先順位をオーバーライドします。  
  
## 区切り記号  
 区切り記号は、その名前が示すとおり、コードのセクションを区切ります。  [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] では、区切り記号はコロン \(`:`\) です。  複数のステートメントを複数行ではなく単一行に配置する場合に、区切り記号を使用します。  これにより、スペースを節約し、コードを読みやすくすることができます。  コロンで区切られた 3 つのステートメントの例を次に示します。  
  
 [!code-vb[VbVbcnConventions#12](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/special-characters-in-code_2.vb)]  
  
 詳細については、「[方法 : コード内でステートメントを分割および連結する](../Topic/How%20to:%20Break%20and%20Combine%20Statements%20in%20Code%20\(Visual%20Basic\).md)」を参照してください。  
  
 コロン文字 \(`:`\) は、ステートメント ラベルを識別するためにも使用されます。  詳細については、「[How to: Label Statements](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)」を参照してください。  
  
## 連結  
 `&` 演算子は、*連結* つまり文字列を結びつけるために使用します。  数値を加算する `+` 演算子と混同しないでください。  数値を連結する場合に `+` 演算子を使用して連結すると、誤った結果が生成されることがあります。  次に例を示します。  
  
 [!code-vb[VbVbcnConventions#13](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/special-characters-in-code_3.vb)]  
  
 このコードを実行すると、`resultA` の値は 21.01、`resultB` の値は "10.0111" になります。  
  
## メンバー アクセス演算子  
 型のメンバーにアクセスするには、型名とメンバー名の間に、ドット \(`.`\) 演算子または感嘆符 \(`!`\) 演算子を用います。  
  
### ドット \(.\) \[演算子\]  
 `.` 演算子は、クラス、構造体、インターフェイス、列挙値にメンバー アクセス演算子として使用します。  フィールド、プロパティ、イベント、メソッドなどのメンバーに使用できます。  次に例を示します。  
  
 [!code-vb[VbVbcnConventions#14](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/special-characters-in-code_4.vb)]  
  
### 感嘆符 \(\!\) \[演算子\]  
 クラスまたはインターフェイスに限っては、感嘆符 \(`!`\) 演算子をディクショナリ アクセス演算子として使用します。  クラスまたはインターフェイスには、単一の文字列型 \(`String`\) の引数を受け入れる既定のプロパティが必要です。  `!` 演算子のすぐ後に識別子を続けると、既定のプロパティに文字列として渡される引数の値になります。  次に例を示します。  
  
 [!code-vb[VbVbcnConventions#15](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/special-characters-in-code_5.vb)]  
  
 `MsgBox` の 3 つの出力行は、いずれも値 `32856` を表示します。  最初の行では `index` プロパティに通常の方法でアクセスし、2 行目では `index` が `hasDefault` クラスの既定のプロパティであることが利用されています。また、3 行目ではディクショナリ アクセスを使ってクラスにアクセスしています。  
  
 `!` 演算子の 2 つ目のオペランドは、有効な Visual Basic 識別子を二重引用符 \(`" "`\) で囲まずに定義する必要があることに注意してください。  つまり、文字列リテラルや文字列変数を使うことはできません。  `MsgBox` 呼び出しの最後の行を次のように書き換えると、文字列リテラルが `"X"` のように二重引用符で囲まれているためエラーが発生します。  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  既定コレクションの参照は、必ず明示的に指定してください。  特に、遅延バインディング変数では `!` 演算子を使用できません。  
  
 感嘆符 \(`!`\) は、`Single` の型宣言文字としても使用されます。  
  
## 参照  
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)