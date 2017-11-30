---
title: "Visual Studio Tools for Docker (Windows 上の Visual Studio) を使用"
description: "Microsoft プラットフォームとツールが、Docker のコンテナー化アプリケーションのライフ サイクル"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: d7a24633f5857bc5b72ebab42020627c645f4302
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2017
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Visual Studio Tools for Docker (Windows 上の Visual Studio) を使用

Visual Studio Code と Docker CLI を使用する場合は、Docker は、ワークフローに似ています、Visual Studio Tools を使用するときに、開発者ワークフロー (実際には、それが同じ Docker CLI) に基づくは作業を開始する方が簡単です、プロセスを簡略化し、大きい値を提供ビルドで生産性は、実行、およびタスクを構成します。 実行し、f5 キーや ctrl キーを押しながら f5 キーを押して Visual Studio からのような単純な操作を使用して、コンテナーをデバッグすることもできます。 さらに高いを実行し、1 つのコンテナーをデバッグすることだけでなく、Visual Studio 2017 するも実行およびデバッグできます (ソリューション全体) のコンテナーのグループ、同時に、ソリューション レベルで同じ docker compose.yml ファイルで定義されている場合。

## <a name="configuring-your-local-environment"></a>ローカル環境を構成します。

Docker for Windows の最新のバージョンでは、これまでにアプリケーションを開発 Docker のため、次の参照で説明したように、セットアップは単純ですより簡単です。

**詳細情報:** Docker for Windows のインストールに関する詳細については、するには<https://docs.docker.com/docker-for-windows/>です。

Visual Studio 2015 を使用している場合は、更新プログラム 3 またはそれ以降のバージョンと Visual Studio Tools for Docker が必要です。

**詳細情報:** Visual Studio をインストールする方法の詳細についてを参照してください[https://www.visualstudio.com/\ 製品/vs-2015-製品のエディション](https://www.visualstudio.com/products/vs-2015-product-editions)です。

Visual Studio Tools for Docker のインストールに関する詳細を参照するには、するには<http://aka.ms/vstoolsfordocker>と<https://docs.microsoft.com/dotnet/articles/core/docker/visual-studio-tools-for-docker>.

Visual Studio 2017 を使用している場合、Docker のサポートは既にに含まれます。

## <a name="using-docker-tools-in-visual-studio-2015"></a>Visual Studio 2015 での Docker ツールの使用

Visual Studio Tools for Docker では、開発し、検証にローカルで、Docker コンテナー for Linux で Linux Docker ホストまたは VM、または Windows 上で直接、Windows コンテナーの一貫した方法を提供します。

1 つのコンテナーを使用している場合は、.NET Core プロジェクトに Docker のサポートを有効にはまずを開始する必要があります。 これを行うには、図 4-25 を示すように、プロジェクト ファイルを右クリックします。

![https://i1.visualstudiogallery.msdn.s-msft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4/image/file/205468/1/add-docker-support.png](./media/image31.png)

図 4-25: をオンに Visual Studio プロジェクトの Docker のサポート

## <a name="using-docker-tools-in-visual-studio-2017"></a>Visual Studio 2017 で Docker ツールの使用

追加すると Docker のサポート サービス プロジェクト、ソリューション内 (図 4-26 を参照)、Visual Studio ではだけに DockerFile ファイルをプロジェクトに追加されませんも追加しているサービス セクションで、ソリューションの docker compose.yml ファイル (またはしていない場合は、ファイルを作成します。存在)。 Multicontainer、ソリューションの作成を開始する簡単な方法はdocker compose.yml ファイルを開いて、それらを他の機能も更新できます。

![](./media/image32.png)

Visual Studio 2017 プロジェクトでサポートされる Docker ソリューションの図 4-26: オンにします。

この操作は、プロジェクトに DockerFile を追加するだけでなく、グローバルの docker-compose.yml ソリューション レベルで設定するのに必要な構成の行のコードを追加します。

できるサポートを有効に Docker で Visual Studio 2017、ASP.NET Core プロジェクトを作成するときに図 4-27 を示すようにします。

![](./media/image33.png)

図 4-27: をオンにする Docker のサポート、プロジェクトを作成するときに

Visual Studio でソリューションに Docker のサポートを追加すると後も表示されます追加 docker compose.yml ファイルが、ソリューション エクスプ ローラーで新しいノード ツリー図 4-28 を示されています。

![](./media/image34.PNG)

図 4-28: docker compose.yml ファイルこれでソリューション エクスプ ローラーで表示します。

Multicontainer を展開することを実行すると、1 つの docker compose.yml ファイルを使用してアプリケーション docker の構成。環境 (運用と開発) と、実行によっての値をオーバーライドするために、Visual Studio が、それらのグループを追加するただし、型 (デバッグとリリース)。 この機能は、後続の章でよく説明されます。

**詳細情報:** サービスの実装と Docker の Visual Studio Tools の使用の詳細については、次の記事を読み取る。

ビルド、デバッグ、更新、およびローカル Docker コンテナーでのアプリの更新: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

リモート Docker ホストに、ASP.NET のコンテナーの展開: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)


>[!div class="step-by-step"]
[前](docker-アプリ-内側のループ-workflow.md) [次へ] (set-up-windows-containers-with-powershell.md)
