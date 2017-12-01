---
title: "Docker コンテナー、イメージ、およびレジストリ"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |Docker コンテナー、イメージ、およびレジストリ"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 224fed34f06d10760b14aa9ecbae6c0e912915cf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="docker-containers-images-and-registries"></a>Docker コンテナー、イメージ、およびレジストリ

Docker を使用して、開発者は、コンテナー イメージにその依存関係にアプリケーションまたはサービス、およびパッケージを作成します。 イメージは、アプリケーションまたはサービス構成およびその依存関係の静的な表現です。

アプリやサービスを実行するには、アプリのイメージは Docker ホストで実行されるコンテナーを作成するインスタンス化されます。 コンテナーは、開発環境または PC で最初にテストされます。

開発者は、イメージのライブラリとして機能し、実稼働 orchestrators に展開する場合に必要なレジストリ内でイメージを格納する必要があります。 Docker を管理を使用してパブリック レジストリ[Docker Hub](https://hub.docker.com/); 他のベンダーは、別のイメージのコレクションのレジストリを提供します。 また、企業がプライベート レジストリを持つことができます独自のイメージの Docker オンプレミスです。

図 2-4 は、他のコンポーネントにイメージと Docker でレジストリを関連付ける方法を示しています。 ベンダーからの複数のレジストリの内容も表示されます。

![](./media/image5.PNG)

**図 2-4**です。 Docker の用語と概念の分類

レジストリにイメージを配置すると、フレームワーク レベルのすべての依存関係を含む、変更できない静的なアプリケーション ビットを保存できます。 それらのイメージでは、しでバージョン管理および複数の環境に配置でき、したがっては一貫性のある展開ユニットを提供することができます。

プライベート イメージ レジストリ、ホストされているか、オンプレミスまたはクラウドでは、推奨されるときに。

-   画像は必要があります機密性により公開されている共有されません。

-   イメージと、選択したデプロイ環境間の最小のネットワーク待機時間にします。 たとえば、実稼働環境が Azure クラウドの場合は、可能性がありますする、イメージの Azure コンテナー レジストリに格納できるように、ネットワークの待機時間が最小限に抑えられます。 同様の方法で、運用環境が、オンプレミスでの場合に、内部設置型 Docker Trusted Registry 同じローカル ネットワーク内で使用できることができます。

>[!div class="step-by-step"]
[前](docker terminology.md) [次へ] (../net-core-net-framework-containers/index.md)
