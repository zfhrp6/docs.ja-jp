---
title: /optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1cfdb94ebafa7d6a14253aeb59ab98b3a953fe4b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="optionexplicit"></a>/optionexplicit
変数が使用されるように宣言されていない場合は、コンパイラがエラーを報告します。  
  
## <a name="syntax"></a>構文  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 省略可能です。 指定`/optionexplicit+`変数の明示的な宣言を要求するようにします。 `/optionexplicit+`オプションは、既定値と同じとして`/optionexplicit`です。 `/optionexplicit-`変数の暗黙の宣言を有効にします。  
  
## <a name="remarks"></a>コメント  
 ソース コード ファイルが含まれている場合、 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)、ステートメントよりも優先、`/optionexplicit`コマンド ライン コンパイラ設定します。  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a>Visual Studio IDE で/optionexplicit を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **[コンパイル]** タブをクリックします。  
  
3.  値を変更、 **Option Explicit**ボックス。  
  
## <a name="example"></a>例  
 次のコードをコンパイル時に`/optionexplicit-`を使用します。  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
