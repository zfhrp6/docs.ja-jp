---
title: "方法: CLR のアクティブ化に関する問題をデバッグする | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "CLR アクティベーション, デバッグ (問題を)"
ms.assetid: 4fe17546-d56e-4344-a930-6d8e4a545914
caps.latest.revision: 5
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法: CLR のアクティブ化に関する問題をデバッグする
正しいバージョンの共通言語ランタイム \(CLR\) を使用してアプリケーションを実行したときに問題が発生した場合は、CLR アクティベーション ログを表示してデバッグできます。  これらのログは、アプリケーションが予期していたバージョンとは異なる CLR バージョンを読み込むか、CLR を全く読み込まない場合のアクティベーションの問題の根本原因を突き止める上で非常に役立ちます。  アプリケーションの CLR が見つからない場合については、「[.NET Framework 初期化エラー: ユーザー エクスペリエンスの管理](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md)」を参照してください。  
  
 CLR アクティベーション ログは、HKEY\_LOCAL\_MACHINE レジストリ キーまたはシステム環境変数を使用してシステム全体で有効にできます。  ログは、レジストリ エントリまたは環境変数が削除されるまで生成されます。  また、ユーザーローカルまたはプロセスローカルの環境変数を使用して、範囲と期間の異なるログを有効にすることもできます。  
  
 CLR アクティベーション ログは、[アセンブリ バインディング ログ](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md)と混同しないようにしてください。これは完全に異なるログです。  
  
## CLR アクティベーション ログを有効にするには  
  
#### レジストリの使用  
  
1.  レジストリ エディターで、HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework \(32 ビット コンピューターの場合\) または HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework フォルダー \(64 ビット コンピューターの場合\) に移動します。  
  
2.  `CLRLoadLogDir` という名前の文字列値を追加し、CLR アクティベーション ログを格納する既存のディレクトリの完全パスに設定します。  
  
 アクティベーション ログは、文字列値を削除するまで有効なままになります。  
  
#### 環境変数の使用  
  
-   `COMPLUS_CLRLoadLogDir` 環境変数を、CLR アクティベーション ログを格納する既存のディレクトリの完全パスを表す文字列に設定します。  
  
     環境変数の設定方法によって、その範囲が以下のように決定されます。  
  
    -   システム レベルで設定した場合、アクティベーション ログは環境変数が削除されるまで、そのコンピューターのすべての .NET Framework アプリケーションで有効になります。  
  
    -   ユーザー レベルで設定した場合、アクティベーション ログは現在のユーザー アカウントのみに対して有効になります。  ログ記録は環境変数が削除されるまで続行します。  
  
    -   CLR を読み込む前にプロセス内から設定した場合、アクティベーション ログはプロセスが終了するまで有効になります。  
  
    -   アプリケーションを実行する前にコマンド プロンプトで設定した場合、アクティベーション ログは、そのコマンド プロンプトから実行されるアプリケーションに対して有効になります。  
  
     たとえば、アクティベーション ログをプロセスレベルのスコープの c:\\clrloadlogs ディレクトリに格納するには、アプリケーションを実行する前に、コマンド プロンプト ウィンドウを開き、次のように入力します。  
  
    ```  
    set COMPLUS_CLRLoadLogDir=c:\clrloadlogs  
    ```  
  
## 使用例  
 CLR アクティベーション ログは、CLR のアクティベーションおよび CLR ホスティング API の使用に関する大量のデータを提供します。  この記事で説明されているように、このデータのほとんどはマイクロソフトにより内部で使用されますが、一部のデータは開発者にも役立ちます。  
  
 ログは、CLR ホスティング API が呼び出された順序で記録されます。  また、コンピューターで検出された、一連のインストール済みランタイムに関する便利なデータも含まれています。  CLR アクティベーション ログ形式自体は文書化されていませんが、CLR のアクティベーションに関する問題を解決する必要のある開発者の役に立つことがあります。  
  
