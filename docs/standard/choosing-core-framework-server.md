---
title: "サーバー アプリ用 .NET Core と .NET Framework の選択"
description: ".NET でのサーバー アプリのビルド時に考慮する必要がある .NET の種類に関するガイドです。"
keywords: .NET, .NET Core, .NET Framework
author: cartermp
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 155553e4-89a2-418d-be88-4e75f6c3cc69
translationtype: Human Translation
ms.sourcegitcommit: 572bec82e08d6b47a188e51964c8c2f440fa471c
ms.openlocfilehash: e23514daacb34739b26b7a31afea2ccb30296e79

---

# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>サーバー アプリ用 .NET Core と .NET Framework の選択

.NET を使用してサーバー側のアプリケーションをビルドする場合に選択できるサポート対象ランタイムには、.NET Framework と .NET Core の 2 つがあります。 両方で同じ .NET プラットフォーム コンポーネントの多くが共有され、2 つの間でコードを共有することができます。 ただし、2 つには基本的な違いがあり、どちらを選択するかは実行内容によって決まります。  この記事では、それぞれを使用するタイミングに関するガイダンスを提供します。

次のような場合、サーバー アプリケーションには .NET Core を使用する必要があります。

* クロスプラット フォームが必要である。
* マイクロサービスが対象である。
* Docker コンテナーを使用している。
* 高パフォーマンスでスケーラブルなシステムが必要である。
* アプリケーションごとに異なる .NET バージョンが必要である。

次のような場合、サーバー アプリケーションには .NET Framework を使用する必要があります。

* 現在、アプリケーションで .NET Framework を使用している (移行ではなく拡張することをお勧めします)。
* .NET Core で使用できないサードパーティ製の .NET ライブラリまたは NuGet パッケージを使用する必要がある。
* .NET Core で使用できない .NET テクノロジを使用する必要がある。
* .NET Core をサポートしていないプラットフォームを使用する必要があります。

## <a name="when-to-choose-net-core"></a>どのような場合に .NET Core を選択すべきか

以下に、前述の .NET Core を選択する理由について詳しく説明します。

### <a name="cross-platform-needs"></a>クロスプラットフォームの必要性

複数のプラットフォーム (Windows、Linux および macOS) でアプリケーション (Web/サービス) を実行できるようにすることが目的であれば、明らかに .NET Core は最良の選択です。

