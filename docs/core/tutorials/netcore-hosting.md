---
title: .NET Core のホスティング
description: ネイティブ コードから .NET Core ランタイムをホスティングする
author: mjrousos
ms.author: mairaw
ms.date: 2/3/2017
ms.openlocfilehash: 96f51c8480bf75b1d7f824a8c87d2cdd6c7f9dd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218607"
---
# <a name="hosting-net-core"></a>.NET Core のホスティング

あらゆるマネージ コードと同様に、.NET Core アプリケーションはホストにより実行されます。 ホストは、ランタイム (JIT やガベージ コレクターのようなコンポーネントを含む) の開始、AppDomain の作成、マネージ エントリ ポイントの呼び出しを担当します。

.NET Core ランタイムのホスティングは高度なシナリオです。ほとんどの場合、.NET Core 開発者はホスティングについて心配する必要がありません。 .NET Core ビルド プロセスが .NET Core アプリケーションを実行するための既定ホストを提供するためです。 ただし、特別な状況で、ネイティブ プロセスのマネージ コードを呼び出す手段として、あるいはランタイムの動作をさらに細かくコントロールする目的で .NET Core ランタイムを明示的にホスティングすると効果的な場合があります。

この記事では、ネイティブ コードから .NET Core ランタイムを開始し、最初のアプリケーション ドメイン (<xref:System.AppDomain>) を作成し、その中でマネージ コードを実行するために必要な手順について説明します。

## <a name="prerequisites"></a>必須コンポーネント

ホストはネイティブ アプリケーションであるため、このチュートリアルでは、C++ アプリケーションを構築して .NET Core をホスティングする方法について説明します。 C++ 開発環境が必要になります ([Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) に付属のものなど)。

