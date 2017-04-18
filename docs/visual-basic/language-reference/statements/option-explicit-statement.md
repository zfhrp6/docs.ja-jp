---
title: "Option Explicit ステートメント (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Explicit
- vb.OptionExplicit
dev_langs:
- VB
helpviewer_keywords:
- declaring variables, explicit
- forced variable declaration in Option Explicit statement
- Explicit keyword
- explicit variable declaration
- Option Explicit statement
ms.assetid: e82ac1ad-2cd3-49b2-b985-8bcf016f3fcc
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 020f12f1fbb9a06647215f1fac6324e3b74e8a77
ms.lasthandoff: 03/13/2017

---
# <a name="option-explicit-statement-visual-basic"></a>Option Explicit ステートメント (Visual Basic)
強制的に、ファイルのすべての変数を明示的に宣言または変数の暗黙の宣言を許可します。  
  
## <a name="syntax"></a>構文  
  
```  
Option Explicit { On | Off }  
```  
  
## <a name="parts"></a>指定項目  
 `On`  
 省略可能です。 により、`Option Explicit`をチェックします。 場合`On`または`Off`が指定されていない、既定値は`On`です。  
  
 `Off`  
 省略可能です。 無効に`Option Explicit`をチェックします。  
  
## <a name="remarks"></a>コメント  
 `Option Explicit On`または`Option Explicit`を使用してすべての変数を明示的に宣言する必要がありますが、ファイルに表示されます、`Dim`または`ReDim`ステートメントです。 宣言されていない変数名を使用しようとする場合は、コンパイル時にエラーが発生します。 `Option Explicit Off`ステートメントでは、変数の暗黙の宣言を使用できます。  
  
 使用した場合、`Option Explicit` ステートメントはファイル内で他のソース コード ステートメントよりも前に記述する必要があります。  
  
> [!NOTE]
>  設定`Option Explicit`に`Off`は一般にないことをお勧めします。 プログラムの実行時に予期しない結果になる&1; つまたは複数の場所で、変数名のスペルを間違えた可能性があります。  
  
## <a name="when-an-option-explicit-statement-is-not-present"></a>Option Explicit ステートメントが存在しない場合  
 ソース コードが含まれていない場合、`Option Explicit`ステートメント、 **Option Explicit**の設定、[コンパイル ページで、プロジェクト デザイナー) (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic)を使用します。 コマンド ライン コンパイラを使用する場合、 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)コンパイラ オプションを使用します。  
  
#### <a name="to-set-option-explicit-in-the-ide"></a>IDE で Option explicit ステートメントを設定するには  
  
1.  **ソリューション エクスプ ローラー**プロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **[コンパイル]** タブをクリックします。  
  
3.  値を設定、 **Option Explicit**ボックス。  
  
 新しいプロジェクトを作成するときに、 **Option Explicit**の設定、**コンパイル**に設定されているタブ、 **Option Explicit**で設定、 **VB の既定値** ダイアログ ボックス。 アクセスする、**既定値は VB**  ダイアログ ボックスの 、**ツール** メニューのをクリックして**オプション**します。 **オプション** ダイアログ ボックスで、展開**プロジェクトおよびソリューション**、 をクリックし、 **VB が既定で**します。 初期の既定の設定**VB 既定**は`On`です。  
  
#### <a name="to-set-option-explicit-on-the-command-line"></a>コマンドラインで Option explicit ステートメントを設定するには  
  
-   含める、 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)コンパイラ オプションで、 **vbc**コマンドです。  
  
## <a name="example"></a>例  
 次の例では、`Option Explicit`ステートメントを強制的にすべての変数を明示的に宣言します。 宣言されていない変数を使用するとすると、コンパイル時にエラーが発生します。  
  
 [!code-vb[VbVbalrStatements #&47;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_1.vb)]  
  
 [!code-vb[VbVbalrStatements #&48;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/option-explicit-statement_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Dim ステートメント](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [ReDim ステートメント](../../../visual-basic/language-reference/statements/redim-statement.md)   
 [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
