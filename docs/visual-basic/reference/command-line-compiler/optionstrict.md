---
title: "/optionstrict |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionstrict
dev_langs:
- VB
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
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
ms.openlocfilehash: 0394d9c1f4c082271316829ef1d226bd97d136c9
ms.lasthandoff: 03/13/2017

---
# <a name="optionstrict"></a>/optionstrict
暗黙の型変換を制限するための厳密な型のセマンティクスを適用します。  
  
## <a name="syntax"></a>構文  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a>引数  
 `+` &#124; `-`  
 省略可能です。 `/optionstrict+`オプションは暗黙の型変換を制限します。 このオプションの既定値は`/optionstrict-`です。 `/optionstrict+`オプションは、同じ`/optionstrict`します。 寛容な型の両方を使用することができます。  
  
 `custom`  
 必須です。 厳密な言語セマンティクスが守られていないときに警告します。  
  
## <a name="remarks"></a>コメント  
 `/optionstrict+`が有効で唯一の拡大型の変換を暗黙的に行うことができます。 暗黙的な縮小の割り当てなどの型変換、`Decimal`整数型のオブジェクトをオブジェクトの入力をエラーとして報告されます。  
  
 暗黙的な縮小の型変換の警告を生成する`/optionstrict:custom`です。 使用`/nowarn:numberlist`特定の警告を無視して`/warnaserror:numberlist`特定の警告をエラーとして処理します。  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a>Visual Studio IDE で/optionstrict を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティです。** 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **[コンパイル]** タブをクリックします。  
  
3.  値を変更、 **Option Strict**ボックス。  
  
### <a name="to-set-optionstrict-programmatically"></a>/Optionstrict をコードから設定するには  
  
-   参照してください[Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)します。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`Test.vb`厳密な型変換を使用します。  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [/nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)   
 [/warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)   
 [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Strict ステートメント](../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
