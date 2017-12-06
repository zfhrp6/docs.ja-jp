---
title: "開発者向けの .NET Framework のインストール"
ms.custom: updateeachrelease
ms.date: 10/17/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: get-started-article
helpviewer_keywords:
- .NET Framework redistributable package, downloading
- .NET Framework, installing
- installing .NET Framework
- installation [.NET Framework]
ms.assetid: daf9d9d5-84ac-4bd9-a864-27665ffd0f5c
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 46e79e67b5d6f088eb2a0fb39e6f4f10c6ed8549
ms.sourcegitcommit: 7296449e03f747528f9bc59954c74bf4e359cc1e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="install-the-net-framework-for-developers"></a>開発者向けの .NET Framework のインストール

.NET は、Windows 上で実行されている多数のアプリケーションに不可欠な部分であり、それらのアプリケーションが稼働するための共通の機能を提供します。 .NET Framework は、視覚的に美しいユーザー エクスペリエンスと、シームレスでありながらもセキュリティで保護された通信機能を備えたアプリケーションを構築するための包括的で一貫性のあるプログラミング モデルを開発者に提供します。  

この記事では、.NET Framework 4.5 から [!INCLUDE[net_current](../../../includes/net-current-version.md)] までのすべての .NET Framework バージョンをコンピューターにインストールするためのリンクを紹介します。 開発者の場合、これらのリンクを使用して、.NET Framework をダウンロードし、アプリと共に .NET Framework を再配布することもできます。

> [!NOTE]
> このトピックは、独自のシステムに .NET Framework をインストールする開発者や自分のアプリケーションで .NET Framework をインストールする開発者のために作成されています。 .NET Framework のインストールに関心があるユーザーは、個別トピックをご覧ください。[Windows 10 と Windows Server 2016 に .NET Framework をインストールする](on-windows-10.md)方法など、特定のオペレーティング システムに .NET Framework をインストールする方法を紹介しています。  
  
.NET Framework の新しいバージョンをインストールしても前のバージョンを常に置換するわけではないことに注意してください。 .NET Framework の各バージョンの詳細と、コンピューターにどのバージョンがインストールされているかを判別する方法については、「[.NET Framework のバージョンおよび依存関係](~/docs/framework/migration-guide/versions-and-dependencies.md)」と「[方法: インストールされている .NET Framework バージョンを確認する](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)」を参照してください。 次の表に示されている .NET Framework のバージョンは、すべて .NET Framework 4 のインプレース更新です。 つまり、.NET Framework 4.6 などの以降のバージョンをインストールする場合でも、先だって .NET Framework 4.5、4.5.1、または 4.5.2 など以前のバージョンをインストールする必要がありません。 同様に、.NET Framework 4.6 などの以降のバージョンをインストールする場合に、まず .NET Framework 4.5、4.5.1、または 4.5.2 など以前のバージョンをアンインストールする必要もありません。 

.NET Framework 4.x 以降のバージョンが前のバージョンをインプレース更新するということは、以降のバージョンが既にインストールされていると、表にリストされている以前のバージョンをインストール*できない*ことを意味します。 Windows 10 の 11 月更新プログラムのシステムには、.NET Framework 4.6.1 がプレインストールされているため、.NET Framework 4.6 をインストールすることはできません。    

> [!NOTE]
> .NET Framework 3.5 の詳細については、「[Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール](~/docs/framework/install/dotnet-35-windows-10.md)」を参照してください。  
  
次の表をクイック リンクとして使用し、詳細を参照してください。 インストール前に .NET Framework のシステム要件を確認するには、「[システム要件](~/docs/framework/get-started/system-requirements.md)」を参照してください。 トラブルシューティングの方法は、「[トラブルシューティング](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)」を参照してください。  
  
