---
title: -ターゲット (Visual Basic)
ms.date: 03/13/2018
helpviewer_keywords:
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4097d82772c24bb0416bcb3f6d48bd1c7f101b95
ms.sourcegitcommit: 2ad7d06f4f469b5d8a5280ac0e0289a81867fc8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2018
ms.locfileid: "35231438"
---
# <a name="-target-visual-basic"></a>-ターゲット (Visual Basic)
コンパイラの出力の形式を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>Remarks  
 次の表の影響、`-target`オプション。  
  
|**オプション**|**動作**|  
|----------------|------------------|  
|`-target:exe`|コンパイラが可能なコンソール アプリケーションを作成します。<br /><br /> これはない場合の既定オプション`-target`オプションを指定します。 拡張子が .exe の実行可能ファイルが作成されます。<br /><br /> それ以外の場合を指定しない限り、`/out`オプション、出力ファイル名は含む入力ファイルの名前、`Sub Main`プロシージャです。<br /><br /> 1 つだけ`Sub Main`.exe ファイルにコンパイルされるソース コード ファイル内のプロシージャが必要です。 使用して、`-main`コンパイラ オプションを指定するクラスが含まれています、`Sub Main`プロシージャです。|  
|`-target:library`|コンパイラでダイナミック リンク ライブラリ (DLL) を作成します。<br /><br /> ダイナミック リンク ライブラリ ファイルは、拡張子が .dll で作成されます。<br /><br /> それ以外の場合を指定しない限り、`-out`オプション、出力ファイル名は、最初の入力ファイルの名前。<br /><br /> DLL を作成するときに、`Sub Main`手順は必要ありません。|  
|`-target:module`|コンパイラがアセンブリに追加できるモジュールを生成します。<br /><br /> .Netmodule の拡張機能では、出力ファイルが作成されます。<br /><br /> .NET 共通言語ランタイムは、アセンブリがないファイルを読み込むことができません。 ただし、組み込むことができます、このようなファイル、アセンブリのアセンブリ マニフェストを使用して`-reference`です。<br /><br /> 使用して両方のモジュールをアセンブリ マニフェストに組み込む必要がありますが 1 つのモジュール内のコードでは、別のモジュールの内部の型を参照、`-reference`です。<br /><br /> [-Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)オプションは、モジュールからメタデータをインポートします。|  
|`-target:winexe`|コンパイラで実行可能ファイルの Windows ベースのアプリケーションを作成します。<br /><br /> 拡張子が .exe の実行可能ファイルが作成されます。 Windows ベースのアプリケーションは、いずれかのいずれかからユーザー インターフェイスを提供する、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]クラス ライブラリまたは Win32 Api を使用します。<br /><br /> それ以外の場合を指定しない限り、`-out`オプション、出力ファイル名は含む入力ファイルの名前、`Sub Main`プロシージャです。<br /><br /> 1 つだけ`Sub Main`.exe ファイルにコンパイルされるソース コード ファイル内のプロシージャが必要です。 内に、コードが 1 つ以上持つクラスである場合、`Sub Main`プロシージャを使用して、`-main`コンパイラ オプションを指定するクラスが含まれています、`Sub Main`プロシージャ|  
|`-target:appcontainerexe`|コンパイラがアプリ コンテナー内で実行する必要が実行可能ファイル、Windows ベース アプリケーションを作成します。 この設定が使用するように設計[!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)]アプリケーションです。<br /><br /> **Appcontainerexe**設定は、ビットの特性 フィールドを設定、[ポータブル実行可能](https://msdn.microsoft.com/library/windows/desktop/ms680547(v=vs.85).aspx?id=19509)ファイル。 このビットは、アプリ コンテナー内で、アプリを実行する必要があることを示します。 このビットが設定されている場合、エラーが発生、`CreateProcess`メソッドはアプリケーション コンテナー外のアプリケーションを起動しようとしています。 このビットを設定する場合を除いて **-/target:appcontainerexe**は等価 **-/target:winexe**です。<br /><br /> 拡張子が .exe の実行可能ファイルが作成されます。<br /><br /> 使用してそれ以外の場合に指定していない限り、`-out`オプション、出力ファイル名は含む入力ファイルの名前、`Sub Main`プロシージャです。<br /><br /> 1 つだけ`Sub Main`.exe ファイルにコンパイルされるソース コード ファイル内のプロシージャが必要です。 コードを持つ 2 つ以上のクラスが含まれるかどうか、`Sub Main`プロシージャを使用して、`-main`コンパイラ オプションを指定するクラスが含まれています、`Sub Main`プロシージャ|  
|`-target:winmdobj`|コンパイラが Windows ランタイムのバイナリ (.winmd) ファイルに変換できる中間ファイルを作成します。 .Winmd ファイルは、マネージ言語プログラムだけでなく、JavaScript および C++ プログラムで使用できます。<br /><br /> .Winmdobj 拡張子を持つ中間ファイルが作成されます。<br /><br /> 使用してそれ以外の場合に指定していない限り、`-out`オプション、出力ファイル名は、最初の入力ファイルの名前。 A`Sub Main`手順は必要ありません。<br /><br /> .Winmdobj ファイルは、入力として使用するように設計された、 <xref:Microsoft.Build.Tasks.WinMDExp> Windows メタデータ (WinMD) ファイルを生成するためにツールをエクスポートします。 WinMD ファイルは、.winmd 拡張子を持ち、その JavaScript、C++、および Windows ランタイムを使用して、元のライブラリおよび WinMD の定義から、コード両方にはが含まれています。|  
  
 指定しない限り`-target:module`、`-target`により、[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]アセンブリ マニフェストを出力ファイルに追加します。  
  
 Vbc.exe の各インスタンスの生成は、多くても 1 つの出力ファイル。 コンパイラ オプションを指定する場合`-out`または`-target`2 回以上、コンパイラのプロセスが有効になる最後の 1 つです。 コンパイルですべてのファイルに関する情報は、マニフェストに追加されます。 すべての出力ファイルで作成されたものを除く`-target:module`マニフェストにアセンブリ メタデータが含まれています。 使用して[Ildasm.exe (IL 逆アセンブラー)](https://msdn.microsoft.com/library/f7dy01k1)出力ファイルにメタデータを表示します。  
  
 `-target` の省略形は `-t` です。  
  
### <a name="to-set--target-in-the-visual-studio-ide"></a>Visual Studio IDE をターゲットに設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。   
  
2.  **[アプリケーション]** タブをクリックします。  
  
3.  値を変更、**アプリケーションの種類**ボックス。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`in.vb`作成、 `in.dll`:  
  
```console
vbc -target:library in.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-main](../../../visual-basic/reference/command-line-compiler/main.md)  
 [-除外 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)  
 [-参照 (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [-addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)  
 [-moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)  
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
