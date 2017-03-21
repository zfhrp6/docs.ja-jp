---
title: "/optimize |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization, enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: bb89b94ab0d431ed79f94f22afd0bd077728b754
ms.lasthandoff: 03/13/2017

---
# <a name="optimize"></a>/optimize
有効またはコンパイラの最適化を無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`+` &#124; `-`|省略可能です。 `/optimize-`オプションは、コンパイラの最適化を無効になります。 `/optimize+`の最適化を有効にします。 既定では、最適化が無効になります。|  
  
## <a name="remarks"></a>コメント  
 コンパイラの最適化は、小さく、高速、かつ効率的に出力ファイルを作成します。 ただし、出力ファイルにコードの再配置の最適化を行うので、`/optimize+`デバッグが困難です。  
  
 生成されるすべてのモジュール`/target:module`アセンブリは同じで使用する必要があります`/optimize`アセンブリとして設定します。 詳細については、次を参照してください。 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)します。  
  
 組み合わせることができます、`/optimize`と`/debug`オプション。  
  
|Visual Studio 統合開発環境で/optimize を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。<br />     詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.**[コンパイル]** タブをクリックします。<br />3.[詳細設定 **** ] ボタンをクリックします。<br />4.変更、**の最適化を有効にする**チェック ボックスをオンします。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`T2.vb`でき、コンパイラの最適化。  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md)   
 [コンパイル コマンドラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