ホストをテストするための単純な .NET Core アプリケーションも必要です。そのため、[.NET Core SDK](https://www.microsoft.com/net/core) をインストールし、[小さい .NET Core テスト アプリを作成](../../core/tutorials/with-visual-studio.md)してください ('Hello World' アプリなど)。 新しい .NET Core コンソール プロジェクト テンプレートで作成される 'Hello World' アプリで十分です。

このチュートリアルとその関連サンプルでは Windows ホストを作成します。Unix のホスティングについては、この記事の終わりにある注記を参照してください。

## <a name="creating-the-host"></a>ホストを作成する

dotnet/samples GitHub リポジトリには、この記事で説明する手順を実演する[サンプル ホスト](https://github.com/dotnet/samples/tree/master/core/hosting)があります。 サンプルの *host.cpp* ファイルにあるコメントを見れば、このチュートリアルで番号が付けられている手順がサンプルのどこで実行されるかわかります。 ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。

サンプル ホストは学習目的のために利用されるものです。エラーのチェック時に軽くなっており、効率性より読みやすさを重視して設計されています。 より実際的なホスト サンプルは [dotnet/coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts) リポジトリにあります。 特に、[CoreRun ホスト](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun)は、単純なサンプルを読んだ後に学習するのに最適な汎用ホストです。

### <a name="a-note-about-mscoreeh"></a>mscoree.h に関する注記
プライマリ .NET Core ホスティング インターフェイス (`ICLRRuntimeHost2`) は [MSCOREE.IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL) で設計されます。 ホストで参照する必要がある、このファイルのヘッダー バージョン (mscoree.h) は、[.NET Core ランタイム](https://github.com/dotnet/coreclr/)がビルドされるときに MIDL 経由で生成されます。 .NET Core ランタイムをビルドしない場合、dotnet/coreclr リポジトリの[ビルド済みヘッダー](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc)の mscoree.h を利用することもできます。 [.NET Core ランタイムのビルド手順](https://github.com/dotnet/coreclr#building-the-repository)はその GitHub リポジトリにあります。 

### <a name="step-1---identify-the-managed-entry-point"></a>手順 1 - マネージ エントリ ポイントを特定する
必要なヘッダーを参照した後 ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) や stdio.h など)、.NET Core ホストが最初に行うことは、それが使用するマネージ エントリ ポイントを見つけることです。 その作業は、このサンプル ホストでは、`main` メソッドが実行されるマネージ バイナリのパスとして最初のコマンド ライン引数をホストに渡すことで行われます。

[!code-cpp[NetCoreHost#1](../../../samples/core/hosting/host.cpp#1)]

### <a name="step-2---find-and-load-coreclrdll"></a>手順 2 - CoreCLR.dll を見つけて読み込む
.NET Core ランタイム API は *CoreCLR.dll* にあります (Windows)。 ホスティング インターフェイス (`ICLRRuntimeHost2`) を取得するには、*CoreCLR.dll* を見つけて読み込む必要があります。 *CoreCLR.dll* の見つけ方を定義するのはホストです。 一部のホストは、コンピューター全体の既知の場所にこのファイルがあるものと予測します (%programfiles%\dotnet\shared\Microsoft.NETCore.App\1.1.0 など)。 他のホストは、ホスト自体またはホスティングするアプリの隣にある場所から *CoreCLR.dll* を読み込むものと予測します。 環境変数を参照してライブラリを見つける場合もあります。

Linux または Mac の場合、コア ランタイム ライブラリはそれぞれ、*libcoreclr.so* と *libcoreclr.dylib* です。

このサンプル ホストでは、いくつかの一般的な場所で *CoreCLR.dll* を探します。 見つかると、`LoadLibrary` (Linux/Mac の場合は `dlopen`) 経由で読み込まれます。

[!code-cpp[NetCoreHost#2](../../../samples/core/hosting/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost2-instance"></a>手順 3 - ICLRRuntimeHost2 インスタンスを取得する
`ICLRRuntimeHost2` ホスティング インターフェイスは、`GetCLRRuntimeHost` で `GetProcAddress` を呼び出し (Linux/Mac の場合は `dlsym`)、その関数を実行することで取得されます。 

[!code-cpp[NetCoreHost#3](../../../samples/core/hosting/host.cpp#3)]

### <a name="step-4---setting-startup-flags-and-starting-the-runtime"></a>手順 4 - スタートアップ フラグを設定し、ランタイムを開始する
`ICLRRuntimeHost2` が用意されたので、ランタイム全体のスタートアップ フラグを指定し、ランタイムを開始できます。 スタートアップ フラグは、使用するガベージ コレクター (GC) (同時実行またはサーバー)、シングル AppDomain とマルチ AppDomain のいずれを使用するのか、使用するローダー最適化ポリシー (アセンブリのドメイン中立読み込み用) を決定します。

[!code-cpp[NetCoreHost#4](../../../samples/core/hosting/host.cpp#4)]

ランタイムは `Start` 関数を呼び出すことで開始されます。

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>手順 5 - AppDomain 設定を準備する
ランタイムが開始したら、AppDomain を設定します。 ただし、.NET AppDomain を作成するとき、たくさんのオプションを指定する必要があります。それらを最初に用意する必要があります。

AppDomain フラグは、セキュリティと相互運用に関連する AppDomain 動作を指定します。 以前の Siliverlight ホストはこれらの設定を利用し、ユーザー コードをサンドボックス化していましたが、最新の .NET Core ホストは完全な信頼としてユーザー コードを実行し、相互運用を有効にします。

[!code-cpp[NetCoreHost#5](../../../samples/core/hosting/host.cpp#5)]

使用する AppDomain フラグを決定したら、AppDomain プロパティを定義する必要があります。 プロパティは文字列のキー/値のペアです。 プロパティの多くは、AppDomain がアセンブリを読み込む方法に関連します。

共通 AppDomain プロパティ:

* `TRUSTED_PLATFORM_ASSEMBLIES` これはアセンブリ パスの一覧です (Windows は ';' で、Unix は ':' で区切られています)。これに対して AppDomain は読み込みに優先順位を設定し、完全信頼を与えます (部分信頼ドメインでも)。 .NET Framework シナリオの GAC と同様に、このリストには 'Framework' アセンブリとその他の信頼されるモジュールを含めます。 目的に応じて、このリストの *coreclr.dll* の隣にライブラリが置かれるホストもあれば、ハードコーディングされたマニフェストに信頼されるアセンブリが一覧表示されるホストもあります。
* `APP_PATHS` これは、信頼されるプラットフォーム アセンブリ (TPA) リストでアセンブリが見つからない場合、アセンブリを探すパスのリストです。 これらのパスは、ユーザーのアセンブリが見つかる可能性のある場所です。 サンドボックス化された AppDomain では、これらのパスから読み込まれるアセンブリには部分信頼のみが与えられます。 共通 APP_PATH パスには、ターゲット アプリの読み込み元のパスやユーザー アセットが存在することがわかっているその他の場所があります。
*  `APP_NI_PATHS` このリストは、ネイティブ イメージを探すパスであることを除き、APP_PATHS とよく似ています。
*  `NATIVE_DLL_SEARCH_DIRECTORIES` このプロパティは、p/invoke で呼び出されたネイティブ DLL を探すときにローダーが調べるパスの一覧です。
*  `PLATFORM_RESOURCE_ROOTS` このリストには、(カルチャ固有の下位ディレクトリで) リソース サテライト アセンブリを探すパスが含まれています。
*  `AppDomainCompatSwitch` この文字列は、明示的なターゲット フレームワーク モニカーのないアセンブリに使用する互換性を指定します (アセンブリが実行する対象のフレームワークを示すアセンブリレベルの属性)。 通常、これは `"UseLatestBehaviorWhenTFMNotSpecified"` に設定しますが、以前の Silverlight や Windows Phone の互換性を優先するホストもあります。

この[単純なサンプル ホスト](https://github.com/dotnet/samples/tree/master/core/hosting)では、これらのプロパティは次のように設定されています。

[!code-cpp[NetCoreHost#6](../../../samples/core/hosting/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>手順 6 - AppDomain を作成する
すべての AppDomain フラグとプロパティを用意したら、`ICLRRuntimeHost2::CreateAppDomainWithManager` を利用して AppDomain を設定できます。 この関数は任意で完全修飾アセンブリ名と型の名前を取得し、ドメインの AppDomain マネージャーとして使用します。 AppDomain マネージャーは、AppDomain の一部の動作の制御をホストに許可できます。ホストがユーザー コードを直接呼び出さない場合、マネージ コードを起動するエントリ ポイントを提供することもあります。   

[!code-cpp[NetCoreHost#7](../../../samples/core/hosting/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>手順 7 - マネージ コードを実行する
AppDomain が稼働したら、ホストはマネージ コードを実行できます。 これを行う最も簡単な方法は、`ICLRRuntimeHost2::ExecuteAssembly` を利用してマネージ アセンブリのエントリ ポイント メソッドを呼び出すことです。 この関数は単一ドメインのシナリオでのみ動作します。

[!code-cpp[NetCoreHost#8](../../../samples/core/hosting/host.cpp#8)]

別の選択肢としては、`ExecuteAssembly` がホストのニーズを満たさない場合、`CreateDelegate` を利用し、静的マネージ メソッドの関数ポインターを作成します。 その場合、ホストにそれが呼び出すメソッドのシグネチャを通知する必要があります (関数ポインターの種類を作成する目的で)。ただし、アセンブリのエントリ ポイント以外のコードを呼び出す柔軟性が許可されます。

```C++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
  domainId,
  L"HW, Version=1.0.0.0, Culture=neutral",  // Target managed assembly
  L"ConsoleApplication.Program",            // Target managed type
  L"Main",                                  // Target entry point (static method)
  (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a>手順 8 - クリーンアップ
最後に、ホストはそれ自体のクリーンアップを行います。AppDomain をアンロードし、ランタイムを停止し、`ICLRRuntimeHost2` 参照を解放します。

[!code-cpp[NetCoreHost#9](../../../samples/core/hosting/host.cpp#9)]

## <a name="about-hosting-net-core-on-unix"></a>Unix で .NET Core をホスティングする方法について
.NET Core はプラットフォームに依存しない製品です。Windows、Linux、Mac オペレーティング システムで動作します。 ただし、ネイティブ アプリケーションのように、プラットフォームが異なればホストに違いがあります。 前述の `ICLRRuntimeHost2` を利用してランタイムを開始し、AppDomain を作成し、マネージ コードを実行するプロセスは、サポートされているあらゆるオペレーティング システムで動作するはずです。 ただし、mscoree.h に定義されているインターフェイスは、Unix プラットフォームで使用するには複雑です。mscoree は、さまざまな面で Win32 を想定しているためです。

Unix プラットフォームでのホスティングを簡単にするために、よりプラットフォーム ニュートラルなホスティング API ラッパーのセットが [coreclrhost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h) にあります。

coreclrhost.h を利用する例 (mscoree.h を直接利用するのではなく) が [UnixCoreRun ホスト](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts)にあります。 coreclrhost.h の API を利用してランタイムをホスティングする手順は、mscoree.h を使用するときので順に似ています。

1. (コマンド ライン パラメーターなどから) 実行するマネージ コードを特定します。 
2. CoreCLR ライブラリを読み込みます。
    1. `dlopen("./libcoreclr.so", RTLD_NOW | RTLD_LOCAL);` 
3. CoreCLR の `coreclr_initialize`、`coreclr_create_delegate`、`coreclr_execute_assembly`、`coreclr_shutdown` 関数の関数ポインターを `dlsym` を利用して取得します。
    1. `coreclr_initialize_ptr coreclr_initialize = (coreclr_initialize_ptr)dlsym(coreclrLib, "coreclr_initialize");`
4. AppDomain プロパティを設定します (TPA リストなど)。 これは前述の mscoree ワークフローの手順 5 と同じです。
5. `coreclr_initialize` を使用し、ランタイムを開始し、AppDomain を作成します。 これで今後のホスティング呼び出しで使用される `hostHandle` ポインターも作成されます。
    1. この関数は、前述のワークフローの手順 4 と 6 の両方の役割を実行します。 
6. `coreclr_execute_assembly` または `coreclr_create_delegate` を利用してマネージ コードを実行します。 これらの関数は、前述のワークフローの手順 7 の mscoree の `ExecuteAssembly` 関数と `CreateDelegate` 関数に似ています。
7. `coreclr_shutdown` を利用して AppDomain をアンロードし、ランタイムをシャットダウンします。 

## <a name="conclusion"></a>まとめ
ホストがビルドされたら、テストできます。コマンド ラインから実行し、ホストが期待する引数を渡します (実行するマネージ アプリなど)。 実行するホストの .NET Core アプリを指定するとき、`dotnet build` により生成された .dll を使用してください。 自己完結型アプリケーションのために `dotnet publish` で生成された実行可能ファイルが実質的に既定の .NET Core ホストになります (メインライン シナリオでコマンド ラインから直接、アプリを起動できるように)。ユーザー コードがコンパイルされ、同じ名前の dll が作られます。 

最初の実行で動作しなかった場合、ホストが期待している場所に *coreclr.dll* があること、必要なすべての Framework ライブラリが TPA 一覧にあること、CoreCLR のビット数 (32 ビットまたは 64 ビット) がホストのビルド方法に一致することをもう一度確認してください。

.NET Core ランタイムのホスティングは、多くの開発者が必要としない高度なシナリオですが、ネイティブ プロセスからマネージ コードを起動する場合や .NET Core ランタイムの動作をより細かくコントロールする場合、非常に便利です。 .NET Core は並行して実行できるので、同じプロセス内で、複数のバージョンの .NET Core ランタイムを初期化して開始するホストを作成し、そのすべてのホスト上でアプリを実行することもできます。 