.NET Core では、開発ワークステーションとして前述のオペレーティング システムもサポートします。 Visual Studio では、Windows 用の統合開発環境 (IDE) が提供されます。  Visual Studio コードは、IntelliSense とデバッグを含む、.NET Core を完全にサポートする macOS、Linux および Windows でも使用できます。 また、Sublime、Emacs、VI などのサードパーティ製のほとんどのエディターを .NET Core で使用することができ、オープン ソースの [Omnisharp](http://www.omnisharp.net/) プロジェクトを使用してエディターの IntelliSense を取得できます。 さらに、コード エディターをまったく使用せずに、サポートされているすべてのプラットフォームで利用可能な .NET Core コマンドライン ツールを直接使用することもできます。

### <a name="microservices-architecture"></a>マイクロサービス アーキテクチャ

複数の独立した動的にスケーラブルなステートフルまたはステートレス マイクロサービスで構成されるマイクロサービス指向のシステムを採用する場合は、.NET Core が最適です。 .NET Core は軽量で、その API サーフェイスはマイクロサービスのスコープに合わせて最小化することができます。 マイクロサービス アーキテクチャでは、サービスの境界をまたいでテクノロジを混在させることもできます。これにより、.NET Framework、Java、Ruby、またはその他のモノリシック テクノロジで開発された他のマイクロサービスやサービスと連動する新しいマイクロサービスで .NET Core を段階的に採用することができます。

使用できるインフラストラクチャ プラットフォームは多数あります。 大規模で複雑なマイクロサービス システムでは、[Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) を使用できます。 ステートレス マイクロサービスでは、[Azure App Service](https://azure.microsoft.com/services/app-service/) などの他の製品を使用することもできます。 Docker ベースのマイクロサービスの代替手段は、以下の説明のように、どのような種類のマイクロサービスのアプローチにもフィットします。 これらすべてのプラットフォームでは .NET Core がサポートされるため、マイクロサービスをホストするには最適です。

### <a name="containers"></a>コンテナー

一般的に、コンテナーはマイクロサービス アーキテクチャと併用されますが、アーキテクチャ パターンに従う Web アプリやサービスをコンテナー化するために使用することもできます。 Windows コンテナーで .NET Framework を使用できますが、モジュール性があり、軽量な .NET Core はコンテナーには最適です。  コンテナーを作成して展開する場合、そのイメージのサイズは .NET Framework より .NET Core の方がはるかに小さくなります。  また、クロスプラットフォームであるため、Linux Docker コンテナーなどにサーバー アプリを展開することができます。

したがって、独自の Linux または Windows インフラストラクチャで Docker コンテナーをホストしたり、クラスターでコンテナー ベースのアプリケーションを管理、オーケストレーションおよびスケーリングできる [Azure Container Service](https://azure.microsoft.com/services/container-service/) などのクラウド サービスを使用したりすることができます。

### <a name="a-need-for-high-performance-and-scalable-systems"></a>高パフォーマンスでスケーラブルなシステムの必要性

システムで考えられる最高のパフォーマンスとスケーラビリティが必要な場合、NET Core と ASP.NET Core が最適です。 ASP.NET Core は ASP.NET よりパフォーマンスが 10 倍優れており、Java サーブレット、Go および node.js などのマイクロサービスの他の一般的な業界テクノロジをリードしています。

これは、特に何百ものマイクロサービスを実行している可能性があるマイクロサービス アーキテクチャに関連します。 ASP.NET Core を使用することで、はるかに少ない数のサーバー/VM でシステムを実行でき、最終的にインフラストラクチャやホストの費用を節約できます。

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>アプリケーション レベルごとに異なる .NET バージョンの必要性

.NET で異なるバージョンのフレームワークへの依存関係を持つアプリケーションをインストールできるようにする場合は、100% 共存可能な .NET Core を使用する必要があります。 同じコンピューター上に異なるバージョンの .NET Core を簡単にサイド バイ サイド インストールできるため、同じサーバーの複数のサービスをそれぞれ別のバージョンの .NET Core で使用できます。これにより、アプリケーションのアップグレードや IT 運用におけるリスクがなくなり、費用を節約できます。

## <a name="when-to-choose-net-framework"></a>どのような場合に .NET Framework を選択すべきか

.NET Core は新しいアプリケーションとアプリケーション パターンには大きな利点がありますが、既存の多くのシナリオでは引き続き .NET Framework が自然な選択肢となります。そのため、すべてのサーバー アプリケーションで .NET Core が代わりに使用されることはありません。

### <a name="current-net-framework-applications"></a>現在の .NET Framework アプリケーション

ほとんどの場合、既存のアプリケーションを .NET Core に移行する必要はありません。 ASP.NET Core で新しい Web サービスを作成するなど、既存のアプリケーションを拡張する際には、代わりに .NET Core を使用することをお勧めします。

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>.NET Core で使用できないサードパーティ製の .NET ライブラリや NuGet パッケージを使用する必要性

ライブラリでは .NET Standard の採用が迅速に進められています。これにより、.NET Core を含むすべての種類の .NET でコードを共有できるようになります。 .NET Standard 2.0 では、これがさらに容易になります。.NET Core API サーフェイスがかなり大きくなり、.NET Core アプリケーションで既存の .NET Framework ライブラリを直接使用できるようになるためです。 この移行はすぐには行われませんが、いずれにせよ、決定する前に、アプリケーションで必要な特定のライブラリを確認することをお勧めします。

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>.NET Core で使用できない .NET テクノロジを使用する必要性

一部の .NET Framework テクノロジは .NET Core では使用できません。 .NET Core の今後のリリースで使用可能になるものもありますが、それ以外は .NET Core の対象となる新しいアプリケーション パターンには適用されず、使用可能にならない可能性があります。 .NET Core 1.0 にはない最も一般的なテクノロジを、以下のリストに示します。

* ASP.NET Web フォーム アプリケーション: ASP.NET Web フォームは .NET Framework でのみ使用可能であるため、このシナリオでは ASP.NET Core/.NET Core を使用することはできません。 現時点では、ASP.NET Web フォームを .NET Core で使用できるようにする予定はありません。

* ASP.NET Web ページ アプリケーション: ASP.NET Web ページは ASP.NET Core 1.0 には含まれていませんが、[.NET Core のロードマップ](https://github.com/aspnet/Home/wiki/Roadmap)に関するページの説明のとおり、今度のリリースに含まれる予定です。

* ASP.NET SignalR サーバー/クライアントの実装。 .NET Core 1.0 リリース (2016 年 6 月) の時点では、ASP.NET SignalR は ASP.NET Core (クライアントとサーバーの両方) では使用できませんが、[.NET Core のロードマップ](https://github.com/aspnet/Home/wiki/Roadmap)に関するページの説明のとおり、今度のリリースに含まれる予定です。 Preview 版は、[サーバー側](https://github.com/aspnet/SignalR-Server)と[クライアント ライブラリ](https://github.com/aspnet/SignalR-Client-Net)の GitHub リポジトリで利用できます。

* WCF サービスの実装。 .NET Core から WCF サービスを利用する [WCF クライアント ライブラリ](https://github.com/dotnet/wcf)がある場合でも、2016 年 6 月の時点では、WCF サーバーの実装は .NET Framework でのみ可能です。 このシナリオは .NET Core の現在の計画に含まれていませんが、将来に向けて検討中です。

* ワークフローに関連するサービス: .Windows Workflow Foundation (WF)、ワークフロー サービス (1 つのサービスに WCF と WF) および WCF Data Services (旧称: "ADO.NET Data Services") は、NET Framework でのみ使用できます。.NET Core で使用できるようにする予定はありません。

* 言語サポート: 現在、Visual Basic と F# は .NET Core でサポートされていませんが、Visual Studio 2017 以降のバージョンの Visual Studio ではどちらもサポートされる予定です。

正式なロードマップに加え、.NET Core に移植される他のフレームワークもあります。完全なリストについては、[port-to-core](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core) というマークの付いた CoreFX の案件を参照してください。 このリストは Microsoft がこれらのコンポーネントを .NET Core に提供することを約束するものではなく、単にコミュニティの要望を取り込んでいるだけであることに注意してください。 上にリストされているコンポーネントが気になる場合には、GitHub でのディスカッションに参加して意見を述べることを検討してください。 また、何か足りないと感じた場合は、[CoreFX リポジトリで新しい案件を作成](https://github.com/dotnet/corefx/issues/new)してください。

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>.NET Core をサポートしていないプラットフォームを使用する必要性

Microsoft やサードパーティ製のプラットフォームの中には、.NET Core をサポートしないものもあります。 たとえば、Service Fabric のステートフル Reliable Services や Service Fabric Reliable Actors などのいくつかの Azure サービスでは .NET Framework が必要です。 他のいくつかのサービスでは、.NET Core ではまだ使用できない SDK が提供されます。 すべての Azure サービスでは .NET Core を使用しているために、これは過渡的な状況です。 その間、クライアント SDK の代わりに同等の REST API をいつでも使用できます。

## <a name="further-resources"></a>他のリソース

* [.NET Core のガイド](../core/index.md)
* [.NET Framework から .NET Core への移植](../core/porting/index.md)
* [Docker 上の .NET Framework のガイド](../framework/index.md)
* [.NET コンポーネントの概要](components.md)



<!--HONumber=Jan17_HO3-->


