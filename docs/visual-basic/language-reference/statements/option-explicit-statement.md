---
title: "Option Explicit Statement (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.Explicit"
  - "vb.OptionExplicit"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "declaring variables, explicit"
  - "forced variable declaration in Option Explicit statement"
  - "Explicit keyword"
  - "explicit variable declaration"
  - "Option Explicit statement"
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Option Explicit Statement (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ファイル内のすべての変数を明示的に宣言するよう強制するか、変数の暗黙の宣言を許可します。  
  
## 構文  
  
```  
Option Explicit { On | Off }  
```  
  
## 指定項目  
 `On`  
 省略可能です。  `Option Explicit` チェックを有効にします。  `On` または `Off` を指定しない場合は、既定で `On` になります。  
  
 `Off`  
 省略可能です。  `Option Explicit` チェックを無効にします。  
  
## 解説  
 ファイル内に `Option Explicit On` または `Option Explicit` を記述したときは、すべての変数を `Dim` ステートメントまたは `ReDim` ステートメントで明示的に宣言する必要があります。  宣言されていない変数名を使用すると、コンパイル時にエラーが発生します。  `Option Explicit Off` ステートメントを使用すると、変数を暗黙的に宣言できます。  
  
 `Option Explicit` ステートメントを使用する場合は、ファイル内の他のどのソース コード ステートメントよりも前に記述する必要があります。  
  
> [!NOTE]
>  一般的に、`Option Explicit` を `Off` に設定することは適切な方法ではありません。  1 つ以上の場所で変数名のスペルを間違えると、プログラムの実行時に予期しない結果が生じる可能性があります。  
  
## Option Explicit ステートメントが存在しない場合  
 ソースコードに `Option Explicit` ステートメントが含まれていない場合は、[\[コンパイル\] ページ、プロジェクト デザイナー \(Visual Basic\)](/visual-studio/ide/reference/compile-page-project-designer-visual-basic) の **Option Explicit** 設定が使用されます。  コマンド ライン コンパイラを使用する場合は、[\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) コンパイラ オプションが使用されます。  
  
#### IDE で Option Explicit を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **\[コンパイル\]** タブをクリックします。  
  
3.  **\[Option Explicit\]** ボックスで値を設定します。  
  
 新しいプロジェクトを作成するとき、**\[コンパイル\]** タブの **\[Option Explicit\]** 設定は、**\[Visual Basic の既定値\]** ダイアログ ボックスの **\[Option Explicit\]** 設定に設定されます。  **\[Visual Basic の既定値\]** ダイアログ ボックスを表示するには、**\[ツール\]** メニューの **\[オプション\]** をクリックします。  **\[オプション\]** ダイアログ ボックスで、**\[プロジェクトおよびソリューション\]** を展開し、**\[Visual Basic の既定値\]** をクリックします。  **\[Visual Basic の既定値\]** の既定の初期設定は `On` です。  
  
#### コマンド ラインで Option Explicit を設定するには  
  
-   **vbc** コマンドに [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md) コンパイラ オプションを含めます。  
  
## 使用例  
 次の例では、`Option Explicit` ステートメントを使用して、すべての変数を明示的に宣言するよう強制します。  宣言されていない変数を使用すると、コンパイル時にエラーが発生します。  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## 参照  
 [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [\/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [\/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [\/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [\[Visual Basic の既定値\] \(\[オプション\] ダイアログ ボックス \- \[プロジェクト\]\)](/visual-studio/ide/reference/visual-basic-defaults-projects-options-dialog-box)