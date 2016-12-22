---
title: "/platform (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/platform"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "platform compiler option [C#]"
  - "-platform compiler option [C#]"
  - "/platform compiler option [C#]"
ms.assetid: c290ff5e-47f4-4a85-9bb3-9c2525b0be04
caps.latest.revision: 46
caps.handback.revision: 46
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /platform (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

アセンブリをどのバージョンの共通言語ランタイム \(CLR: Common Language Runtime\) で実行するかを指定します。  
  
## 構文  
  
```  
/platform:string  
```  
  
#### パラメーター  
 `string`  
 anycpu \(既定\)、anycpu32bitpreferred、ARM、x86、x64、または Itanium。  
  
## 解説  
  
-   **anycpu** \(既定\)、任意のプラットフォームで実行されるアセンブリがコンパイルされます。  このモードを使用すると、64 ビット プロセスとしてアプリケーションの実行可能な限りと 32 ビットに戻る分類できます。  
  
-   **anycpu32bitpreferred** : 任意のプラットフォーム上で実行できるように、アセンブリをコンパイルします。  64 ビット アプリケーションと 32 ビット アプリケーションをサポートするシステムの 32 ビット モードでアプリケーションを実行します。  .NET Framework 4.5 を対象とするプロジェクトでのみ、このオプションを指定できます。  
  
-   **ARM** は RISC コンピューター \(ARM\) の高度なプロセッサを搭載したコンピューターで実行されるアセンブリがコンパイルされます。  
  
-   **x64** : AMD64 または EM64T 命令セットをサポートするコンピューターで 64 ビット共通言語ランタイムにより実行できるように、アセンブリをコンパイルします  
  
-   **x86** は 32 ビットの x86 互換共通言語ランタイムで実行されるアセンブリがコンパイルされます。  
  
-   **Itanium** は Itanium プロセッサ搭載コンピューター上の 64 ビット共通言語ランタイムで実行されるアセンブリがコンパイルされます。  
  
 64 ビットの Windows オペレーティング システムでは次のようになります。  
  
-   **\/platform:x86** でコンパイルされたアセンブリは、WOW64 の制御下にある 32 ビット CLR 上で実行されます。  
  
-   **\/platform:anycpu** でコンパイルされた DLL が読み込まれるのプロセスと同じ CLR 上で実行されます。  
  
-   **\/platform:anycpu** でコンパイルされた実行可能ファイルは 64 ビット CLR 上で実行されます。  
  
-   **\/platform:anycpu32bitpreferred** でコンパイルされた実行可能ファイルは 32 ビット CLR 上で実行されます。  
  
 **anycpu32bitpreferred** の設定は、実行可能ファイル \(.EXE\) ファイルでのみ有効で、.NET Framework 4.5 が必要です。  
  
 64 ビットの Windows オペレーティング システム上で実行されるアプリケーションの開発の詳細については、「[64 ビット アプリケーション](../Topic/64-bit%20Applications.md)」を参照してください。  
  
### Visual Studio 開発環境でこのコンパイラ オプションを設定するには  
  
1.  プロジェクトの **\[プロパティ\]** ページを開きます。  
  
2.  **\[ビルド\]** プロパティ ページをクリックします。  
  
3.  、.NET Framework 4.5 を対象とするかまたは **\[32 ビットを使用\]** チェック ボックスをオフにするプロジェクトの **\[プラットフォーム ターゲット\]** のプロパティを変更します。  
  
 **メモ**  
 **\/platform** は、Visual C\# Express の開発環境では使用できません。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.CSharpProjectConfigurationProperties3.PlatformTarget%2A>」を参照してください。  
  
## 使用例  
 次の例では、アプリケーションでの 64 ビット CLR で 64 ビットの Windows オペレーティング システムで実行する必要があることを指定するために **\/platform** オプションを使用する方法を示します。  
  
```  
csc /platform:anycpu filename.cs  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)