---
title: "方法: シングルファイル アセンブリをビルドする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アセンブリ [.NET Framework], 単一ファイル"
  - "アセンブリ マニフェスト, シングルファイル アセンブリ"
  - "コード モジュール"
  - "コマンド ライン コンパイラ"
  - "ライブラリ アセンブリ"
  - "出力ファイル名 (アセンブリの)"
  - "シングルファイル アセンブリ"
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法: シングルファイル アセンブリをビルドする
シングルファイル アセンブリは最も単純な種類のアセンブリであり、[アセンブリ マニフェスト](../../../docs/framework/app-domains/assembly-manifest.md)と同様に型情報と実装を格納します。  コマンド ライン コンパイラまたは [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] を使用して、シングルファイル アセンブリを作成できます。  既定では、コンパイラは .exe 拡張子の付いたアセンブリ ファイルを作成します。  
  
> [!NOTE]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for C\# および Visual Basic はシングルファイル アセンブリの作成にしか使用できません。  マルチファイル アセンブリを作成する場合は、コマンド ライン コンパイラまたは [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C\+\+ を使用する必要があります。  
  
 コマンド ライン コンパイラを使用してシングルファイル アセンブリを作成する手順を次に示します。  
  
### .exe 拡張子の付いたアセンブリを作成するには  
  
1.  コマンド プロンプトに次のコマンドを入力します。  
  
     \<*コンパイラ コマンドの*\>  \<*モジュール名*\>  
  
     このコマンドでは、*compiler command* はコード モジュールで使用する言語のコンパイラ コマンドです。*module name* は、コンパイルしてアセンブリを生成するコード モジュールの名前です。  
  
 コード モジュール `myCode` からアセンブリ `myCode.exe` を作成する例を次に示します。  
  
```csharp  
csc myCode.cs  
```  
  
```vb  
vbc myCode.vb  
```  
  
#### .exe 拡張子を持つアセンブリを作成し、出力ファイル名を指定するには  
  
1.  コマンド プロンプトに次のコマンドを入力します。  
  
     \<*コンパイラ コマンドの*\>**\/out:**の\<*ファイル名の*\>  \<*モジュール名*\>  
  
     このコマンドで、*compiler command* はコード モジュールで使用する言語のコンパイラ コマンドです。*file name* は出力ファイル名です。*module name* はコンパイルしてアセンブリを生成するコード モジュールの名前です。  
  
 コード モジュール `myCode` からアセンブリ `myAssembly.exe` を作成する例を次に示します。  
  
```csharp  
csc /out:myAssembly.exe myCode.cs  
```  
  
```vb  
vbc /out:myAssembly.exe myCode.vb  
```  
  
## ライブラリ アセンブリの作成  
 ライブラリ アセンブリは、クラス ライブラリに類似しています。  ライブラリ アセンブリには、他のアセンブリが参照する型が格納されますが、実行を開始するためのエントリ ポイントは含まれません。  
  
#### ライブラリ アセンブリを作成するには、次のようにします。  
  
1.  コマンド プロンプトに次のコマンドを入力します。  
  
     \<*コンパイラ コマンドの*\>**\/t:library** の \<*モジュール名*\>  
  
     このコマンドでは、*compiler command* はコード モジュールで使用する言語のコンパイラ コマンドです。*module name* は、コンパイルしてアセンブリを生成するコード モジュールの名前です。  **\/out:** オプションなどのほかのコンパイラ オプションも使用できます。  
  
 コード モジュール `myCode` からライブラリ アセンブリ `myCodeAssembly.dll` を作成する例を次に示します。  
  
```csharp  
csc /out:myCodeLibrary.dll /t:library myCode.cs  
```  
  
```vb  
vbc /out:myCodeLibrary.dll /t:library myCode.vb  
```  
  
## 参照  
 [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)   
 [マルチファイル アセンブリ](../../../docs/framework/app-domains/multifile-assemblies.md)   
 [方法 : マルチファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)   
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)