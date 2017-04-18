---
title: "/optioncompare |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optioncompare
dev_langs:
- VB
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
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
ms.openlocfilehash: 53dee5bb50e20204725f031e3e04f5c37c5b3f96
ms.lasthandoff: 03/13/2017

---
# <a name="optioncompare"></a>/optioncompare
文字列比較の方法を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/optioncompare:{binary | text}  
```  
  
## <a name="remarks"></a>コメント  
 指定できます`/optioncompare`で&2; つの形式:`/optioncompare:binary`バイナリ文字列比較を使用して`/optioncompare:text`テキスト文字列の比較を使用します。 既定では、コンパイラを使用して`/optioncompare:binary`します。  
  
 Microsoft Windows では、使用されているコード ページは、バイナリ並べ替え順を決定します。 一般的なバイナリ並べ替え順序は次のとおりです。  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 テキスト ベースの文字列比較は、システムのロケールで決定される小文字を区別しないテキスト並べ替え順序に基づきます。 一般的なテキストの並べ替え順序は次のとおりです。  
  
 `(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
### <a name="to-set-optioncompare-in-the-visual-studio-ide"></a>Visual Studio IDE で/optioncompare を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **[コンパイル]** タブをクリックします。  
  
3.  値を変更、 **Option Compare**ボックス。  
  
### <a name="to-set-optioncompare-programmatically"></a>/Optioncompare をコードから設定するには  
  
-   参照してください[Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)します。  
  
## <a name="example"></a>例  
 次のコードでは、P`rojFile.vb`バイナリ文字列比較を使用しています。  
  
```  
vbc /optioncompare:binary projFile.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)   
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)   
 [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