> [!NOTE]
>  アクティベーション ログは、CLR を使用するプロセスが終了するまで開くことができません。  
  
> [!NOTE]
>  CLR アクティベーション ログはローカライズされず、常に英語で生成されます。  
  
 次のアクティベーション ログの例では、最も役に立つ情報が強調表示されており、ログの後に説明されています。  
  
```  
532,205950.367,CLR Loading log for C:\Tests\myapp.exe   
532,205950.367,Log started at 4:26:12 PM on 10/6/2011   
532,205950.367,-----------------------------------   
532,205950.382,FunctionCall: _CorExeMain   
532,205950.382,FunctionCall: ClrCreateInstance, Clsid: {2EBCD49A-1B47-4A61-B13A-4A03701E594B}, Iid: {E2190695-77B2-492E-8E14-C4B3A7FDD593}   
532,205950.382,MethodCall: ICLRMetaHostPolicy::GetRequestedRuntime. Version: (null), Metahost Policy Flags: 0x168, Binary: (null), Iid: {BD39D1D2-BA2F-486A-89B0-B4B0CB466891}   
532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0   
532,205950.382,Input values for ComputeVersionString follow this line   
532,205950.382,-----------------------------------   
532,205950.382,Default Application Name: C:\Tests\myapp.exe   
532,205950.382,IsLegacyBind is: 0   
532,205950.382,IsCapped is 0   
532,205950.382,SkuCheckFlags are 0   
532,205950.382,ShouldEmulateExeLaunch is 0   
532,205950.382,LegacyBindRequired is 0   
532,205950.382,-----------------------------------   
532,205950.382,Parsing config file: C:\Tests\myapp.exe   
532,205950.382,UseLegacyV2RuntimeActivationPolicy is set to 0   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,LegacyFunctionCall: GetFileVersion. Filename: C:\Tests\myapp.exe   
532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727   
532,205950.382,ERROR: Version v2.0.50727 is not present on the machine.   
532,205950.398,SEM_FAILCRITICALERRORS is set to 0   
532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3   
532,205950.398,FunctionCall: RealDllMain. Reason: 0   
532,205950.398,FunctionCall: OnShimDllMainCalled. Reason: 0  
  
```  
  
-   **CLR Loading log** は、マネージ コードを読み込んだプロセスを開始した実行可能ファイルのパスを示します。  これはネイティブ ホストである可能性があります。  
  
    ```  
    532,205950.367,CLR Loading log for C:\Tests\myapp.exe  
  
    ```  
  
-   **Installed Runtime** は、コンピューター上にインストールされている、アクティベーション要求候補である一連の CLR バージョンです。  
  
    ```  
    532,205950.382,Installed Runtime: v4.0.30319. VERSION_ARCHITECTURE: 0  
  
    ```  
  
-   **built with version** は、[ICLRMetaHostPolicy::GetRequestedRuntime](../Topic/ICLRMetaHostPolicy::GetRequestedRuntime%20Method.md) などのメソッドに提供されたバイナリを構築するために使用された CLR のバージョンです。  
  
    ```  
    532,205950.382,C:\Tests\myapp.exe was built with version: v2.0.50727  
  
    ```  
  
-   **feature\-on\-demand installation** は、Windows 8 での .NET Framework 3.5 の有効化に関するものです。   このシナリオの詳細については、「[.NET Framework 初期化エラー: ユーザー エクスペリエンスの管理](../../../docs/framework/deployment/initialization-errors-managing-the-user-experience.md)」を参照してください。  
  
    ```  
    532,205950.398,Launching feature-on-demand installation. CmdLine: C:\Windows\system32\fondue.exe /enable-feature:NetFx3  
  
    ```  
  
## 参照  
 [配置](../../../docs/framework/deployment/net-framework-and-applications.md)   
 [方法 : .NET Framework 4 または 4.5 をサポートするアプリケーションを構成する](../../../docs/framework/migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)