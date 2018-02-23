---
title: "公式の .NET Docker イメージ"
description: "コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 公式の .NET Docker イメージ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 42872caa1a9306187daeefd35feb9bec3fae60af
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="official-net-docker-images"></a>公式の .NET Docker イメージ

公式の .NET Docker イメージは Microsoft により作成および最適化された Docker イメージです。 [Docker Hub](https://hub.docker.com/u/microsoft/) の Microsoft リポジトリで一般公開されています。 各リポジトリには、.NET のバージョンに応じて、また OS (Linux Debian、Alpine Linux、Windows Nano Server、Windows Server Core など) とそのバージョンに応じて、複数のイメージを含めることができます。

Microsoft による .NET リポジトリのバージョン設定は、きめ細かく焦点を合わせたものにすることを目的としています。ここで、リポジトリとは特定のシナリオやワークロードのことを示しています。 たとえば、[microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) イメージは、Docker 上で ASP.NET Core を使用する際に必要となります。これらの ASP.NET Core イメージは、コンテナーの開始時間を短縮できるようにさらなる最適化を行います。

その一方で、.NET Core イメージ (microsoft/dotnet) は .NET Core をベースとしたコンソール アプリ向けです。 たとえば、バッチ プロセスや Azure WebJobs、その他のコンソールのシナリオなどでは .NET Core を使用する必要があります。 それらのイメージには ASP.NET Core スタックは含まれません。結果として、コンテナー イメージのサイズが小さくなります。

イメージ リポジトリの多くではさまざまなタグを利用できるため、特定のフレームワーク バージョンだけでなく、OS (Linux ディストリビューションまたは Windows のバージョン) も選択できます。

Microsoft が提供する公式の .NET Docker イメージの詳細については、「[.NET Docker Images summary](https://aka.ms/dotnetdockerimages)」 (NET Docker Images 概要) を参照してください。

## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>開発と運用における .NET Core および Docker イメージの最適化

Microsoft では開発者向けの Docker イメージをビルドするにあたり、次の主な 2 つのシナリオに重点を置きました。

-   .NET Core アプリの*開発*およびビルドに使用されるイメージ。

-   .NET Core アプリの実行に "*使用*" されるイメージ。

なぜ複数のイメージですか。 コンテナー化されたアプリケーションを開発、ビルド、実行する場合、通常は優先順位がそれぞれ異なります。 このような個々のタスク向けにさまざまなイメージを提供することによって、Microsoft は、アプリを開発、ビルド、および展開する個々のプロセスの最適化を支援しています。

### <a name="during-development-and-build"></a>開発中およびビルド中

開発中に重要な点は、変更を繰り返し処理する速さと、変更をデバッグする機能です。 コードを変更し、それをすばやく確認する機能に比べて、イメージのサイズはそれほど重要ではありません。 ツールおよび "ビルドエージェント コンテナー" の中には、開発プロセスおよびビルド プロセス時に ASP.NET Core の開発イメージ (microsoft/aspnetcore-build) を使用するものがあります。 Docker コンテナー内でビルドを行う場合は、アプリをコンパイルするために必要な要素が重要となります。 これには、コンパイラおよびその他の .NET 依存関係に加えて、npm、Gulp、Bower などの Web 開発の依存関係が含まれます。

この種のビルド イメージが重要な理由は何でしょうか。 このイメージは、実稼働環境には展開しません。 実稼働イメージに配置するコンテンツをビルドする場合に使用します。 このイメージは継続的インテグレーション (CI) 環境またはビルド環境で使用されます。 たとえば、ビルド エージェント ホスト (VM など) に直接すべてのアプリケーション依存関係を手動でインストールするのではなく、ビルド エージェントが、アプリケーションのビルドに必要なすべての依存関係と共に .NET Core イメージをインスタンス化します。 この Docker イメージの実行方法を理解する必要があるのはビルド エージェントのみです。 これにより、CI 環境が簡略化され、予測可能性が高まります。

### <a name="in-production"></a>実稼働環境

実稼働環境で重要な点は、実稼働 .NET Core イメージに基づいてコンテナーの展開および運用開始をいかに速く行えるかということです。 したがって、[microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) に基づくランタイムのみのイメージは規模が小さく、したがって、Docker レジストリから Docker ホストまでのネットワークで迅速に移動することができます。 コンテンツは実行できる状態であるため、コンテナーの開始から結果の処理までを最速で行うことができます。 Docker モデルでは、ビルド コンテナーを使用するときに dotnet build または dotnet publish を実行する場合のように C\# コードからコンパイルを行う必要はありません。

この最適化されたイメージでは、アプリケーションを実行するために必要なバイナリとその他のコンテンツのみを配置します。 たとえば、dotnet publish で作成されたコンテンツには、コンパイルされた .NET バイナリ、イメージ、.js、および .css ファイルのみが含まれています。 時間の経過と共に、事前に Just-In-Time (JIT) にコンパイルされたパッケージを含むイメージが表示されます。

.NET Core イメージおよび ASP.NET Core イメージには複数のバージョンがありますが、これらはすべて、基本レイヤーなどの 1 つまたは複数のレイヤーを共有します。 そのため、イメージの格納に必要なディスク領域は小さくて済みます。カスタム イメージとその基本イメージ間のデルタのみで構成されます。 結果として、レジストリからイメージを迅速にプルすることができます。

Docker Hub の .NET イメージ リポジトリを探索すると、タグで分類またはマークされた複数のイメージ バージョンを見つかります。 これらのタグは、次の示すように、必要とするバージョンに応じて使用するものを特定するのに役立ちます。

-   microsoft/**aspnetcore:2.0**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   microsoft/**aspnetcore-build:2.0**

        ASP.NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[Previous] (net-container-os-targets.md) [Next] (../architect-microservice-container-applications/index.md)
