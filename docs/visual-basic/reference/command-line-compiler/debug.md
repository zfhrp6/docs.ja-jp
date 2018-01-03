---
title: /debug (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07ab386ddb456c059b6390b986ec0a880320973b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="debug-visual-basic"></a>/debug (Visual Basic)
コンパイラがデバッグ情報が生成され、出力ファイルに配置します。  
  
## <a name="syntax"></a>構文  
  
```  
/debug[+ | -]  
' -or-  
/debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`+` &#124; `-`|任意。 指定する`+`または`/debug`コンパイラがデバッグ情報を生成して .pdb ファイルに配置します。 指定する`-`を指定しない場合と同じ効果`/debug`です。|  
|`full` &#124; `pdbonly`|任意。 コンパイラによって生成されるデバッグ情報の種類を指定します。 指定しない場合`/debug:pdbonly`、既定値は`full`、実行中のプログラムにデバッガーをアタッチできます。 `pdbonly`引数により、ソース コードのデバッグ時に、デバッガーでプログラムが開始されていて、実行中のプログラムが、デバッガーに接続されている場合にのみ、アセンブリ言語のコードが表示されます。|  
  
## <a name="remarks"></a>コメント  
 このオプションを使用してデバッグ ビルドを作成します。 指定しない場合`/debug`、 `/debug+`、または`/debug:full`プログラムの出力ファイルをデバッグすることはできません。  
  
 既定では、デバッグ情報は出力されません (`/debug-`)。 デバッグ情報を生成するには指定`/debug`または`/debug+`です。  
  
 アプリケーションのデバッグ パフォーマンスを構成する方法については、「[イメージのデバッグの簡略化](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md)」を参照してください。  
  
|Visual Studio で/debug を設定するには、統合開発環境|  
|---|  
|1.**ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]**をクリックします。 <br />2.**[コンパイル]** タブをクリックします。<br />3.**[詳細コンパイル オプション]** をクリックします。<br />4.値を変更、**デバッグ情報の生成**ボックス。|  
  
## <a name="example"></a>例  
 次の例は、デバッグ情報を出力ファイルに入れ`App.exe`です。  
  
```  
vbc /debug /out:app.exe test.vb  
```  
  
## <a name="see-also"></a>参照  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
