---
title: "Option Explicit ステートメント (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
helpviewer_keywords:
- declaring variables [Visual Basic], explicit
- forced variable declaration in Option Explicit statement [Visual Basic]
- Explicit keyword
- explicit variable declaration
- Option Explicit statement [Visual Basic]
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3d4c9cd3310e0ec3943c4e2b5e28be5b9a393db
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit ステートメント (Visual Basic)
強制的に、ファイル内のすべての変数を明示的に宣言または変数の暗黙的な宣言を許可します。  
  
## <a name="syntax"></a>構文  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>指定項目  
 `On`  
 任意。 により、`Option Explicit`をチェックします。 場合`On`または`Off`が指定されていない、既定値は`On`します。  
  
 `Off`  
 任意。 無効に`Option Explicit`をチェックします。  
  
## <a name="remarks"></a>コメント  
 ときに`Option Explicit On`または`Option Explicit`を使用してすべての変数を明示的に宣言する必要がありますが、ファイルに表示されます、`Dim`または`ReDim`ステートメントです。 宣言されていない変数名を使用しようとする場合は、コンパイル時にエラーが発生します。 `Option Explicit Off`ステートメントにより、変数を暗黙的に宣言します。  
  
 使用した場合、`Option Explicit` ステートメントはファイル内で他のソース コード ステートメントよりも前に記述する必要があります。  
  
> [!NOTE]
>  設定`Option Explicit`に`Off`は一般にないことをお勧めします。 変数名のスペルを 1 か所以上間違えると、プログラムの実行時に予期しない結果を招く可能性があります。  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Option Explicit ステートメントが存在する場合されません。  
 ソース コードが含まれていない場合、`Option Explicit`ステートメントでは、 **Option Explicit**の設定、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)を使用します。 コマンド ライン コンパイラを使用する場合、 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)コンパイラ オプションを使用します。  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>IDE で Option Explicit を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2.  **[コンパイル]** タブをクリックします。  
  
3.  値を設定、 **Option Explicit**ボックス。  
  
 新しいプロジェクトを作成するときに、 **Option Explicit**の設定、**コンパイル** タブに設定されている、 **Option Explicit**での設定、 **VBの既定値** ダイアログ ボックス。 アクセスする、**既定値は VB**  ダイアログ ボックスで、**ツール** メニューのをクリックして**オプション**です。 **[オプション]** ダイアログ ボックスの **[プロジェクトおよびソリューション]** を展開し、**[VISUAL BASIC の既定値]** をクリックします。 初期の既定の設定**VB 既定**は`On`します。  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>コマンドラインで Option Explicit を設定するには  
  
-   含める、 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)コンパイラ オプション、 **vbc**コマンド。  
  
## <a name="example"></a>例  
 次の例では、`Option Explicit`すべての変数の明示的な宣言を強制するステートメント。 宣言されていない変数を使用すると場合、コンパイル時にエラーが発生します。  
  
 [!code-vb[VbVbalrStatements#47](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements#48](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a>参照  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)  
 [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)  
 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
