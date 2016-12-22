---
title: "/win32manifest (C# Compiler Options) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/win32manifest"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "/win32manifest compiler option [C#]"
  - "win32manifest compiler option [C#]"
  - "-win32manifest compiler option [C#]"
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# /win32manifest (C# Compiler Options)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

**\/win32manifest** オプションを使用して、プロジェクトの移植可能な実行可能 \(PE: Portable Executable\) ファイルに埋め込むユーザー定義の Win32 アプリケーション マニフェスト ファイルを指定します。  
  
## 構文  
  
```  
/win32manifest: filename  
```  
  
## Arguments  
 `filename`  
 カスタム マニフェスト ファイルの名前と場所。  
  
## 解説  
 既定では、"asInvoker" 要求実行レベルを指定するアプリケーション マニフェストが、[!INCLUDE[csharp_current_short](../../../csharp/language-reference/compiler-options/includes/csharp_current_short_md.md)] コンパイラによって埋め込まれます。Visual Studio を使用すると、アプリケーション マニフェストは、通常 bin\\Debug または bin\\Release フォルダーは、実行可能ファイルをビルドするフォルダー内に作成します。  カスタム マニフェストを指定する場合は、「highestAvailable」または「requireAdministrator の要求実行レベルを指定するには」、ファイルの名前を指定するには、このオプションを使用します。  
  
> [!NOTE]
>  このオプションと [\/win32res \(Import a Win32 Resource File\)](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) オプションは相互に排他的です。  同じコマンド ライン内で両方のオプションを使用すると、ビルド エラーが発生します。  
  
 要求実行レベルを指定するアプリケーション マニフェストのないアプリケーションは、Windows Vista のユーザー アカウント制御機能によってファイルとレジストリが仮想化されます。  仮想化の詳細については、参照します [Windows Vista の Developer Story: User Account Control \(UAC\) の Windows Vista Application Development Requirements](http://go.microsoft.com/fwlink/?LinkId=95452)。  
  
 アプリケーションが次のいずれかの条件を満たす場合、アプリケーションは仮想化されます。  
  
-   **\/nowin32manifest** オプションを使用し、それ以降のビルド ステップでマニフェストを指定していないか、**\/win32res** オプションを使用して Windows リソース \(.res\) ファイルの一部としてマニフェストを指定していない。  
  
-   要求実行レベルを指定しないカスタム マニフェストを指定している。  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] は既定の .manifest ファイルを作成し、実行可能ファイルと共に debug ディレクトリおよび release ディレクトリに格納します。  カスタム マニフェストは、任意のテキスト エディターで作成してプロジェクトに追加できます。  または、**ソリューション エクスプローラー**で **\[プロジェクト\]** アイコンを右クリックし、**\[新しい項目の追加\]** をクリックして、**\[アプリケーション一覧ファイル\]** をクリックします。  新しいマニフェスト ファイルまたは既存のマニフェスト ファイルを追加すると、**\[マニフェスト\]** ボックスの一覧にそのファイルが表示されます。  詳細については、「[\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(C\#\)](../Topic/Application%20Page,%20Project%20Designer%20\(C%23\).md)」を参照してください。  
  
 アプリケーション マニフェストは、カスタムのビルド後のステップで指定するか、[\/nowin32manifest \(No Win32 Manifest\)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md) オプションを使用して Win32 リソース ファイルの一部として指定できます。  Windows Vista でアプリケーションのファイルとレジストリを仮想化する場合にも同じオプションを使用します。  これにより、コンパイラで既定のマニフェストが作成され、移植可能な実行可能 \(PE\) ファイルに埋め込まれるのを防ぐことができます。  
  
## 使用例  
 Visual C\# コンパイラによって PE に挿入される既定のマニフェストの例を次に示します。  
  
> [!NOTE]
>  コンパイラは、"MyApplication.app" という名前の通常のアプリケーションを xml に挿入します。  これは、アプリケーションを Windows Server 2003 Service Pack 3 上で実行するための代替手段になります。  
  
```  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## 参照  
 [C\# Compiler Options](../../../csharp/language-reference/compiler-options/index.md)   
 [\/nowin32manifest \(No Win32 Manifest\)](../../../csharp/language-reference/compiler-options/nowin32manifest-compiler-option.md)   
 [方法 : プロジェクト プロパティおよび構成設定を変更する](http://msdn.microsoft.com/ja-jp/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)