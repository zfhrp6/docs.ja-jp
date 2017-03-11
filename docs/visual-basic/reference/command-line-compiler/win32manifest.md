---
title: "/win32manifest (Visual Basic) | Microsoft Docs"
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
  - "/win32manifest compiler option [Visual Basic]"
  - "win32manifest compiler option [Visual Basic]"
  - "-win32manifest compiler option [Visual Basic]"
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# /win32manifest (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロジェクトの移植可能な実行可能 \(PE\) ファイルに埋め込むユーザー定義の Win32 アプリケーション マニフェスト ファイルを識別します。  
  
## 構文  
  
```  
/win32manifest: fileName  
```  
  
## 引数  
  
|||  
|-|-|  
|語句|定義|  
|`fileName`|カスタム マニフェスト ファイルのパスを指定します。|  
  
## 解説  
 既定では、asInvoker の要求実行レベルを指定するアプリケーション マニフェストが、Visual Basic コンパイラによって埋め込まれます。  このマニフェストは、実行可能ファイルをビルドするフォルダー内に作成されます。Visual Studio を使用する場合、通常この場所は bin\\Debug フォルダーまたは bin\\Release フォルダーになります。  カスタム マニフェストを用意して、たとえば highestAvailable または requireAdministrator の要求実行レベルを指定する場合は、このオプションを使用してファイルの名前を指定します。  
  
> [!NOTE]
>  このオプションと [\/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) オプションは相互に排他的です。  同じコマンド ライン内で両方のオプションを使用すると、ビルド エラーが発生します。  
  
 要求実行レベルを指定するアプリケーション マニフェストのないアプリケーションは、Windows Vista のユーザー アカウント制御機能によってファイルとレジストリが仮想化されます。  仮想化の詳細については、「[Windows Vista の ClickOnce 配置](/visual-studio/deployment/clickonce-deployment-on-windows-vista)」を参照してください。  
  
 アプリケーションが次のいずれかの条件を満たす場合、アプリケーションは仮想化されます。  
  
1.  `/nowin32manifest` オプションを使用し、それ以降のビルド ステップでマニフェストを指定していないか、`/win32resource` オプションを使用して Windows リソース \(.res\) ファイルの一部としてマニフェストを指定していない。  
  
2.  要求実行レベルを指定しないカスタム マニフェストを指定している。  
  
 [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] は既定の .manifest ファイルを作成し、実行可能ファイルと共に debug ディレクトリおよび release ディレクトリに格納します。  既定の app.manifest ファイルは、プロジェクト デザイナーで **\[アプリケーション\]** タブの **\[UAC 設定の表示\]** をクリックして、表示または編集できます。詳細については、「[\[アプリケーション\] ページ \(プロジェクト デザイナー\) \(Visual Basic\)](/visual-studio/ide/reference/application-page-project-designer-visual-basic)」を参照してください。  
  
 アプリケーション マニフェストは、カスタムのビルド後のステップで指定するか、`/nowin32manifest` オプションを使用して Win32 リソース ファイルの一部として指定できます。  Windows Vista でアプリケーションのファイルとレジストリを仮想化する場合にも同じオプションを使用します。  これにより、コンパイラで既定のマニフェストが作成され、PE ファイルに埋め込まれるのを防ぐことができます。  
  
## 使用例  
 Visual Basic コンパイラによって PE に挿入される既定のマニフェストの例を次に示します。  
  
> [!NOTE]
>  コンパイラは、MyApplication.app という名前の通常のアプリケーションを、マニフェスト XML に挿入します。  これは、アプリケーションを Windows Server 2003 Service Pack 3 上で実行するための代替手段になります。  
  
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
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/nowin32manifest](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)