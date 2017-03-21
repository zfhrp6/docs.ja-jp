---
title: "/debug (Visual Basic) |Microsoft ドキュメント"
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
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
caps.latest.revision: 18
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
ms.openlocfilehash: 7384e69f066022e861a4277f418df3f4d094c3be
ms.lasthandoff: 03/13/2017

---
# <a name="debug-visual-basic"></a>/debug (Visual Basic)
コンパイラでデバッグ情報が生成され、出力ファイルに配置します。  
  
## <a name="syntax"></a>構文  
  
```  
/debug[+ | -]  
' -or-  
/debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`+` &#124; `-`|省略可能です。 指定する`+`または`/debug`コンパイラがデバッグ情報が生成され、.pdb ファイルに配置します。 指定する`-`を指定しないと同じ効果を持ちます`/debug`します。|  
|`full` &#124; `pdbonly`|省略可能です。 コンパイラによって生成されるデバッグ情報の種類を指定します。 指定しない場合`/debug:pdbonly`、既定値は`full`、実行中のプログラムにデバッガーをアタッチできます。 `pdbonly`引数では、ソース コードのデバッグ、デバッガーでプログラムを開始するが、実行中のプログラムが、デバッガーに接続されている場合にのみ、アセンブリ言語のコードが表示されます。|  
  
## <a name="remarks"></a>コメント  
 このオプションを使用すると、デバッグ ビルドを作成できます。 指定しない場合`/debug`、 `/debug+`、または`/debug:full`プログラムの出力ファイルをデバッグすることはできません。  
  
 既定では、デバッグ情報は生成されず (`/debug-`)。 デバッグ情報を出力する次のように指定します。`/debug`または`/debug+`です。  
  
 アプリケーションのデバッグ パフォーマンスを構成する方法については、「[イメージのデバッグの簡略化](http://msdn.microsoft.com/library/7d90ea7a-150f-4f97-98a7-f9c26541b9a3)」を参照してください。  
  
|統合開発環境 Visual Studio で/debug を設定するには|  
|---|  
|1.**ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。<br />2.**[コンパイル]** タブをクリックします。<br />3.クリックして**詳細コンパイル オプション**します。<br />4.値を変更、**デバッグ情報の生成**ボックス。|  
  
## <a name="example"></a>例  
 次の例は、デバッグ情報を出力ファイルに入れ`App.exe`します。  
  
```  
vbc /debug /out:app.exe test.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
