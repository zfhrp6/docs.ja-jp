---
title: "/target (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "target compiler options [Visual Basic]"
  - "-target compiler options [Visual Basic]"
  - "/target compiler options [Visual Basic]"
ms.assetid: e0954147-548b-461f-9c4b-a8f88845616c
caps.latest.revision: 29
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 29
---
# /target (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

コンパイラの出力形式を指定します。  
  
## 構文  
  
```  
/target:{exe | library | module | winexe | appcontainerexe | winmdobj}  
```  
  
## 解説  
 次の表に、`/target` オプションの働きをまとめます。  
  
|**オプション**|**\[動作\]**|  
|---------------|----------------|  
|`/target:exe`|実行可能なコンソール アプリケーションをコンパイラで作成します。<br /><br /> `/target` オプションを指定しなかった場合の既定のオプションです。  拡張子 .exe を使って実行可能ファイルが作成されます。<br /><br /> `/out` オプションで特に指定しない限り、出力ファイル名は `Sub Main` プロシージャを含む入力ファイルの名前と同じになります。<br /><br /> .exe ファイルを生成するためにコンパイルするソース コード ファイルで必要な `Sub Main` プロシージャは 1 つだけです。  `/main` コンパイラ オプションを使用して、`Sub Main` プロシージャを含むクラスを指定します。|  
|`/target:library`|コンパイラにダイナミック リンク ライブラリ \(DLL\) を作成させます。<br /><br /> 拡張子が .dll であるダイナミック リンク ライブラリ ファイルが作成されます。<br /><br /> `/out` オプションで特に指定しない限り、出力ファイル名は最初の入力ファイルと同じになります。<br /><br /> DLL の作成には、`Sub Main` プロシージャは不要です。|  
|`/target:module`|アセンブリに追加できるモジュールをコンパイラで生成します。<br /><br /> 出力ファイルの拡張子は .  netmodule になります。<br /><br /> .NET の共通言語ランタイムは、アセンブリのないファイルを読み込むことができません。  ただし、アセンブリがないファイルでも、`/reference` を使用してアセンブリのアセンブリ マニフェストに組み込むことができます。<br /><br /> あるモジュールのコードが別のモジュールの内部型を参照する場合は、`/reference` を使用して両方のモジュールをアセンブリ マニフェストに組み込む必要があります。<br /><br /> [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) は、モジュールからメタデータをインポートします。|  
|`/target:winexe`|実行可能な Windows ベースのアプリケーションをコンパイラで作成します。<br /><br /> 拡張子 .exe を使って実行可能ファイルが作成されます。  Windows ベースのアプリケーションは、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] クラス ライブラリまたは Win32 API のユーザー インターフェイスを提供するプログラムです。<br /><br /> `/out` オプションで特に指定しない限り、出力ファイル名は `Sub Main` プロシージャを含む入力ファイルの名前と同じになります。<br /><br /> .exe ファイルを生成するためにコンパイルするソース コード ファイルで必要な `Sub Main` プロシージャは 1 つだけです。  コード内に `Sub Main` プロシージャを持つクラスが複数ある場合、`/main` コンパイラ オプションを使用して、どのクラスに `Sub Main` プロシージャが含まれているかを指定します。|  
|`/target:appcontainerexe`|コンパイラをアプリ コンテナーで実行する実行可能な Windows ベースのアプリケーションを作成します。  この設定は [!INCLUDE[win8_appname_long](../../../csharp/includes/win8-appname-long-md.md)] のアプリケーションで使用するように設計されています。<br /><br /> セットを設定 **appcontainerexe** ファイル [ポータブル実行可能](http://go.microsoft.com/fwlink/p/?LinkId=236960) 特性のフィールドのビット。  このビットは、アプリケーションがアプリ コンテナーで実行する必要があることを示します。  このビットが設定されている場合、エラーが `CreateProcess` のメソッドがアプリ コンテナーの外部でアプリケーションを起動しようとすると発生します。  このビットの設定は、別として、**\/target:appcontainerexe** は **\/target:winexe**と同じです。<br /><br /> 拡張子 .exe を使って実行可能ファイルが作成されます。<br /><br /> `/out` のオプションを使用して、特に指定しない限り、出力ファイル名は `Sub Main` のプロシージャを含む入力ファイルと同じになります。<br /><br /> .exe ファイルを生成するためにコンパイルするソース コード ファイルで必要な `Sub Main` プロシージャは 1 つだけです。  コードが `Sub Main` のプロシージャを持つ複数のクラスが含まれている場合、どのクラスの `Sub Main` のプロシージャを含むかを指定する `/main` のコンパイラ オプションを使用します。|  
|`/target:winmdobj`|コンパイラが、Windows にランタイムのバイナリ \(.winmd\) ファイルを変換する中間ファイルを作成します。  .winmd ファイルは、マネージ言語のプログラムでなく JavaScript および C\+\+ プログラムによって実行できます。<br /><br /> 中間ファイルは、.winmdobj の拡張子で作成されます。<br /><br /> `/out` のオプションを使用して、特に指定しない限り、出力ファイル名は、最初の入力ファイルと同じになります。  `Sub Main` の手順は必要ではありません。<br /><br /> .winmdobj のファイルが使用されるように <xref:Microsoft.Build.Tasks.WinMDExp> のエクスポートのツールが Windows のメタデータの \(WinMD\) ファイルを生成できるように、入力として設計されています。  WinMD ファイルは .winmd の拡張子を持ち、元のライブラリの JavaScript コードと、C\+\+、および Windows のランタイムを使用 WinMD の定義の両方が含まれます。|  
  
 `/target:module` を指定しない限り、`/target` を使用すると、[!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort-md.md)] のアセンブリ マニフェストが出力ファイルに追加されます。  
  
 Vbc.exe のインスタンスごとに生成される出力ファイルは、多くても 1 つです。  `/out` や `/target` のようなコンパイラ オプションを 2 回以上指定すると、コンパイラが最後に認識したオプションだけが有効になります。  コンパイルされたすべてのファイルに関する情報は、マニフェストに追加されます。  `/target:module` で作成されるファイル以外のすべての出力ファイルでは、マニフェスト内にアセンブリ メタデータが格納されます。  出力ファイルのメタデータを表示するには、[Ildasm.exe \(IL 逆アセンブラー\)](../Topic/Ildasm.exe%20\(IL%20Disassembler\).md) を使用します。  
  
 `/target` の省略形は `/t` です。  
  
### Visual Studio IDE で \/target を設定するには  
  
1.  **ソリューション エクスプローラー**でプロジェクトを選択します。  **\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  詳細については、「[Introduction to the Project Designer](http://msdn.microsoft.com/ja-jp/898dd854-c98d-430c-ba1b-a913ce3c73d7)」を参照してください。  
  
2.  **\[アプリケーション\]** タブをクリックします。  
  
3.  **\[アプリケーションの種類\]** ボックス内の値を変更します。  
  
## 使用例  
 `in.vb` をコンパイルして `in.dll` を作成する場合のコード例です。  
  
```  
vbc /target:library in.vb  
```  
  
## 参照  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [\/out](../../../visual-basic/reference/command-line-compiler/out.md)   
 [\/reference](../../../visual-basic/reference/command-line-compiler/reference.md)   
 [\/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md)   
 [\/moduleassemblyname](../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md)   
 [アセンブリとグローバル アセンブリ キャッシュ](../Topic/Assemblies%20and%20the%20Global%20Assembly%20Cache%20\(C%23%20and%20Visual%20Basic\).md)   
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)