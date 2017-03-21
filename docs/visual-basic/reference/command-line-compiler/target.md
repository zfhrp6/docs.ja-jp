---
title: "/target (Visual Basic) |Microsoft ドキュメント"
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
- target compiler options [Visual Basic]
- -target compiler options [Visual Basic]
- /target compiler options [Visual Basic]
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
caps.latest.revision: 29
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
ms.openlocfilehash: ccdb87188b924303057d5867dccece937defe74d
ms.lasthandoff: 03/13/2017

---
# <a name="target-visual-basic"></a>/target (Visual Basic)
コンパイラの出力形式を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## <a name="remarks"></a>コメント  
 次の表に、影響、 `/target`  オプション。  
  
|**オプション**|**動作**|  
|----------------|------------------|  
|`/target:exe`|コンパイラが、可能なコンソール アプリケーションを作成します。<br /><br /> これはない場合は、既定オプション`/target`オプションを指定します。 拡張子が .exe の実行可能ファイルが作成されます。<br /><br /> それ以外の場合を指定しない限り、`/out`オプション、出力ファイル名を含む入力ファイルの名前を受け取り、`Sub Main`プロシージャです。<br /><br /> 1 つだけ`Sub Main`.exe ファイルにコンパイルされるソース コード ファイル内のプロシージャが必要です。 使用して、`/main`コンパイラ オプションを指定するクラスを含む、`Sub Main`プロシージャです。|  
|`/target:library`|コンパイラがダイナミック リンク ライブラリ (DLL) を作成します。<br /><br /> ダイナミック リンク ライブラリ ファイルは、拡張子が .dll で作成されます。<br /><br /> それ以外の場合を指定しない限り、`/out`オプション、出力ファイル名は最初の入力ファイルの名前。<br /><br /> DLL を作成するときに、`Sub Main`手順は必要ありません。|  
|`/target:module`|コンパイラでアセンブリに追加できるモジュールを生成します。<br /><br /> .Netmodule の拡張子を持つ出力ファイルが作成されます。<br /><br /> .NET 共通言語ランタイムは、アセンブリがないファイルを読み込めませんでした。 ただし、組み込むことができます、このようなファイル、アセンブリのアセンブリ マニフェストを使用して`/reference`します。<br /><br /> 使用して、アセンブリ マニフェストに両方のモジュールを組み込む必要が&1; つのモジュール内のコードでは、別のモジュールの内部型を参照する場合`/reference`します。<br /><br /> [/Addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)オプションは、モジュールからメタデータをインポートします。|  
|`/target:winexe`|コンパイラが実行可能ファイルの Windows ベースのアプリケーションを作成します。<br /><br /> 拡張子が .exe の実行可能ファイルが作成されます。 Windows ベースのアプリケーションは、いずれかのいずれかのユーザー インターフェイスを提供する、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]クラス ライブラリまたは Win32 Api を使用します。<br /><br /> それ以外の場合を指定しない限り、`/out`オプション、出力ファイル名を含む入力ファイルの名前を受け取り、`Sub Main`プロシージャです。<br /><br /> 1 つだけ`Sub Main`.exe ファイルにコンパイルされるソース コード ファイル内のプロシージャが必要です。 内に、コードが&1; つ以上のクラスを持つ場合、`Sub Main`プロシージャを使用して、`/main`コンパイラ オプションを指定するクラスを含む、`Sub Main`プロシージャ|  
|`/target:appcontainerexe`|コンパイラは、実行可能な Windows ベース アプリケーションを作成するアプリ コンテナー内で実行する必要があります。 この設定が使用するように設計[!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)]アプリケーションです。<br /><br /> **Appcontainerexe**設定では、少しの特性 フィールドに、[ポータブル実行可能](http://go.microsoft.com/fwlink/p/?LinkId=236960)ファイルです。 このビットは、アプリがアプリ コンテナー内で実行される必要があることを示します。 場合にエラーが発生したこのビットが設定されている場合、`CreateProcess`メソッドはアプリケーション コンテナーの外部でアプリケーションを起動しようとしています。 このビットを設定するとは別**/target:appcontainerexe**は**/target:winexe**します。<br /><br /> 拡張子が .exe の実行可能ファイルが作成されます。<br /><br /> 使用してそれ以外の場合に指定していない限り、 `/out`  オプションを含む入力ファイルの名前は、出力ファイル名、`Sub Main`プロシージャです。<br /><br /> 1 つだけ`Sub Main`.exe ファイルにコンパイルされるソース コード ファイル内のプロシージャが必要です。 コードには複数のクラスが含まれるかどうか、`Sub Main`プロシージャを使用して、`/main`コンパイラ オプションを指定するクラスを含む、`Sub Main`プロシージャ|  
|`/target:winmdobj`|コンパイラが、Windows ランタイム バイナリ (.winmd) ファイルに変換できる中間ファイルを作成します。 .Winmd ファイルは、マネージ言語プログラムだけでなく JavaScript および C++ プログラムで使用できます。<br /><br /> .Winmdobj 拡張子を持つ中間ファイルが作成されます。<br /><br /> 使用してそれ以外の場合に指定していない限り、`/out`オプション、出力ファイル名は最初の入力ファイルの名前。 A`Sub Main`手順は必要ありません。<br /><br /> .Winmdobj ファイルが入力として使用するように設計、 <xref:Microsoft.Build.Tasks.WinMDExp>Windows メタデータ (WinMD) ファイルを作成するツールをエクスポートします</xref:Microsoft.Build.Tasks.WinMDExp>。 WinMD ファイルは、.winmd 拡張子を持ち、その JavaScript、C++、および、Windows ランタイムで使用する、元のライブラリと WinMD 定義から、コード両方にはが含まれています。|  
  
 指定しない限り`/target:module`、`/target`により、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)]出力ファイルに追加するアセンブリのマニフェスト。  
  
 Vbc.exe の各インスタンスが発生した場合、最大で&1; つの出力ファイル。 コンパイラ オプションを指定する場合は、`/out`または`/target`2 回以上、最後の&1; つは、コンパイラのプロセスを有効にします。 コンパイルですべてのファイルに関する情報は、マニフェストに追加します。 すべての出力ファイルで作成されたものを除く`/target:module`マニフェストでアセンブリ メタデータが含まれます。 使用[Ildasm.exe (IL 逆アセンブラー)](https://msdn.microsoft.com/library/f7dy01k1)出力ファイルにメタデータを表示します。  
  
 短い形式の`/target`は`/t`です。  
  
### <a name="to-set-target-in-the-visual-studio-ide"></a>Visual Studio IDE 内/target:publish を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。 **プロジェクト** メニューのをクリックして**プロパティ**します。 詳細については、「[プロジェクト デザイナーの概要](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **[アプリケーション]** タブをクリックします。  
  
3.  値を変更、**アプリケーションの種類**ボックス。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`in.vb`作成、 `in.dll`:  
  
```  
vbc /target:library in.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [/out (Visual Basic)](../../../visual-basic/reference/command-line-compiler/out.md)   
 [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)   
 [/moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)   
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
