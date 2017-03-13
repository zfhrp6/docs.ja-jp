---
title: "Option Compare Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Compare"
  - "vb.OptionCompare"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "case sensitivity, Option Compare statement"
  - "Compare keyword"
  - "binary comparison"
  - "strings [Visual Basic], returning from functions"
  - "binary comparison, Option Compare statement"
  - "strings [Visual Basic], comparing"
  - "string comparison [Visual Basic], Option Compare statement"
  - "Text keyword, Option Compare statement"
  - "Binary keyword, Option Compare statement"
  - "string comparison [Visual Basic], sorting data"
  - "Option Compare statement"
  - "text [Visual Basic], comparing"
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
caps.latest.revision: 37
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 37
---
# Option Compare Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

文字列データを比較するときに使用する既定の比較方法を宣言します。  
  
## 構文  
  
```  
Option Compare { Binary | Text }  
```  
  
## 指定項目  
  
|||  
|-|-|  
|用語|定義|  
|`Binary`|省略可能です。  文字列比較は、文字の内部バイナリ表現から派生した並べ替え順序に基づきます。<br /><br /> この種類の比較は、文字列にテキストとして解釈されない文字を含めることができる場合に特に便利です。  この場合、大文字と小文字の区別など、アルファベットの等値比較にバイアスをかけないことをお勧めします。|  
|`Text`|省略可能です。  文字列比較は、システムのロケールによって決まる、大文字と小文字を区別しないテキストの並べ替え順序に基づきます。<br /><br /> この種類の比較は、文字列にすべてのテキスト文字が含まれており、大文字と小文字を区別しないことや類縁の文字など、アルファベットの等値を考慮して文字列を比較する場合に便利です。  たとえば、`A` と `a` は等しく、`Ä` と `ä` は `B` と `b` よりも前に位置すると見なされるようにできます。|  
  
## 解説  
 使用した場合、`Option Compare` ステートメントはファイル内で他のソース コード ステートメントよりも前に記述する必要があります。  
  
 `Option Compare` ステートメントでは、文字列の比較方法 \(`Binary` または `Text`\) を指定します。  既定のテキスト比較方法は `Binary` です。  
  
 `Binary` 比較では、各文字列の各文字の Unicode 数値が比較されます。  `Text` 比較では、現在のカルチャでの語彙的意味に基づいて各 Unicode 文字が比較されます。  
  
 Microsoft Windows では、並べ替え順序はコード ページによって決まります。  詳細については、「[コード ページ](/visual-cpp/c-runtime-library/code-pages)」を参照してください。  
  
 次の例では、英語\/ヨーロッパ言語のコード ページ \(ANSI 1252\) の文字が、`Option Compare Binary` を使用して並べ替えられ、一般的なバイナリ並べ替え順序が生成されます。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 `Option Compare Text` を使用して同じコード ページの同じ文字を並べ替えると、次のテキスト並べ替え順序が生成されます。  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## Option Compare ステートメントが指定されていない場合  
 ソース コードに `Option Compare` ステートメントが含まれていない場合は、[\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) の **Option Compare** 設定が使用されます。  コマンド ライン コンパイラを使用した場合は、[\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) コンパイラ オプションによって指定された設定が使用されます。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
#### IDE で Option Compare を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[NIB: Managing Project Properties with the Project Designer](http://msdn.microsoft.com/ja-jp/983f3c18-832f-4666-afec-74b716ff3e0e)」を参照してください。  
  
2.  **\[コンパイル\]** タブをクリックします。  
  
3.  **\[Option Compare\]** ボックスに値を設定します。  
  
 プロジェクトを作成すると、**\[コンパイル\]** タブの **\[Option Compare\]** 設定が **\[オプション\]** ダイアログ ボックスの **\[Option Compare\]** 設定に設定されます。  この設定を変更するには、**\[ツール\]** メニューの **\[オプション\]** をクリックします。  **\[オプション\]** ダイアログ ボックスの **\[プロジェクトおよびソリューション\]** を展開し、**\[VISUAL BASIC の既定値\]** をクリックします。  **\[VISUAL BASIC の既定値\]** の初期の既定値は **\[バイナリ\]** です。  
  
#### コマンド ラインで Option Compare を設定するには  
  
-   **vbc** コマンドに [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md) コンパイラ オプションを含めます。  
  
## 使用例  
 次の例では、`Option Compare` ステートメントを使用して、既定の文字列比較方法としてバイナリ比較を設定します。  このコードを使用するには、`Option Compare Binary` ステートメントのコメントを解除し、ソース ファイルの先頭に配置します。  
  
 [!code-vb[VbVbalrStatements#45](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_1.vb)]  
  
## 使用例  
 次の例では、`Option Compare` ステートメントを使用して、既定の文字列比較方法として大文字と小文字を区別しないテキスト並べ替え順序を設定します。  このコードを使用するには、`Option Compare Text` ステートメントのコメントを解除し、ソース ファイルの先頭に配置します。  
  
 [!code-vb[VbVbalrStatements#46](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-compare-statement_2.vb)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Strings.InStr%2A>   
 <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>   
 <xref:Microsoft.VisualBasic.Strings.Replace%2A>   
 <xref:Microsoft.VisualBasic.Strings.Split%2A>   
 <xref:Microsoft.VisualBasic.Strings.StrComp%2A>   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [Comparison Operators](../../../visual-basic/language-reference/operators/comparison-operators.md)   
 [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)   
 [Like Operator](../../../visual-basic/language-reference/operators/like-operator.md)   
 [文字列関数](../../../visual-basic/language-reference/functions/string-functions.md)   
 [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)