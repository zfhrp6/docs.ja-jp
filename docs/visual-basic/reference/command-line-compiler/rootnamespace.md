---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60cd661fe321c7bc3346f4d20e373240d6c35b5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653161"
---
# <a name="-rootnamespace"></a>-rootnamespace
すべての型宣言に対して名前空間を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`namespace`|現在のプロジェクトのすべての型宣言を囲む名前空間の名前。|  
  
## <a name="remarks"></a>コメント  
 使用して、Visual Studio 統合開発環境で作成されたプロジェクトをコンパイルする Visual Studio の実行可能ファイル (Devenv.exe) を使用する場合`-rootnamespace`の値を指定する、<xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A>プロパティです。 参照してください[Devenv コマンド ライン スイッチ](/visualstudio/ide/reference/devenv-command-line-switches)詳細についてはします。  
  
 共通言語ランタイム MSIL 逆アセンブラーを使用して (`Ildasm.exe`) を出力ファイルの名前空間の名前を表示します。  
  
|Visual Studio 統合開発環境で-rootnamespace を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2.**[アプリケーション]** タブをクリックします。<br />3.値を変更、**ルート Namespace**ボックス。|  
  
## <a name="example"></a>例  
 次のコードのコンパイル`In.vb`名前空間のすべての型宣言を囲むおよび`mynamespace`です。  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Ildasm.exe (IL 逆アセンブラー)](https://msdn.microsoft.com/library/f7dy01k1)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
