---
title: 公式の .NET Docker イメージ
description: コンテナー化された .NET アプリケーションの .NET マイクロサービス アーキテクチャ | 公式の .NET Docker イメージ
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: bb2190a4fae6f8a26b220fd12ecb9f65ea6f4b96
ms.sourcegitcommit: 6c480773ae896f45af4671fb3e26611a50e4dd81
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2018
ms.locfileid: "35251117"
---
# <a name="official-net-docker-images"></a>公式の .NET Docker イメージ

公式の .NET Docker イメージは Microsoft により作成および最適化された Docker イメージです。 [Docker Hub](https://hub.docker.com/u/microsoft/) の Microsoft リポジトリで一般公開されています。 各リポジトリには、.NET のバージョンに応じて、また OS (Linux Debian、Alpine Linux、Windows Nano Server、Windows Server Core など) とそのバージョンに応じて、複数のイメージを含めることができます。

.NET Core 2.1 以降は、ASP.NET Core 用を含むすべての .NET Core イメージが Docker Hub の [.NET Core イメージ リポジトリ](https://hub.docker.com/r/microsoft/dotnet/)で提供されています。

イメージ リポジトリの多くではさまざまなタグを利用できるため、特定のフレームワーク バージョンだけでなく、OS (Linux ディストリビューションまたは Windows のバージョン) も選択できます。


## <a name="net-core-and-docker-image-optimizations-for-development-versus-production"></a>開発と運用における .NET Core および Docker イメージの最適化

Microsoft では開発者向けの Docker イメージをビルドするにあたり、次の主な 2 つのシナリオに重点を置きました。

-   .NET Core アプリの*開発*およびビルドに使用されるイメージ。

-   .NET Core アプリの実行に "*使用*" されるイメージ。

なぜ複数のイメージですか。 コンテナー化されたアプリケーションを開発、ビルド、実行する場合、通常は優先順位がそれぞれ異なります。 このような個々のタスク向けにさまざまなイメージを提供することによって、Microsoft は、アプリを開発、ビルド、および展開する個々のプロセスの最適化を支援しています。

### <a name="during-development-and-build"></a>開発中およびビルド中

開発中に重要な点は、変更を繰り返し処理する速さと、変更をデバッグする機能です。 コードを変更し、それをすばやく確認する機能に比べて、イメージのサイズはそれほど重要ではありません。 ツールおよび "ビルドエージェント コンテナー" の中には、開発プロセスおよびビルド プロセス時に ASP.NET Core の開発イメージ (**microsoft/dotnet:2.1-sdk**) を使用するものがあります。 Docker コンテナー内でビルドを行う場合は、アプリをコンパイルするために必要な要素が重要となります。 これには、コンパイラおよびその他の .NET 依存関係に加えて、Web 開発の依存関係が含まれます。

この種のビルド イメージが重要な理由は何でしょうか。 このイメージは、実稼働環境には展開しません。 実稼働イメージに配置するコンテンツをビルドする場合に使用します。 このイメージは、継続的インテグレーション (CI) 環境、または Docker マルチステージ ビルド使用時のビルド環境で使用されます。

### <a name="in-production"></a>実稼働環境

実稼働環境で重要な点は、実稼働 .NET Core イメージに基づいてコンテナーの展開および運用開始をいかに速く行えるかということです。 したがって、**microsoft/dotnet:2.1-aspnetcore-runtime** に基づくランタイムのみのイメージは、ネットワーク経由で Docker レジストリから Docker ホストまで迅速に送信できるように小さくなっています。 コンテンツは実行できる状態であるため、コンテナーの開始から結果の処理までを最速で行うことができます。 Docker モデルでは、ビルド コンテナーを使用するときに dotnet build または dotnet publish を実行する場合のように C\# コードからコンパイルを行う必要はありません。

この最適化されたイメージでは、アプリケーションを実行するために必要なバイナリとその他のコンテンツのみを配置します。 たとえば、dotnet publish で作成されたコンテンツには、コンパイルされた .NET バイナリ、イメージ、.js、および .css ファイルのみが含まれています。 時間の経過と共に、事前に Just-In-Time (JIT) にコンパイルされたパッケージを含むイメージが表示されます。

.NET Core イメージおよび ASP.NET Core イメージには複数のバージョンがありますが、これらはすべて、基本レイヤーなどの 1 つまたは複数のレイヤーを共有します。 そのため、イメージの格納に必要なディスク領域は小さくて済みます。カスタム イメージとその基本イメージ間のデルタのみで構成されます。 結果として、レジストリからイメージを迅速にプルすることができます。

Docker Hub の .NET イメージ リポジトリを探索すると、タグで分類またはマークされた複数のイメージ バージョンを見つかります。 これらのタグは、次の示すように、必要とするバージョンに応じて使用するものを特定するのに役立ちます。

-   microsoft/dotnet:**2.1-aspnetcore-runtime**

        ASP.NET Core, with runtime only and ASP.NET Core optimizations, on Linux and Windows (multi-arch)

-   microsoft/**dotnet:2.1-sdk**

        .NET Core, with SDKs included, on Linux and Windows (multi-arch)


>[!div class="step-by-step"]
[Previous] (net-container-os-targets.md) [Next] (../architect-microservice-container-applications/index.md)