|.NET Framework のバージョン|Developer のインストール|再頒布可能なインストール|プラットフォームのサポート|  
|----------------------------|----------------------------|----------------------------------|----------------------|  
|**4.7.1**|[NET Framework 4.7.1 Dev Pack](http://go.microsoft.com/fwlink/?LinkId=852105)|[4.7.1 Web インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/?LinkId=852095)<br /><br /> [4.7.1 オフライン インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/?LinkId=852107)|このバージョンを含む製品 <br/>Windows 10 Fall Creators Update<br/>Windows Server、バージョン 1709<br /><br /> インストール可能なバージョン<br/> Windows 10 Creators Update <br /> Windows 10 Anniversary Update<br /> Windows 8.1 以前<br /> Windows Server 2012 R2 以前<br /> (完全な一覧については、「[システム要件](~/docs/framework/get-started/system-requirements.md)」を参照してください)||
|**4.7**|[NET Framework 4.7 Dev Pack](http://go.microsoft.com/fwlink/?LinkId=825319)|[4.7 Web インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/?LinkId=825299)<br /><br /> [4.7 オフライン インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/?LinkId=825303)|このバージョンを含む製品 <br/>Windows 10 Creators Update<br /><br /> インストール可能なバージョン<br /> Windows 10 Anniversary Update<br /> Windows 8.1 以前<br /> Windows Server 2012 R2 以前<br /> (完全な一覧については、「[システム要件](~/docs/framework/get-started/system-requirements.md)」を参照してください)||
|**4.6.2**|[NET Framework 4.6.2 Dev Pack](http://go.microsoft.com/fwlink/?LinkId=780617)|[4.6.2 Web インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/?LinkId=780597)<br /><br /> [4.6.2 オフライン インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/?LinkId=780601)|このバージョンを含む製品 <br /> Windows 10 Anniversary Update<br /><br /> インストール可能なバージョン<br /> Windows 10 の 11 月更新版 <br/> Windows 10 <br /> Windows 8.1 以前<br /> Windows Server 2012 R2 以前<br /> (完全な一覧については、「[システム要件](~/docs/framework/get-started/system-requirements.md)」を参照してください)|
|**4.6.1**|[NET Framework 4.6.1 Dev Pack](http://go.microsoft.com/fwlink/?LinkId=690706)|[4.6.1 Web インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/?LinkId=671729)<br /><br /> [4.6.1 オフライン インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/?LinkId=671744)|インストール可能なバージョン<br /> Windows 10 <br /> Windows 8.1 以前<br /> Windows Server 2012 R2 以前<br /> (完全な一覧については、「[システム要件](~/docs/framework/get-started/system-requirements.md)」を参照してください)|
|**4.6**|[!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)] に含まれています。 詳しくは、「[Visual Studio 2015 へようこそ](http://msdn.microsoft.com/library/dd831853\(v=vs.140\).aspx)」をご覧ください。<br /><br /> [Microsoft .NET Framework 4.6 Targeting Pack](http://go.microsoft.com/fwlink/?LinkId=528261)|[4.6 Web インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/?LinkId=528259)<br /><br /> [4.6 オフライン インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/?LinkId=528233)|このバージョンを含む製品 <br /> Windows 10 <br />[!INCLUDE[vs_dev14](../../../includes/vs-dev14-md.md)]<br /><br /> インストール可能なバージョン<br /> Windows 8.1 以前<br /> Windows Server 2012 R2 以前<br /> (完全な一覧については、「[システム要件](~/docs/framework/get-started/system-requirements.md)」を参照してください)|  
|**4.5.2**|[Microsoft .NET Framework 4.5.2 Developer Pack](http://go.microsoft.com/fwlink/?LinkId=397702)<br /><br /> [Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=325532)、Visual Studio 2012 または他の IDE での使用|[4.5.2 Web インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/p/?LinkId=397703)<br /><br /> [4.5.2 オフライン インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/p/?LinkId=397706)|インストール可能なバージョン<br /> Windows 8.1 以前<br /> Windows Server 2012 R2 以前<br /> (完全な一覧については、「[システム要件](~/docs/framework/get-started/system-requirements.md)」を参照してください)|  
|**4.5.1**|[Microsoft .NET Framework 4.5.1 Developer Pack](http://go.microsoft.com/fwlink/?LinkId=324213)<br /><br /> Visual Studio 2012 または他の IDE での使用|[4.5.1 Web インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/p/?LinkId=310158)<br /><br /> [4.5.1 オフライン インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/p/?LinkId=310159)|このバージョンを含む製品<br /> [!INCLUDE[win81](../../../includes/win81-md.md)]<br /> Windows Server 2012 R2<br /> [Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=325532)<br /><br /> インストール可能なバージョン<br /> [!INCLUDE[win8](../../../includes/win8-md.md)] 以前<br /> [!INCLUDE[winserver8](../../../includes/winserver8-md.md)] 以前<br />(完全な一覧については、「[システム要件](~/docs/framework/get-started/system-requirements.md)」を参照してください)|  
|**4.5**|Visual Studio 2012 に含まれる<br /><br /> [Windows 8 SDK](http://msdn.microsoft.com/windows/hardware/hh852363) の一部としても使用可能|[4.5 Web インストーラーのダウンロード ページ](http://go.microsoft.com/fwlink/p/?LinkId=245484)|このバージョンを含む製品 <br /> [!INCLUDE[win8](../../../includes/win8-md.md)]<br /> [!INCLUDE[winserver8](../../../includes/winserver8-md.md)]<br /> Visual Studio 2012<br /><br /> インストール可能なバージョン<br /> Windows 7 以前<br /> Windows Server 2008 SP2 以前<br />(完全な一覧については、「[システム要件](~/docs/framework/get-started/system-requirements.md)」を参照してください)|  

.NET Framework の特定のバージョンの **Dev Pack** は、利用可能な場合には、サポートされているすべてのプラットフォームにインストールできます。  
  
以下に **Web またはオフライン インストーラー**をインストールできます。  
  
- Windows 8.1 以前  
  
- Windows Server 2012 R2 以前  
  
(完全な一覧については、「[システム要件](~/docs/framework/get-started/system-requirements.md)」を参照してください)  

ユーザーと開発者のための .NET Framework の概要については、「[.NET Framework の概要](../get-started/index.md)」を参照してください。 アプリとの .NET Framework の配置については、「[配置ガイド](~/docs/framework/deployment/deployment-guide-for-developers.md)」を参照してください。 .NET Framework のアーキテクチャおよび主要機能の概要については、[概要](~/docs/framework/get-started/overview.md)を参照してください。  

<a name="choices"></a>
## <a name="installation-choices"></a>インストールの選択肢

開発者を対象としたパックをインストールして、Visual Studio や他の開発環境で .NET Framework の最新バージョンに合わせた開発を行います。または、再頒布可能な .NET Framework をダウンロードして、アプリやコントロールと一緒に配布します。  
  
## <a name="to-install-the-net-framework-developer-or-targeting-pack"></a>.NET Framework Developer Pack または Targeting Pack をインストールするには

.NET Framework 4.5.1 または 4.5.2 の Developer Pack と、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] の Targeting Pack、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]、4.6.2、4.7、4.7.1 の Developer Pack は、Visual Studio などの統合開発環境で使用する .NET Framework 4.5.1、4.5.2 または [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]、4.6.1、4.6.2、または .NET Framework 4.7 または 4.7.1 の参照アセンブリ、言語パック、IntelliSense ファイルを提供します。  Visual Studio を使用している場合、Developer Pack または Targeting Pack をインストールすると、新しいプロジェクトを作成するときに .NET Framework のインストール済みバージョンがターゲットの選択肢に追加されます。  次のいずれかの Developer Pack または Targeting Pack を選択してください。  

- [Microsoft .NET Framework 4.7.1 Dev Pack](http://go.microsoft.com/fwlink/?LinkId=852105)

- [Microsoft .NET Framework 4.7 Dev Pack](http://go.microsoft.com/fwlink/?LinkId=825319)

- [Microsoft .NET Framework 4.6.2 Dev Pack](http://go.microsoft.com/fwlink/?LinkId=780617)  
  
- [Microsoft .NET Framework 4.6.2 Dev Pack](http://go.microsoft.com/fwlink/?LinkId=780617)  
  
- [Microsoft .NET Framework 4.6.1 Dev Pack](http://go.microsoft.com/fwlink/?LinkId=690706)  
  
- [Microsoft .NET Framework 4.6 Targeting Pack](http://go.microsoft.com/fwlink/?LinkId=528261)  
  
- [.NET Framework 4.5.2 Developer Pack](http://go.microsoft.com/fwlink/?LinkId=397702) により、Windows 8.1 以前、Visual Studio 2013、Visual Studio 2012、または他の IDE にバージョン 4.5.2 をインストールします。  
  
- [.NET Framework 4.5.1 Developer Pack](http://go.microsoft.com/fwlink/?LinkId=324213) により、Visual Studio 2012 または他の IDE にバージョン 4.5.1 をインストールします。  
  
開発者パックのダウンロード ページから、**[ダウンロード]** を選択します。 次に、**[実行]** または **[保存]** をクリックし、表示される指示に従います。  
  
## <a name="to-install-or-download-the-net-framework-redistributable"></a>再頒布可能な .NET Framework をインストールまたはダウンロードするには

これらのインストーラーは、アプリやコントロールが対象とするバージョンの .NET Framework について、.NET Framework コンポーネントをダウンロードします。 アプリまたはコントロールを実行する各コンピューターにこれらのコンポーネントをインストールする必要があります。 インストーラーはどちらも再頒布可能であるため、自分のアプリのセットアップ プログラムに含めることができます。  
  
ダウンロード ページは複数の言語で提供されますが、多くのダウンロードは英語でのみ提供されます。 追加の言語サポートについては、言語パックをインストールする必要があります。  
  
次の 2 種類の再頒布可能なインストールが用意されています。  
  
- **Web インストーラー** (Web ブートストラップ) は、インストール先のコンピューターのオペレーティング システムに一致する必須コンポーネントと言語パックを Web からダウンロードします。 このパッケージはオフラインのインストーラーよりもかなり小さくなりますが、安定したインターネット接続が必要です。 [スタンドアロンの言語パック](#standalone_language_packs)をダウンロードして、追加の言語サポートをインストールできます。  
  
- **オフライン インストーラー** (スタンドアロン再頒布可能) には、.NET Framework をインストールするために必要なすべてのコンポーネントが含まれますが、言語パックは含まれていません。 このダウンロードは、Web インストーラーより大きくなります。 オフライン インストーラーはインターネット接続を必要としません。 オフライン インストーラーを実行した後、[スタンドアロンの言語パック](#standalone_language_packs)をダウンロードして、言語サポートをインストールできます。 安定したインターネット接続に依存できない場合は、オフライン インストーラーを使用します。  
  
Web インストーラーとオフライン インストーラーはどちらも、x86 ベースおよび x64 ベースのコンピューター用に設計されていますが ([システム要件](~/docs/framework/get-started/system-requirements.md)を参照)、Itanium ベースのコンピューターはサポートしていません。  
  
1.  インストールする .NET Framework のバージョンのダウンロード ページを開きます。  

   - .NET Framework 4.7.1 ([Web インストーラー](http://go.microsoft.com/fwlink/?LinkId=852095)または[オフライン インストーラー](http://go.microsoft.com/fwlink/p/?LinkId=852107))

   - .NET Framework 4.7 ([Web インストーラー](http://go.microsoft.com/fwlink/?LinkId=825299)または[オフライン インストーラー](http://go.microsoft.com/fwlink/p/?LinkId=825303))

    - .NET Framework 4.6.2 ([Web インストーラー](http://go.microsoft.com/fwlink/?LinkId=780597)または[オフライン インストーラー](http://go.microsoft.com/fwlink/p/?LinkId=780601))  
    
    - .NET Framework 4.6.1 ([Web インストーラー](http://go.microsoft.com/fwlink/?LinkId=671729)または[オフライン インストーラー](http://go.microsoft.com/fwlink/p/?LinkId=671744))  
  
    - .NET framework 4.6 ([Web インストーラー](http://go.microsoft.com/fwlink/?LinkId=528259)または[オフライン インストーラー](http://go.microsoft.com/fwlink/p/?LinkId=528233))  
  
    - .NET Framework 4.5.2 ([Web インストーラー](http://go.microsoft.com/fwlink/p/?LinkId=397703)または[オフライン インストーラー](http://go.microsoft.com/fwlink/p/?LinkId=397706))  
  
    - .NET Framework 4.5.1 ([Web インストーラー](http://go.microsoft.com/fwlink/p/?LinkId=310158)または[オフライン インストーラー](http://go.microsoft.com/fwlink/p/?LinkId=310159))  
  
    - [.NET Framework 4.5](http://go.microsoft.com/fwlink/p/?LinkId=245484)  
  
1. ダウンロード ページの言語を選択します。 このオプションによって、.NET Framework のローカライズされたリソースがダウンロードされるわけではありません。これは、ダウンロード ページに表示されるテキストにのみ影響します。  
  
1. **[ダウンロード]** を選択します。  
  
1. メッセージが表示されたら、システムのアーキテクチャに一致するダウンロードを選択し、**[次へ]** を選択してください。  
  
1. ダウンロードのプロンプトが表示されたら、次のいずれか **1 つ**を実行します。
  
   - コンピューターに .NET Framework をインストールする場合は、**[実行]** を選択し、画面の指示に従います。   
  
   - 再頒布のために .NET Framework をダウンロードする場合は、**[保存]** を選択し、画面の指示に従います。  
  
1. 他の言語用のリソースをダウンロードする場合は、次のセクションの手順に従って、1 つ以上の言語パックをインストールします。  
  
> [!NOTE]
> インストール中に問題が発生した場合は、「[トラブルシューティング](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)」をご覧ください。  
  
 **インストールに関する注意事項:**  
  
- [!INCLUDE[net_v451](../../../includes/net-v451-md.md)]、4.5.2、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]、4.6.1、4.6.2、4.7、4.7.1 は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] のインプレース更新です。  
  
- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] とそのポイント リリース、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] とそのポイント リリース、.NET Framework 4.7 とそのポイント リリースは [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] を置き換えます。 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] がインストールされたシステムにこれらのバージョンをインストールすると、アセンブリが置換されます。
  
- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] とそのポイント リリース、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] とそのポイント リリース、.NET Framework 4.7 とそのポイント リリースをアンインストールすると、前に存在していた [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] のファイルも削除されます。 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]に戻る場合は、そのバージョンとすべての更新プログラムを再インストールする必要があります。 (「 [.NET Framework 4 のインストール](http://go.microsoft.com/fwlink/p/?LinkId=230665)」をご覧ください)。  
  
- [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] とそのポイント リリース、.NET Framework 4.6 とそのポイント リリース、.NET Framework 4.7 とそのポイント リリースをインストールするには、管理者資格情報が必要です。
  
- .NET Framework 4.5 再頒布可能パッケージは、2012 年 10 月 9 に更新されています。この更新により、Microsoft によって生成および署名されたファイルへのデジタル署名が途中で有効期限切れになるという、デジタル証明書の不適切なタイムスタンプに関連する問題が解決しました。 2012 年 8 月 16 日付けの .NET Framework 4.5 再頒布可能パッケージをインストールしていた場合は、[Microsoft ダウンロード センター](http://go.microsoft.com/fwlink/p/?LinkId=245484)から最新の再頒布可能パッケージを入手して更新を行うことをお勧めします。 この問題について詳しくは、「[マイクロソフト セキュリティ アドバイザリ (2749655)](http://technet.microsoft.com/security/advisory/2749655)」および「[サポート技術情報 2770445](http://support.microsoft.com/kb/2770445)」をご覧ください。  
  
<a name="standalone_language_packs"></a>   
## <a name="to-install-language-packs"></a>言語パックのインストール

 言語パックは、サポートされている言語用にローカライズされたリソース (翻訳されたエラー メッセージや UI テキストなど) を含む実行可能ファイルです。 言語パックをインストールしない場合、.NET Framework のエラー メッセージ、その他のテキストは英語で表示されます。  Web インストーラーによって、オペレーティング システムに対応した言語パックが自動的にインストールされますが、追加の言語パックをコンピューターにダウンロードできます。 オフライン インストーラーには言語パックは含まれていません。 
  
> [!IMPORTANT]
> 言語パックには、アプリの実行に必要な .NET Framework コンポーネントは含まれていません。言語パックをインストールする前に、Web インストーラーまたはオフライン インストーラーを実行する必要があります。 既に言語パックをインストールしてある場合は、まず言語パックをアンインストールしてから、.NET Framework をインストールし、言語パックを再インストールします。  
  
1.  インストールした .NET Framework のバージョンに対応する言語パックのダウンロード ページを開きます。  
  
    - [.NET Framework 4.7.1 の言語パック](http://go.microsoft.com/fwlink/?LinkID=852090) 

    - [.NET Framework 4.7 の言語パック](http://go.microsoft.com/fwlink/?LinkID=825306) 

    - [.NET Framework 4.6.2 言語パック](http://go.microsoft.com/fwlink/?LinkID=780604)  
  
    - [.NET Framework 4.6.1 言語パック](http://go.microsoft.com/fwlink/?LinkID=671747)  
  
    - [.NET Framework 4.6 言語パック](http://go.microsoft.com/fwlink/?LinkID=528314)  
  
    - [.NET Framework 4.5.2 言語パック](http://go.microsoft.com/fwlink/?LinkId=397701)  
  
    - [.NET Framework 4.5.1 言語パック](http://go.microsoft.com/fwlink/?LinkId=322101)  
  
    - [.NET Framework 4.5 言語パック](http://go.microsoft.com/fwlink/p/?LinkId=245451)  
  
2.  言語の一覧で、ダウンロードする言語を選択し、その言語でページを再び読み込まれるまで数秒待ちます。  
  
3.  **[ダウンロード]** を選択します。  
  
サポートしている言語の一覧を次の表に示します。  
  
| 言語              | カルチャ |
| --------------------- | :-----: |
| アラビア語                | ar      |
| チェコ語                 | cs      |
| デンマーク語                | da      |
| オランダ語                 | nl      |
| フィンランド語               | fi      |
| フランス語                | fr      |
| ドイツ語                | de      |
| ギリシャ語                 | el      |
| ヘブライ語                | he      |
| ハンガリー語             | hu      |
| イタリア語               | it      |
| 日本語              | ja      |
| 韓国語                | ko      |
| ノルウェー語             | no      |
| ポーランド語                | pl      |
| ポルトガル語 (ブラジル)   | pt-BR   |
| ポルトガル語 (ポルトガル) | pt-PT   |
| ロシア語               | ru      |
| 簡体字中国語    | zh-CHS  |
| スペイン語               | es      |
| スウェーデン語               | sv      |
| 繁体字中国語   | zh-CHT  |
| トルコ語               | tr      |
| 英語 (米国)            | en-US   |
  
## <a name="next-steps"></a>次のステップ  
  
- .NET Framework での経験がない場合は、[概要](~/docs/framework/get-started/overview.md)を参照して、主な概念とコンポーネントの概要を確認してください。  
  
- .NET Framework 4.5 以降のすべてのバージョンでの新機能と機能強化については、「[新機能](../../../docs/framework/whats-new/index.md)」を参照してください。  
  
- アプリと一緒に .NET Framework を配置する方法の詳細については、「[.NET Framework 配置ガイド (開発者向け)](~/docs/framework/deployment/deployment-guide-for-developers.md)」を参照してください。  
  
- アプリと一緒に .NET Framework を配置する場合に影響を与える変更点については、「[.NET Framework 4.5 のインストール中のシステム再起動の削減](~/docs/framework/deployment/reducing-system-restarts.md)」を参照してください。  
  
- .NET Framework 4 から [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] またはそのポイント リリースのいずれかへのアプリの移行については、「[移行ガイド](~/docs/framework/migration-guide/index.md)」を参照してください。 

- .NET Framework のソース コードをオンラインで参照するには、「[.NET Framework Reference Source](http://referencesource.microsoft.com/)」をご覧ください。 この参照ソースは、[GitHub](https://github.com/Microsoft/referencesource) から入手することもできます。 [リファレンス ソースをダウンロード](http://referencesource.microsoft.com/download.html)してオフラインで表示したり、デバッグ中にソース (パッチや更新を含む) をステップ実行したりできます。 詳細については、ブログ記事「[A new look for .NET Reference Source (.NET Reference Source の新しい外観)](http://blogs.msdn.com/b/dotnet/archive/2014/02/24/a-new-look-for-net-reference-source.aspx)」を参照してください。  
  
## <a name="see-also"></a>関連項目

[配置ガイド (開発者向け)](~/docs/framework/deployment/deployment-guide-for-developers.md)   
[配置ガイド (管理者向け)](~/docs/framework/deployment/guide-for-administrators.md)   
[Windows 8、Windows 8.1、および Windows 10 への .NET Framework 3.5 のインストール](~/docs/framework/install/dotnet-35-windows-10.md)   
[.NET Framework のインストールおよびアンインストールのブロックのトラブルシューティング](~/docs/framework/install/troubleshoot-blocked-installations-and-uninstallations.md)
