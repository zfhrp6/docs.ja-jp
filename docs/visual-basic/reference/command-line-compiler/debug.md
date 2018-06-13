---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18d74b8f0a7b319e08780a8db9175c7be16d932e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654149"
---
# <a name="-debug-visual-basic"></a>デバッグ (Visual Basic)
コンパイラがデバッグ情報が生成され、出力ファイルに配置します。  
  
## <a name="syntax"></a>構文  
  
```  
-debug[+ | -]  
' -or-  
-debug:[full | pdbonly]  
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
  
|Set - には、Visual Studio 統合開発環境でデバッグします。|  
|---|  
|1.**ソリューション エクスプ ローラー**でプロジェクトを選択し、 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[コンパイル]** タブをクリックします。<br />3.**[詳細コンパイル オプション]** をクリックします。<br />4.値を変更、**デバッグ情報の生成**ボックス。|  
  
## <a name="example"></a>例  
 次の例は、デバッグ情報を出力ファイルに入れ`App.exe`です。  
  
```  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
