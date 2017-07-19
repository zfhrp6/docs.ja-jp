---
title: "方法: シングルファイル アセンブリをビルドする | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
caps.latest.revision: 10
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0ddf25f1d588c0972381a54ee0da4b35e3c0dc33
ms.contentlocale: ja-jp
ms.lasthandoff: 06/02/2017

---
# <a name="how-to-build-a-single-file-assembly"></a>方法: シングルファイル アセンブリをビルドする
アセンブリの最も単純な形式であるシングルファイル アセンブリには、型の情報、実装、[アセンブリ マニフェスト](../../../docs/framework/app-domains/assembly-manifest.md)が含まれています。 コマンド ライン コンパイラや [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] を利用し、シングルファイル アセンブリを作成できます。 既定では、コンパイラは .exe 拡張子でアセンブリ ファイルを作成します。  
  
> [!NOTE]
> C# と Visual Basic の  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] は、シングルファイル アセンブリの作成にのみ使用できます。 マルチファイル アセンブリを作成する場合は、コマンド ライン コンパイラまたは [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] for Visual C++ を使用する必要があります。  
  
 次の手順は、コマンド ライン コンパイラでシングルファイル アセンブリを作成する方法です。  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a>拡張子が .exe のアセンブリを作成するには  
  
1.  コマンド プロンプトに次のコマンドを入力します。  
  
     \<*コンパイラ コマンド*> \<*モジュール名*>  
  
     このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンドで、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。  
  
 次の例では、`myCode` という名前のコード モジュールから `myCode.exe` という名前のアセンブリが作成されます。  
  
```csharp  
csc myCode.cs  
```  
  
```vb  
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>拡張子が .exe のアセンブリを作成し、出力ファイル名を指定するには  
  
1.  コマンド プロンプトに次のコマンドを入力します。  
  
     \<*コンパイラ コマンド*> **/out:**\<*ファイル名*> \<*モジュール名*>  
  
     このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンド、*ファイル名*は出力ファイル名、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。  
  
 次の例では、`myCode` という名前のコード モジュールから `myAssembly.exe` という名前のアセンブリが作成されます。  
  
```csharp  
csc /out:myAssembly.exe myCode.cs  
```  
  
```vb  
vbc /out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a>ライブラリ アセンブリを作成する  
 ライブラリ アセンブリはクラス ライブラリに似ています。 他のアセンブリにより参照される型が含まれますが、実行を開始するためのエントリ ポイントがありません。  
  
#### <a name="to-create-a-library-assembly"></a>ライブラリ アセンブリを作成するには  
  
1.  コマンド プロンプトに次のコマンドを入力します。  
  
     \<*コンパイラ コマンド*> **/t:library** \<*モジュール名*>  
  
     このコマンドでは、*コンパイラ コマンド*はお使いのコード モジュールで使用されている言語のコンパイラ コマンドで、*モジュール名*はアセンブリにコンパイルするコード モジュールの名前です。 **/out:** オプションなど、他のコンパイラ オプションも使用できます。  
  
 次の例では、`myCode` という名前のコード モジュールから `myCodeAssembly.dll` という名前のライブラリ アセンブリが作成されます。  
  
```csharp  
csc /out:myCodeLibrary.dll /t:library myCode.cs  
```  
  
```vb  
vbc /out:myCodeLibrary.dll /t:library myCode.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [アセンブリの作成](../../../docs/framework/app-domains/create-assemblies.md)   
 [マルチファイル アセンブリ](../../../docs/framework/app-domains/multifile-assemblies.md)   
 [方法: マルチファイル アセンブリをビルドする](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)   
 [アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)
