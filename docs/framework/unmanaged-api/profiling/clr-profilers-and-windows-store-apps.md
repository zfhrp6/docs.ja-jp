---
title: "CLR プロファイラーと Windows ストア アプリ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d884b80ba8ccc42d1b6acc671db408305a095a7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="clr-profilers-and-windows-store-apps"></a>CLR プロファイラーと Windows ストア アプリ
このトピックでは、分析する診断ツールの書き込みが Windows ストア アプリ内で実行されているコードを管理する場合について検討する必要がありますについて説明します。  また、Windows ストア アプリに対して実行する、操作を続行するために、既存の開発ツールを変更するガイドラインを示します。  この情報を理解するのには、ツールを変更するスクリプトは Windows デスクトップ アプリケーション、およびするに対して正しく実行、対象となるようになりましたこと診断ツールで、この API を既に使用している場合は、共通言語ランタイム プロファイリング API に慣れている、最適ですWindows ストア アプリに対して正しく実行します。  
  
 このトピックは、次のセクションで構成されています。  
  
 [はじめに](#Intro)  
 [アーキテクチャと用語](#Arch)  
 [Windows RT デバイス](#RT)  
[Windows ランタイム Api の使用](#Consuming)  
[プロファイラー DLL の読み込み](#Loading)  
 [起動時の一般的な考慮事項と読み込みのアタッチ](#Common)  
 [スタートアップ負荷](#Startup)  
 [負荷をアタッチします。](#Attach)  
[Windows ストア アプリ内で実行されています。](#Running)  
 [Windows ストア アプリの Api を](#APIs)  
 [アクセス許可が制限](#Permissions)  
 [プロセス間通信](#Interprocess)  
 [シャット ダウンの通知はありません。](#Shutdown)  
[Windows ランタイム メタデータ ファイル](#Metadata)  
 [マネージ コードと非マネージ Winmd](#WMDs)  
 [WinMD ファイルが CLR モジュールのようになります](#CLRModules)  
 [Winmd からメタデータの読み取り](#Reading)  
 [Winmd からメタデータを変更します。](#Modifying)  
 [Winmd でアセンブリ参照を解決します。](#Resolving)  
[メモリ プロファイラー](#Profilers)  
 [ForceGC マネージ スレッドを作成します。](#ForceGC)  
 [ConditionalWeakTableReferences](#WeakTable)  
[まとめ](#Conclusion)  
[リソース](#Resources)  
  
<a name="Intro"></a>   
## <a name="introduction"></a>はじめに  
 場合は、過去の導入段落、CLR プロファイル API を使い慣れています。  管理対象のデスクトップ アプリケーションに対して適切に動作する診断ツールを既に書き込まれています。  これで、興味の対処、ツールは、管理対象の Windows ストア アプリで動作できるようにします。  おそらく既にしようとしたこの作業を行い、簡単な作業ではないことが検出されます。  実際には、すべてのツール開発者に知られていない可能性がありますの考慮事項の数があります。  例:  
  
-   Windows ストア アプリは、重大な権限のコンテキストで実行します。  
  
-   Windows メタデータ ファイルには、従来のマネージ モジュールと比較して一意の特性があります。  
  
-   Windows ストア アプリでは、対話機能がダウンしたときにそれ自体の中断の習慣があります。  
  
-   プロセス間通信メカニズムは、さまざまな理由で動作しない可能性があります。  
  
 このトピックでは、注意すべき事項およびそれらに適切に対処する方法を示します。  
  
 CLR プロファイル API を初めて場合は、このトピックの最後にリソースをより深く概要情報を検索するまでスキップします。  
  
 特定の Windows Api と使用方法に関する詳細な情報を提供することは、このトピックの内容のスコープ外もです。  このトピックの開始点を検討し、ここで参照されるすべての Windows Api の詳細については、MSDN を参照してください。  
  
<a name="Arch"></a>   
## <a name="architecture-and-terminology"></a>アーキテクチャと用語  
 通常、診断ツールは、次の図のようなアーキテクチャを持ちます。 「プロファイラー、」という用語を使用してが、このような多くのツールには、標準的なパフォーマンスまたはメモリのプロファイリングにコード カバレッジなどの領域に、以外の操作もモック オブジェクト フレームワーク、タイム トラベルの監視、およびなどのアプリケーションのデバッグが参照してください。  わかりやすくするため、このトピックは引き続きプロファイラーとしてこれらすべてのツールを参照してください。  
  
 次の用語は、このトピック全体で使用されます。  
  
 アプリケーション  
 これは、プロファイラーが分析されているアプリケーションです。  通常、このアプリケーションの開発者は、アプリケーションの問題の診断に役立つプロファイラーを使用するがようになりました。  従来、このアプリケーションが、Windows デスクトップ アプリケーションであっても、このトピックの「Windows ストア アプリに求めています。  
  
 プロファイラー DLL  
 これは、分析対象のアプリケーションのプロセス空間に読み込まれるコンポーネントです。  プロファイラーの「エージェント」とも呼ばれる、このコンポーネントを実装して、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)[ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)(2、3 など) インターフェイスおよび消費、 [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)(2、3 など)、分析対象のアプリケーションについて、可能性のあるデータを収集するインターフェイスは、アプリケーションの動作の側面を変更します。  
  
 プロファイラー UI  
 これは、プロファイラーのユーザーが対話するデスクトップ アプリケーションです。  ユーザーにアプリケーションの状態を表示して、分析対象のアプリケーションの動作を制御するための手段をユーザーに提供を行います。  このコンポーネントは、プロファイリング対象アプリケーションのプロセス空間とは別に独自のプロセス空間で常に実行されます。  プロファイラーの UI は、「アタッチ トリガー、」これを呼び出すプロセスとしても機能できます、 [iclrprofiling::attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)分析アプリケーションがこのような場合は、プロファイラー DLL しなかったでプロファイラー DLL を読み込むのメソッド起動時にロードします。  
  
> [!IMPORTANT]
>  プロファイラー UI おく必要がある Windows デスクトップ アプリケーションでは、コントロールと Windows ストア アプリでレポートを使用した場合にもします。  パッケージを Windows ストアに、診断ツールを出荷するのには期待しないでください。  ツールは、Windows ストア アプリが実行できないし、プロファイラーの UI の内部にそれらの問題の多くの作業を行う必要があります。  
  
 サンプル コードには、このドキュメント全体を前提とします。  
  
-   CLR プロファイル API の要件に従って、ネイティブ DLL をする必要がありますので、C++ では、プロファイラー DLL が書き込まれます。  
  
-   プロファイラーの UI には、c# で書き込まれます。  必要に応じて、これはありませんが、プロファイラー UI のプロセスの言語の要件がないため、わかりやすく、シンプルでは言語を選択しないのはなぜですか。  
  
<a name="RT"></a>   
### <a name="windows-rt-devices"></a>Windows RT デバイス  
 Windows RT デバイスがロックされている非常にします。  サード パーティ製プロファイラー単にすることはできませんなどのデバイス上にロードします。  このドキュメントは、Windows 8 Pc について説明します。  
  
<a name="Consuming"></a>   
## <a name="consuming-windows-runtime-apis"></a>Windows ランタイム Api の使用  
 次のセクションで説明したシナリオの多くは、プロファイラー UI デスクトップ アプリケーションをいくつかの新しい Windows ランタイム Api を使用する必要があります。  デスクトップ アプリケーションから使用できるどの Windows ランタイム Api を理解するのには、ドキュメントを参照してくださいにしておくし、かどうかの動作が異なる場合にアプリと呼ばれるデスクトップ アプリケーションと Windows ストアからです。  
  
 場合は、プロファイラーの UI は、マネージ コードで記述された、簡単なそれらの Windows ランタイム Api を使用するために実行する必要があります、いくつかの手順があります。  参照してください、[マネージ デスクトップ アプリと Windows ランタイム](http://go.microsoft.com/fwlink/?LinkID=271858)詳細については資料です。  
  
<a name="Loading"></a>   
## <a name="loading-the-profiler-dll"></a>プロファイラー DLL の読み込み  
 このセクションでは、プロファイラー UI が、プロファイラー DLL を読み込む Windows ストア アプリがどのように発生する方法について説明します。  このセクションで説明したコードは、プロファイラー UI、デスクトップ アプリで属しており、したがっては安全にデスクトップ アプリは Windows ストア アプリの必ずしも安全でない Windows Api を使用してが含まれます。  
  
 プロファイラー UI には、プロファイラー DLL の 2 つの方法で、アプリケーションのプロセス空間に読み込まれる可能性があります。  
  
-   アプリケーションの起動時、環境変数によって制御されるためです。  
  
-   呼び出すことによって起動が完了した後、アプリケーションにアタッチすることにより、 [iclrprofiling::attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)メソッドです。  
  
 スタートアップ ロード テストと Windows ストア アプリで正しく動作する、プロファイラー DLL のアタッチ読み込み、最初の障害のいずれかが取得されます。  読み込みの両方の形式は、特別な考慮事項を共通の共有で始めます。  
  
<a name="Common"></a>   
### <a name="common-considerations-for-startup-and-attach-loads"></a>起動時の一般的な考慮事項と読み込みのアタッチ  
 **プロファイラー DLL の署名**  
 Windows では、プロファイラー DLL をロードしようとして、プロファイラー DLL が正しく署名されていることを確認します。  ない場合は、既定では、読み込みに失敗します。 これには、2 つの方法があります。  
  
-   プロファイラー DLL が署名されていることを確認します。  
  
-   インストールが必要、開発者用ライセンスの Windows 8 コンピューターで、ツールを使用する前に、ユーザーに通知します。  これは、ために自動的に Visual Studio から、またはコマンド プロンプトから手動でします。  詳細については、次を参照してください。[開発者用ライセンスを取得](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)です。  
  
 **ファイル システム権限**  
 Windows ストア アプリの読み込みおよび格納されているファイル システム上の場所から、プロファイラー DLL を実行するアクセス許可が必要です。  既定では、Windows ストア アプリでは、ほとんどのディレクトリでこのようなアクセス許可がないし、プロファイラー DLL の読み込みに失敗したしようとすると、Windows アプリケーション イベント ログにこのようなエントリが生成されます。  
  
```Output  
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].  
```  
  
 一般に、Windows ストア アプリは限られた、ディスク上の場所にアクセス許可のみです。  各 Windows ストア アプリは、すべての Windows ストア アプリがアクセスを許可、ファイル システム内の他のいくつかの領域と同様に、独自のアプリケーション データ フォルダーにアクセスできます。  すべての Windows ストア アプリが読み取られますが、既定では実行アクセス許可があるため、プロファイラー DLL とその依存関係の Program Files または Program Files (x86)、下にある任意の場所をインストールすることをお勧めします。  
  
<a name="Startup"></a>   
### <a name="startup-load"></a>スタートアップ負荷  
 通常、デスクトップ アプリでプロファイラー UI にメッセージが表示されます、プロファイラー DLL の起動ロード必要な CLR プロファイル API 環境変数が含まれる環境ブロックを初期化することによって (つまり、 `COR_PROFILER`、 `COR_ENABLE_PROFILING`、および`COR_PROFILER_PATH`)、およびその環境ブロックで、新しいプロセスを作成します。  Windows ストア アプリの場合は true を保持して、同じがメカニズムが異なります。  
  
 **管理者特権で実行しません。**  
 プロセスを Windows ストア アプリ プロセス B、A のプロセスを起動するときに実行するかどう中程度の整合性にレベル、高い整合性レベル (つまり、昇格したされません) ではなくです。  つまり、いずれかがプロファイラー UI は中程度の整合性レベルで実行されている必要がありますまたは、Windows ストア アプリの起動処理するメディアの整合性レベルで別のデスクトップ プロセスを起動する必要があります。  
  
 **プロファイルへの Windows ストア アプリを選択します。**  
 まず、質問、プロファイラーを起動するには、どの Windows ストア アプリにします。  デスクトップ アプリは、ファイル参照のダイアログ ボックスを表示する場合と、ユーザーが検索して .exe ファイルを選択します。  Windows ストア アプリが異なる場合、し、[参照] ダイアログを使用すると、意味がないためです。  代わりに、ユーザーからを選択するには、そのユーザー用にインストールされた Windows ストア アプリの一覧を表示することをお勧めします。  
  
 使用することができます、 [PackageManager クラス](https://msdn.microsoft.com/library/windows/apps/windows.management.deployment.packagemanager.aspx)をこの一覧を生成します。  `PackageManager`デスクトップ アプリで使用可能な Windows ランタイム クラスは、実際には*のみ*デスクトップ アプリで利用できます。  
  
 C# yses でデスクトップ アプリとして書き込まれる仮定プロファイラー UI から次のコード例、 `PackageManager` Windows アプリの一覧を生成します。  
  
```csharp  
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();  
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();  
PackageManager packageManager = new PackageManager();  
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);  
```  
  
 **カスタムの環境ブロックを指定します。**  
 新しい COM インターフェイス、 [IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)診断の形式によっては簡単にするための Windows ストア アプリの実行動作をカスタマイズすることができます。  そのメソッドのいずれかの[EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=vs.85\).aspx)、開始すると、環境ブロックを Windows ストア アプリに渡すことができますと共に自動処理の中断を無効にするように他の便利な効果。  環境変数を指定する必要があるために、環境ブロックは重要な (`COR_PROFILER`、 `COR_ENABLE_PROFILING`、および`COR_PROFILER_PATH)`)、プロファイラー DLL を読み込むために、CLR で使用します。  
  
 次のコード スニペットを考慮してください。  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, debuggerCommandLine,   
                                                                 (IntPtr)fixedEnvironmentPzz);  
```  
  
 いくつかの項目が、正しく理解する必要があります。  
  
-   `packageFullName`パッケージを反復処理して、取得中に決定できる`package.Id.FullName`です。  
  
-   `debuggerCommandLine`もっと興味深いです。  Windows ストア アプリへのカスタム環境ブロックを渡すために、独自の単純なダミー デバッガーを記述する必要があります。  Windows 産み落とす Windows ストア アプリは中断され、この例でようにコマンドラインを使用して、デバッガーを起動して、デバッガーをアタッチします。  
  
    ```Output  
    MyDummyDebugger.exe -p 1336 -tid 1424  
    ```  
  
     ここで`-p 1336`Windows ストア アプリのプロセス ID 1336、ことを意味し、`-tid 1424`スレッド ID 1424 が中断されているスレッドであることを意味します。  ダミーのデバッガーのコマンドラインから ThreadID を解析は、そのスレッドを再開およびを終了します。  
  
     そのために C++ コードのいくつかの例を次に示します (エラー チェックを追加することを確認する!)。  
  
    ```cpp  
    int wmain(int argc, wchar_t* argv[])  
    {      
        // …  
        // Parse command line here  
        // …  
  
        HANDLE hThread = OpenThread(THREAD_SUSPEND_RESUME,   
                                                                  FALSE /* bInheritHandle */, nThreadID);  
        ResumeThread(hThread);  
        CloseHandle(hThread);  
        return 0;  
    }  
    ```  
  
     診断ツールのインストールの一部としてこのダミー デバッガーを展開し、このデバッガーでへのパスを指定する必要があります、`debuggerCommandLine`パラメーター。  
  
 **Windows ストア アプリを起動します。**  
 Windows ストア アプリを起動する時点が最後に到着しました。 既に既にこれを自分でこれをしようとした場合、お気付きを[CreateProcess](https://msdn.microsoft.com/library/windows/desktop/ms682425\(v=vs.85\).aspx)は Windows ストア アプリのプロセスを作成する方法にありません。  代わりに、使用する必要があります、 [IApplicationActivationManager::ActivateApplication](https://msdn.microsoft.com/library/windows/desktop/Hh706903\(v=vs.85\).aspx)メソッドです。  実行するには、初めて起動する Windows ストア アプリのアプリのユーザー モデル ID を取得する必要があります。  つまり、少し物置マニフェストからを実行する必要があります。  
  
 パッケージを繰り返し処理しているときに (「を選択する、Windows ストア アプリをプロファイル」を参照してください、[スタートアップ ロード](#Startup)前セクション)、現在のパッケージのマニフェストに含まれているアプリケーションのセットを取得します。  
  
```csharp  
string manifestPath = package.InstalledLocation.Path + "\\AppxManifest.xml";  
  
AppxPackaging.IStream manifestStream;  
SHCreateStreamOnFileEx(  
                    manifestPath,  
                    0x00000040,     // STGM_READ | STGM_SHARE_DENY_NONE  
                    0,              // file creation attributes  
                    false,          // fCreate  
                    null,           // reserved  
                    out manifestStream);  
  
IAppxManifestReader manifestReader = appxFactory.CreateManifestReader(manifestStream);  
  
IAppxManifestApplicationsEnumerator appsEnum = manifestReader.GetApplications();  
```  
  
 はい、1 つのパッケージは、複数のアプリケーションを持つことができ、各アプリケーションには、独自のアプリケーション ユーザー モデル ID  したがって、ユーザーに、プロファイルするアプリケーションを確認し、その特定のアプリケーションからのアプリケーション ユーザー モデル ID を取得します。  
  
```csharp  
while (appsEnum.GetHasCurrent() != 0)  
{  
    IAppxManifestApplication app = appsEnum.GetCurrent();  
    string appUserModelId = app.GetAppUserModelId();  
…  
```  
  
 最後に、今すぐ必要がある Windows ストア アプリを起動する必要があります。  
  
```csharp  
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();  
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);  
```  
  
 **DisableDebugging を呼び出す**  
 呼び出されたとき[IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx)、呼び出すことによって自分の後にクリーンアップすると、promise を作成した、 [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx)メソッド、ので、必ずを行うにはプロファイリング セッションが上にします。  
  
<a name="Attach"></a>   
### <a name="attach-load"></a>負荷をアタッチします。  
 使用して、プロファイラーの UI は、プロファイラー DLL を実行して既に開始されているアプリケーションにアタッチする場合、 [iclrprofiling::attachprofiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)です。  同じ Windows ストア アプリを使用した場合は true を保持します。  上記の一般的な考慮事項、に加えてことを確認しますが、対象の Windows ストア アプリは中断されません。  
  
 **EnableDebugging**  
 同様にスタートアップ ロードを呼び出す、 [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx)メソッドです。  環境ブロックを渡す不要でその他の機能の 1 つ必要があります: 自動処理の中断を無効にします。  それ以外の場合、プロファイラー UI を呼び出すと[AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md)対象の Windows ストア アプリを中断する可能性があります。  実際には、この可能性は、ユーザーが、プロファイラー UI と対話するようになりましたし、Windows ストア アプリがユーザーの画面のいずれかでアクティブでない場合。  かどうか、Windows ストア アプリが中断されていることはできませんへ応答とは、CLR がプロファイラー DLL をアタッチするそこに送信を通知します。  
  
 これを行う次のようにします。  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, null /* debuggerCommandLine */,   
                                                                 IntPtr.Zero /* environment */);  
```  
  
 これを実行するようにスタートアップ負荷の場合、デバッガー コマンドラインまたは環境ブロックを指定しない点を除いて、同じ呼び出しです。  
  
 **DisableDebugging**  
 いつものように、忘れずに呼び出す[IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx)プロファイル セッションが完了するとします。  
  
<a name="Running"></a>   
## <a name="running-inside-the-windows-store-app"></a>Windows ストア アプリ内で実行されています。  
 したがって、Windows ストア アプリには、プロファイラー DLL は最後に読み込まれました。  プロファイラー DLL には、Windows ストア アプリで必要な別のルールで再生する方法を学習する必要があります、これで Api は、許容される方法などを実行するアクセス許可に制限します。  
  
<a name="APIs"></a>   
### <a name="stick-to-the-windows-store-app-apis"></a>Windows ストア アプリの Api を  
 Windows API を参照する場合に、すべての API がデスクトップ アプリ、Windows ストア アプリ、またはその両方に適用されているとして記載されていることがわかります。  たとえば、**要件**のドキュメントのセクションで、 [InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx)関数は、関数は、デスクトップ アプリのみに適用されることを示します。 これに対し、 [InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx)機能は、デスクトップ アプリと Windows ストア アプリの両方を使用します。  
  
 プロファイラー DLL を開発するときに扱うことを示す、Windows ストア アプリにある場合と Windows ストア アプリに使用可能と記載されている Api を使用してのみです。  依存関係を分析 (たとえば、実行することができます`link /dump /imports`を監査する、プロファイラー DLL に対して)、依存関係のうち、[ok] はおらず、これを表示するドキュメントを検索します。  Safe として記載されている API の新しい形式で交換するだけで、ほとんどの場合、違反を修正することができます (たとえば、置換[InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx)で[InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx))。  
  
 プロファイラー DLL は、デスクトップ アプリのみに適用されるいくつかの Api を呼び出すし、まだように見えるであっても、プロファイラー DLL が読み込まれるときに Windows ストア アプリ内での作業ことに注意してください可能性があります。  Windows ストア アプリのプロセスに読み込まれるときに、プロファイラー DLL での Windows ストア アプリで使用するために記載されていないすべての API を使用して危険なことに注意してください。  
  
-   このような Api は、Windows ストア アプリで実行された一意のコンテキストで呼び出されたときに動作する保証はありません。  
  
-   別の Windows ストア アプリのプロセス内で呼び出された場合、このような Api が一貫して機能しません可能性があります。  
  
-   このような Api は、現在のバージョンの Windows、Windows ストア アプリから正常に動作するように思えるかもしれませんが分割または将来のリリースの Windows で無効にします。  
  
 すべての違反の修正し、リスクを回避することをお勧めします。  
  
 絶対に特定の API なしで使用できないを Windows ストア アプリ用に適切な代替を見つけることができませんがあります。  このような場合は、最低限。  
  
-   テスト、テスト、その API の使用からリビング daylights をテストします。  
  
-   API の突然が中断または呼び出された場合に表示されなくなりますを理解してから Windows ストア内のアプリ今後のリリースにおける Windows です。  これは、されませんによってと見なされる互換性問題にならなければ、Microsoft との使用をサポートするしても、優先度はされません。  
  
<a name="Permissions"></a>   
### <a name="reduced-permissions"></a>アクセス許可が制限  
 これは、デスクトップ アプリと Windows ストア アプリのアクセス許可は異なる方法をすべて一覧に、このトピックの範囲外です。  確実に動作は異なる、プロファイラー DLL (Windows ストア アプリ、デスクトップ アプリと比較してに読み込まれる) と任意リソースにアクセスしようとするたびにです。  ファイル システムでは、最も一般的な例を示します。  ありますが、いくつかが特定の Windows ストア アプリのアクセスが許可されているディスク上に配置 (を参照してください[ファイル アクセスと権限 (Windows ランタイム アプリ](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx))、および、プロファイラー DLL が下にある同じ制限が適用されます。  コードを徹底的にテストします。  
  
<a name="Interprocess"></a>   
### <a name="inter-process-communication"></a>プロセス間通信  
 図のように、このホワイト ペーパーの先頭に、プロファイラー DLL (Windows ストア アプリのプロセス空間に読み込まれる) が、プロファイラー UI に (別のデスクトップ アプリのプロセス領域で実行されている)、独自のカスタム プロセスの間で通信するために必要があります。通信 (IPC) チャネル。  プロファイラーの UI は、その動作を変更するプロファイラー DLL に信号を送信し、プロファイラー DLL は、分析対象の Windows ストア アプリからデータを処理後のおよびプロファイラーのユーザーに表示するため、プロファイラーの UI に送り返します。  
  
 ほとんどのプロファイラーがこのように動作する必要がありますが Windows ストア アプリに、プロファイラー DLL が読み込まれるときの IPC メカニズムの選択項目がより限定されました。  たとえば、名前付きパイプに含まれない SDK、Windows ストア アプリのため、使用することはできません。  
  
 もちろん、ファイルである限りより限定的にです。  イベントも使用できます。  
  
 **ファイル経由の通信**  
 ほとんどのデータは、ファイルを使用して、プロファイラー DLL プロファイラー UI と可能性があります渡されます。  キーを選択し、プロファイラーの DLL (Windows ストア アプリのコンテキスト) とプロファイラー UI の両方が読み取りがファイルの場所への書き込みアクセス。  たとえば、一時フォルダーのパスは、プロファイラー DLL とプロファイラー UI の両方からアクセスできる場所が、(他の Windows ストア アプリのパッケージからログ情報を隔離) その他の Windows ストア アプリのパッケージにアクセスできません。  
  
 プロファイラーの UI とプロファイラー DLL の両方を判断できましていないこのパス個別にします。  現在のユーザーに対してインストールされているすべてのパッケージを反復処理時に、プロファイラー UI (前のサンプル コードを参照) へのアクセスの取得、`PackageId`クラス、コンピューターをこのスニペットのようなコードの派生元となる一時フォルダーのパス。  (いつものように、エラー チェックを省略すると簡略化のためです。)  
  
```csharp  
// C# code for the Profiler UI.  
ApplicationData appData =  
    ApplicationDataManager.CreateForPackageFamily(  
        packageId.FamilyName);  
  
tempDir = appData.TemporaryFolder.Path;  
```  
  
 その一方で、プロファイラー DLL が基本的に同じ操作で行うことができますより簡単に取得できるか、 [ApplicationData](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.aspx)クラスを使用して、 [ApplicationData.Current](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.current.aspx)プロパティです。  
  
 **イベントを介して通信**  
 プロファイラー UI とプロファイラー DLL の間での単純なシグナリング セマンティクスを実行する場合に、Windows ストア アプリだけでなくデスクトップ アプリ内のイベントを使用することができます。  
  
 プロファイラー DLL だけを呼び出し、 [CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx)任意の名前と名前付きイベントを作成する関数。  例:  
  
```cpp  
// Profiler DLL in Windows Store app (C++).  
CreateEventEx(   
    NULL,  // Not inherited  
    "MyNamedEvent"  
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */  
    EVENT_ALL_ACCESS);  
```  
  
 プロファイラー UI には、Windows ストア アプリの名前空間の下にある名前付きイベントを検索する必要があります。  たとえば、プロファイラー UI を呼び出すことが[CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx)、としてイベント名を指定します。  
  
 `AppContainerNamedObjects\<acSid>\MyNamedEvent`  
  
 `<acSid>`Windows ストア アプリの AppContainer SID です。  このトピックの前のセクションでは、現在のユーザーに対してインストールされているパッケージを繰り返し処理する方法を示しました。  そのサンプル コードから、パッケージ Id を取得できます。  Id を取得したりできます、`<acSid>`には、次のようなコード。  
  
```csharp  
IntPtr acPSID;  
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);  
  
string acSid;  
ConvertSidToStringSid(acPSID, out acSid);  
  
string acDir;  
GetAppContainerFolderPath(acSid, out acDir);  
```  
  
<a name="Shutdown"></a>   
### <a name="no-shutdown-notifications"></a>シャット ダウンの通知はありません。  
 いずれかに依存しないように、プロファイラー DLL、Windows ストア アプリ内の実行中、 [icorprofilercallback::shutdown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)またはでも[DllMain](https://msdn.microsoft.com/library/windows/desktop/ms682583\(v=vs.85\).aspx) (で`DLL_PROCESS_DETACH`) 呼び出しをプロファイラー DLL を通知するにはWindows ストア アプリが終了しています。  実際には、それらが呼び出されないことが予想されます。  従来は、多くのプロファイラー Dll を使ってこれらの通知の便利な場所としてのディスク、ファイルを閉じると、プロファイラー UI などに通知を送信するキャッシュをフラッシュします。プロファイラー DLL は少し異なる方法で編成する必要があります。  
  
 プロファイラー DLL はログ情報をする必要があります。  パフォーマンス上の理由から、可能性があるメモリ内の情報をバッチのバッチが過去のいくつかのしきい値サイズの増大に応じて拡張をディスクにフラッシュします。  まだディスクにフラッシュされていないすべての情報が失われることを前提としています。  これに、しきい値は、慎重に選択して、プロファイラーの UI がプロファイラー DLL によって書き込まれた不完全な情報を処理するセキュリティで保護する必要があることを意味します。  
  
<a name="Metadata"></a>   
## <a name="windows-runtime-metadata-files"></a>Windows ランタイム メタデータ ファイル  
 詳しくは、このドキュメントのスコープ外はファイルは、どのような Windows ランタイム メタデータ (WinMD) です。    このセクションでは、WinMD ファイルが、プロファイラー DLL を分析する Windows ストア アプリによって読み込まれるときに CLR プロファイル API の動作に制限されます。  
  
<a name="WMDs"></a>   
### <a name="managed-and-non-managed-winmds"></a>マネージ コードと非マネージ Winmd  
 開発者は、新しい Windows ランタイム コンポーネント プロジェクトを作成する Visual Studio を使用している場合、そのプロジェクトのビルドは、開発者が作成したメタデータ (クラス、インターフェイスなどの種類の説明) を記述する WinMD ファイルを生成します。  このプロジェクトが c# または VB で記述されたマネージ言語プロジェクトの場合は、それらの型 (開発者のソース コードからコンパイルされているすべての IL が含まれていることを意味) の実装は同じ WinMD ファイルも含まれます。  このようなファイルは、マネージ WinMD ファイルと呼ばれます。  務める興味深い点で、Windows ランタイム メタデータと基になる実装の両方が含まれています。  
  
 これに対し、開発者は、C++ の Windows ランタイム コンポーネント プロジェクトを作成する場合にそのプロジェクトのビルドには、メタデータのみを含む WinMD ファイルが生成されます。 と実装は、別のネイティブ DLL にコンパイルされます。  同様に、Windows SDK に含まれている WinMD ファイルには、Windows の一部として出荷されている個別のネイティブ Dll にコンパイルの実装とメタデータのみが含まれます。  
  
 以下の情報は、両方マネージ Winmd、メタデータと実装を含んでいると非マネージ Winmd メタデータのみを含めるに適用されます。  
  
<a name="CLRModules"></a>   
### <a name="winmd-files-look-like-clr-modules"></a>WinMD ファイルが CLR モジュールのようになります  
 CLR に関する限り、すべての WinMD ファイルはモジュールです。  そのため、CLR プロファイル API は、WinMD ファイルを読み込むときに、プロファイラー DLL とその ModuleIDs とは何か他のマネージ モジュールと同じ方法でように指示します。  
  
 プロファイラー DLL は呼び出すことによって他のモジュールから WinMD ファイルを区別することができます、 [icorprofilerinfo 3::getmoduleinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)メソッドを調べて、`pdwModuleFlags`の出力パラメーター、 [COR_PRF_MODULE_WINDOWS_ランタイム](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)フラグ。  (これは設定 ModuleID WinMD を表す場合にのみ)。  
  
<a name="Reading"></a>   
### <a name="reading-metadata-from-winmds"></a>Winmd からメタデータの読み取り  
 正規のモジュール同様、WinMD ファイルには使用して読み取ることができるメタデータが含まれて、[メタデータ Api](../../../../docs/framework/unmanaged-api/metadata/index.md)です。  ただし、CLR は、WinMD ファイルをプログラムにマネージ コードと WinMD ファイルを使用する開発者がより自然なプログラミングの経験を持つことができますを読み取る際に、.NET Framework の型を Windows ランタイム型をマップします。  これらのマッピングの例については、次を参照してください。 [.NET Framework サポートの Windows ストア アプリおよび Windows ランタイム](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)です。  
  
 ビュー、プロファイラーが表示されます、メタデータ Api を使用する場合: 生の Windows ランタイム ビュー、またはマップされた .NET Framework ビューしますか?  回答: が設定します。  
  
 呼び出すと、 [icorprofilerinfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)メソッドなど、メタデータ インターフェイスを取得する WinMD を[IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)、設定することもできます[ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)で、`dwOpenFlags`パラメーターをこのマッピングをオフにします。  それ以外の場合、既定では、マッピングを有効にするされます。  通常、プロファイラーでは、プロファイラー DLL は、WinMD メタデータ (たとえば、型の名前) から取得する文字列がについてよく理解し、プロファイラーのユーザーに自然に表示されるように、マッピングを有効にするが保持されます。  
  
<a name="Modifying"></a>   
### <a name="modifying-metadata-from-winmds"></a>Winmd からメタデータを変更します。  
 Winmd でメタデータを変更することはサポートされていません。  呼び出す場合は、 [icorprofilerinfo::getmodulemetadata](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) WinMD のメソッド ファイルし、指定[ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)で、`dwOpenFlags`パラメーターなど、書き込み可能なメタデータ インターフェイスを要求または[IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)、 [GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)は失敗します。  これは、(たとえば、assemblyrefs がまたはの新しいメソッドを追加する場合)、インストルメンテーションをサポートするためにメタデータを変更する必要がある IL の書き換えのプロファイラーに特に重要です。  確認するように[COR_PRF_MODULE_WINDOWS_RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md)最初 (前のセクションで説明しています) にし、このようなモジュールに書き込み可能なメタデータ インターフェイスを要求しないようにします。  
  
<a name="Resolving"></a>   
### <a name="resolving-assembly-references-with-winmds"></a>Winmd でアセンブリ参照を解決します。  
 多くのプロファイラーは、インストルメンテーションや型検査を支援するために手動でメタデータの参照を解決する必要があります。  このようなプロファイラーは、これらの参照は標準のアセンブリ参照はまったく異なる方法で解決されるために CLR が Winmd、 をポイントするアセンブリ参照を解決する方法について注意する必要があります。  
  
<a name="Profilers"></a>   
## <a name="memory-profilers"></a>メモリ プロファイラー  
 マネージ ヒープとガベージ コレクターには、Windows ストア アプリおよびデスクトップ アプリで根本的に違いはありません。  ただし、プロファイラーの作成者が認識する必要がある微妙な違いがあります。  
  
<a name="ForceGC"></a>   
### <a name="forcegc-creates-a-managed-thread"></a>ForceGC マネージ スレッドを作成します。  
 プロファイラー DLL で通常を呼び出すから別のスレッドが作成されるメモリのプロファイリングを行うときに、 [ForceGC メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)メソッドです。  これは、何も新しいです。  Windows ストア アプリ内でのガベージ コレクションの処理の動作は、可能性があります、スレッドをマネージ スレッドに変換することにより意外どのような場合がありますが、(たとえば、プロファイリング API スレッド Id をそのスレッドに作成されます)。  
  
 このような影響を理解するのには、CLR プロファイル API で定義されている同期と非同期呼び出しの間の違いを理解する必要があります。 これは、Windows ストア アプリでの非同期呼び出しの概念から大きく異なることに注意してください。  ブログの投稿を参照してください[CORPROF_E_UNSUPPORTED_CALL_SEQUENCE あります](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/)詳細についてはします。  
  
 重要な点は、プロファイラーによって作成されたスレッドで行われた呼び出しが常と見なされる同期、プロファイラー DLL のいずれかの実装の外部からそれらの呼び出しが行われる場合でも[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)メソッドです。  少なくとも、ために使用される場合があります。  これで、CLR がプロファイラーのスレッドのマネージ スレッドにへの呼び出しが原因になって[ForceGC メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)スレッドは、プロファイラーのスレッドと見なされなくことです。  CLR が、そのスレッドの同期対象のより厳格な定義に適用されるよう、— つまりの呼び出しに由来する必要がありますのプロファイラー DLL のいずれかの内側[ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)と同期を修飾するメソッド。  
  
 その結果、実際にしますか。  ほとんど[ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)メソッドのみを同期的に呼び出せる安全されはすぐに失敗するそれ以外の場合。  プロファイラー DLL が再利用する場合は、 [ForceGC メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)プロファイラーで作成されたスレッドで行われた通常他の呼び出しに対してスレッド (たとえば、 [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)、 [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)、または[RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md))、問題が発生する予定です。  など、非同期セーフ関数でも[DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)マネージ スレッドから呼び出された場合の特別な規則です。 (ブログの投稿を参照してください[プロファイラー スタック ウォーク: 基礎以降](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/)詳細についてはします)。  
  
 したがって、ことをお勧めを呼び出して、プロファイラー DLL を作成する任意のスレッド[ForceGC メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)使用する必要があります*のみ*Gc をトリガーし、しの GC コールバックに応答するためにします。  プロファイル API をスタックのサンプリングまたはデタッチなど他のタスクを実行するには呼び出さないでください。  
  
<a name="WeakTable"></a>   
### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences  
 新しい GC コールバックは、.NET Framework 4.5 以降で、 [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)、プロファイラーの情報の詳細を示しています。*依存ハンドル*です。 これらのハンドルは実質的に、GC 有効期間管理を目的として、ターゲット オブジェクトに、ソース オブジェクトから参照を追加します。  依存ハンドルは、何も新しい、され、マネージ コードでプログラミングする場合を使用して、独自の依存ハンドルを作成できている、 <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> Windows 8 および .NET Framework 4.5 する前にクラスです。  
  
 ただし、XAML の Windows ストア アプリの管理されていることを依存ハンドルの頻繁に使用します。  具体的には、CLR にそれらを使用マネージ オブジェクトとアンマネージの Windows ランタイム オブジェクト間の循環参照の管理に役立ちます。  これはにとって重要になるようになりましたよりこれまでメモリ プロファイラー ヒープ グラフのエッジの残りの部分と共に、視覚化できるようにこれらの依存ハンドルに通知するためにあることを意味します。  プロファイラー DLL を使用する必要があります[RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)、 [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)、および[ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)ヒープ グラフの完全なビューを形成するには.  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>まとめ  
 Windows ストア アプリ内で実行されるマネージ コードを分析する CLR プロファイル API を使用することはできます。  実際には、開発中、既存のプロファイラーを実行し、Windows ストア アプリをターゲットにできるように、いくつか特定の変更を加えることがことができます。   プロファイラー UI には、デバッグ モードでの Windows ストア アプリをアクティブ化のため新しい Api を使用する必要があります。  プロファイラー DLL が Windows ストア アプリの該当する Api のみを消費することを確認します。  プロファイラー DLL とプロファイラー UI 間の通信機構は、Windows ストア アプリ用のアクセス許可の制限を意識して Windows ストア アプリ API の制限を念頭に書き込まれます必要があります。  プロファイラー DLL は、CLR が Winmd はどのように処理する方法を認識する必要がありますとなり、ガベージ コレクターの動作はマネージ スレッドに関するさまざまな方法です。  
  
<a name="Resources"></a>   
## <a name="resources"></a>リソース  
 **共通言語ランタイム**  
 -   [CLR プロファイル API リファレンス](../../../../docs/framework/unmanaged-api/profiling/index.md)  
  
-   [CLR メタデータ API リファレンス](../../../../docs/framework/unmanaged-api/metadata/index.md)  
  
 **Windows ランタイムと CLR の相互作用**  
 [Windows ストア アプリおよび Windows ランタイムのための .NET Framework サポート](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
  
 **Windows ストア アプリ**  
 -   [ファイルへのアクセスと権限 (Windows ランタイム アプリ](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)  
  
-   [開発者ライセンスを取得](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)  
  
-   [IPackageDebugSettings インターフェイス](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)  
  
## <a name="see-also"></a>参照  
 [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
