---
title: ".NET Framework およびアプリケーションの配置 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
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
  - ".NET Framework アプリケーションの配置"
  - ".NET Framework, 配置"
  - "配置 (アプリケーションを) [.NET Framework] "
  - "配置 (アプリケーションを) [.NET Framework] , 配布"
  - "配置 (アプリケーションを) [.NET Framework] , 機能"
  - "配置 (アプリケーションを) [.NET Framework] , パッケージ化"
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
caps.latest.revision: 56
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
---
# .NET Framework およびアプリケーションの配置
ここでは、アプリケーションと共に .NET Framework を配置する方法についての概要を示します。  情報のほとんどは、開発者、OEM、およびエンタープライズ管理者を対象としています。  コンピューターに .NET Framework をインストールするユーザーは、「[Installing the .NET Framework 4.5 \(.NET Framework 4.5 のインストール\)](../../../docs/framework/install/guide-for-developers.md)」を参照してください。  
  
## 主な配置リソース  
 .NET Framework の配置とサービスの詳細については、次に示す他の MSDN トピックへのリンク先を参照してください。  
  
 **セットアップと配置**  
  
-   インストーラーと配置についての一般的な情報:  
  
    -   インストーラー オプション:  
  
        -   [Web インストーラー](../../../docs/framework/install/guide-for-developers.md#choices)  
  
        -   [オフライン インストーラー](../../../docs/framework/install/guide-for-developers.md#choices)  
  
    -   インストール モード:  
  
        -   [サイレント インストール](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_custom)  
  
        -   [UI の表示](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining_default)  
  
    -   [.NET Framework 4.5 のインストール中のシステム再起動の削減](../../../docs/framework/deployment/reducing-system-restarts.md)  
  
    -   [ブロックされた .NET Framework インストールのトラブルシューティング](../../../docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)  
  
-   .NET Framework とクライアント アプリケーションの配置 \(開発者向け\):  
  
    -   セットアップと配置プロジェクトでの [InstallShield の使用](../../../docs/framework/deployment/deployment-guide-for-developers.md#installshield)  
  
    -   [Visual Studio の ClickOnce アプリケーションの使用](../../../docs/framework/deployment/deployment-guide-for-developers.md#clickonce)  
  
    -   [WiX インストール パッケージの作成](../../../docs/framework/deployment/deployment-guide-for-developers.md#wix)  
  
    -   [カスタム インストーラーの使用](../../../docs/framework/deployment/deployment-guide-for-developers.md#chaining)  
  
    -   開発者向けの[追加情報](../../../docs/framework/deployment/deployment-guide-for-developers.md)  
  
-   .NET Framework の配置 \(OEM と管理者向け\):  
  
    -   [Windows Assessment and Deployment Kit \(ADK\) \(Windows アセスメント & デプロイメント キット \(ADK\)\)](http://go.microsoft.com/fwlink/p/?LinkId=254976)  
  
    -   [管理者ガイド](../../../docs/framework/deployment/guide-for-administrators.md)  
  
 **サービス**  
  
-   一般情報については、[.NET Framework blog \(.NET Framework ブログ\)](http://go.microsoft.com/fwlink/p/?LinkId=254977) を参照してください。  
  
-   [バージョンの検出](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)  
  
-   [Service Pack と更新プログラムの検出](../../../docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
  
## 配置を簡素化する機能  
 .NET Framework には、アプリケーションを簡単に配置できるようにするための基本機能が数多く用意されています。  
  
-   ゼロインパクト アプリケーション  
  
     この機能は、アプリケーションを分離し、DLL の競合を解消します。  既定では、コンポーネントはほかのアプリケーションに影響を与えません。  
  
-   プライベート コンポーネント \(既定\)  
  
     既定では、コンポーネントはアプリケーション ディレクトリに配置され、コンテナー アプリケーションだけで参照できます。  
  
-   制御コードの共有  
  
     コードを共有するには、既定の動作を実行する代わりに、共有するためのコードを明示的に作成する必要があります。  
  
-   side\-by\-side でのバージョン管理。  
  
     コンポーネントまたはアプリケーションの複数のバージョンを共存させ、使用するバージョンを選択できます。共通言語ランタイムによって、バージョン管理ポリシーが適用されます。  
  
-   XCOPY による配置およびレプリケーション  
  
     自己言及的な、単体で使用できるコンポーネントやアプリケーションは、レジストリ エントリや依存関係を設定せずに配置できます。  
  
-   実行時更新  
  
     管理者は、ASP.NET などのホストを使用してプログラムの DLL を更新できます。リモート コンピューター上の DLL も更新できます。  
  
-   Windows インストーラーとの統合  
  
     アプリケーションを配置するときに、通知、発行、修復、およびオンデマンド インストールのすべてを使用できます。  
  
-   エンタープライズ配置  
  
     この機能を使用すると、Active Directory を使用する場合など、ソフトウェアの配布を簡単に行うことができます。  
  
-   ダウンロードとキャッシュ  
  
     インクリメンタル ダウンロードにより、ダウンロードのサイズを小さくすることができます。また、コンポーネントを分離して、そのアプリケーションだけで使用されるようにし、配置の影響を抑えることができます。  
  
-   完全な権利を与えられていないコード  
  
     ID は、ユーザーではなく、コードに基づきます。証明書関連のダイアログ ボックスは表示されません。  
  
## .NET Framework アプリケーションのパッケージ化と配布  
 .NET Framework でのパッケージ化および配置についての情報の一部は、ドキュメントの別のトピックで説明します。  それらのトピックでは、レジストリ エントリを必要としない[アセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)と呼ばれる自己言及的な単位、名前の一意性を保証し、名前の悪用を防止する[厳密な名前付きアセンブリ](../../../docs/framework/app-domains/strong-named-assemblies.md)、および DLL 競合に関連した問題の多くを解決する[アセンブリのバージョン管理](../../../docs/framework/app-domains/assembly-versioning.md)についての情報を提供します。  以下のセクションでは、.NET Framework アプリケーションのパッケージ化および配布について説明します。  
  
### パッケージ化  
 .NET Framework は、アプリケーション パッケージ化のために、次のオプションを提供します。  
  
-   単一のアセンブリまたはアセンブリのコレクションとしてパッケージ化する。  
  
     このオプションでは、.dll ファイルまたは .exe ファイルは既に作成されているため、単に使用するだけです。  
  
-   キャビネット \(CAB\) ファイルとしてパッケージ化する。  
  
     このオプションでは、配布やダウンロードの時間を短縮するために、ファイルを .cab ファイルに圧縮します。  
  
-   Windows インストーラー パッケージとして、またはその他のインストーラー フォーマットでパッケージ化する。  
  
     このオプションでは、Windows インストーラーで使用する .msi ファイルを作成するか、または他のインストーラー用としてアプリケーションをパッケージ化します。  
  
### 配布  
 .NET Framework には、アプリケーション配布のために、次のオプションが用意されています。  
  
-   XCOPY または FTP を使用する。  
  
     共通言語ランタイム アプリケーションは、自己言及的で、レジストリ エントリを必要としないため、XCOPY または FTP を使用して適切なディレクトリに単純にコピーできます。  その後、そのディレクトリでアプリケーションを実行できます。  
  
-   コードのダウンロードを使用する。  
  
     アプリケーションをインターネットや企業のイントラネットに配布する場合は、コードをコンピューターにダウンロードし、そこでアプリケーションを実行できます。  
  
-   Windows Installer 2.0 などのインストーラー プログラムを使用する。  
  
     Windows インストーラー 2.0 を使用して、グローバル アセンブリ キャッシュおよびプライベート ディレクトリへの .NET Framework アセンブリのインストール、修復、または削除を行うことができます。  
  
### インストール先  
 ランタイムがアプリケーションのアセンブリを検索できるようなアセンブリの配置先については、「[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)」を参照してください。  
  
 アプリケーションの配置方法には、セキュリティの考慮事項も関係します。  コードが存在する場所に基づいて、マネージ コードにセキュリティ アクセス許可が付与されます。  インターネットなど、信頼度の低い場所にアプリケーションやコンポーネントを配置すると、そのアプリケーションやコンポーネントが実行できることは制限されます。  配置とセキュリティ上の考慮事項については、「[コード アクセス セキュリティの基礎](../../../docs/framework/misc/code-access-security-basics.md)」を参照してください。  
  
## 関連トピック  
  
|タイトル|説明|  
|----------|--------|  
|[ランタイムがアセンブリを検索する方法](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)|共通言語ランタイムが、バインド要求を満たすために、使用するアセンブリをどのように特定するかを説明します。|  
|[アセンブリの読み込みのベスト プラクティス](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)|<xref:System.InvalidCastException>、<xref:System.MissingMethodException>、およびその他のエラーの原因となることがある型 ID の問題を回避する方法について説明します。|  
|[.NET Framework 4.5 のインストール中のシステム再起動の削減](../../../docs/framework/deployment/reducing-system-restarts.md)|再起動をできる限り回避する再起動マネージャーと、.NET Framework をインストールするアプリケーションがそれをどのように利用できるかを説明しています。|  
|[配置ガイド \(管理者向け\)](../../../docs/framework/deployment/guide-for-administrators.md)|System Center Configuration Manager \(SCCM\) を使用したシステム管理者による .NET Framework の配置方法と、ネットワーク全体でのシステムの依存関係について説明します。|  
|[配置ガイド \(開発者向け\)](../../../docs/framework/deployment/deployment-guide-for-developers.md)|開発者による .NET Framework とアプリケーションのユーザーのコンピューターへのインストール方法について説明します。|  
|[アプリケーション、サービス、およびコンポーネントの配置](../Topic/Deploying%20Applications,%20Services,%20and%20Components.md)|ClickOnce を使用したアプリケーションの発行手順や、Windows インストーラー テクノロジなど、Visual Studio の配置オプションについて説明します。|  
|[ClickOnce アプリケーションの発行](../Topic/Publishing%20ClickOnce%20Applications.md)|Windows フォーム アプリケーションをパッケージ化し、これを ClickOnce でネットワーク上のクライアント コンピューターに配置する方法を説明します。|  
|[リソースのパッケージ化と配置](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)|.NET Framework でリソースのパッケージ化と配置に使用する、ハブ アンド スポーク モデルについて説明します。リソースの名前付け規則、フォールバック プロセス、およびパッケージ化の代替策についても説明します。|  
|[相互運用アプリケーションの配置](../../../docs/framework/interop/deploying-an-interop-application.md)|相互運用アプリケーションの出荷方法とインストール方法について説明します。通常、相互運用アプリケーションには、.NET Framework クライアント アセンブリ、個別の COM タイプ ライブラリを表す 1 つ以上の相互運用機能アセンブリ、および 1 つ以上の登録済み COM コンポーネントが含まれています。|  
|[方法: .NET Framework 4.5 インストーラーの進行状況を表示する](../../../docs/framework/deployment/how-to-get-progress-from-the-dotnet-installer.md)|進行状況のビューを独自に表示する一方で、.NET Framework セットアップ プロセスをサイレントで起動および追跡する方法を説明します。|  
  
## 参照  
 [開発ガイド](../../../docs/framework/development-guide.md)