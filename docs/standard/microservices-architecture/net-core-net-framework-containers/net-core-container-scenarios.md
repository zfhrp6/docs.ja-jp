---
title: "Docker コンテナー用 .Net Core を選択するタイミング"
description: ".NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | Docker コンテナー用 .Net Core を選択するタイミング"
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
ms.openlocfilehash: d9489bca5ac69046818a1809b2f3082baea1eaa8
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2018
---
# <a name="when-to-choose-net-core-for-docker-containers"></a>Docker コンテナー用 .Net Core を選択するタイミング

.NET Core のモジュール性と軽量性はコンテナーに最適です。 コンテナーを展開して起動すると、そのイメージは .NET Framework の場合よりも .NET Core の方がはるかに小さくなります。 それに対して、コンテナーに .NET Framework を使用する場合、イメージを Windows Server Core イメージに基づいて作成する必要があります。このイメージは、.NET Core に使用する Windows Nano Server イメージや Linux イメージよりもはるかに重くなります。

さらに、.NET Core はクロスプラットフォームなので、Linux または Windows のコンテナー イメージを使用してサーバー アプリケーションを展開できます。 ただし、従来の .NET Framework を使用している場合は、Windows Server Core に基づいてイメージを展開する必要があります。

ここでは、.NET Core を選択する理由について詳しく説明します。

## <a name="developing-and-deploying-cross-platform"></a>クロスプラットフォームの開発と展開

Docker (Linux と Windows) でサポートされている複数のプラットフォーム上で動作するアプリケーション (Web アプリケーションまたはサービス) を目標としている場合、.NET Framework は Windows のみをサポートしているので、明らかに .NET Core の方が適しています。

.NET Core は開発プラットフォームとして macOS もサポートしています。 ただし、コンテナーを Docker ホストに展開する場合、(現時点で) ホストは Linux または Windows をベースにしている必要があります。 たとえば、開発環境では Mac 上で動作する Linux VM を使用できます。

[Visual Studio](https://www.visualstudio.com/) には Windows 用の統合開発環境 (IDE) が用意されています。また、Docker 開発をサポートしています。 

[Visual Studio for Mac](https://www.visualstudio.com/vs/visual-studio-mac/) は macOS で動作する IDE であり、Xamarin Studio が進化したものです。2017 年中頃から Docker をサポートしています。

また、macOS、Linux、および Windows 上で [Visual Studio Code](https://code.visualstudio.com/) (VS Code) も使用できます。 VS Code は、IntelliSense、デバッグなどの .NET Core を完全にサポートしています。 VS Code は軽量なエディターなので、Docker CLI や [.NET Core コマンドライン インターフェイス (CLI) ツール](../../../core/tools/index.md)と組み合わせて、コンテナー化されたアプリケーションを Mac 上で開発することができます。 Sublime Text、Emacs、vi、.NET 言語の IntelliSense サポートを提供するオープンソースの OmniSharp プロジェクトなど、ほとんどのサードパーティ製エディターで .NET Core を対象にすることもできます。 IDE とエディターだけでなく、サポートされているすべてのプラットフォームで .NET Core CLI を使用できます。

## <a name="using-containers-for-new-green-field-projects"></a>新しい ("グリーン フィールド") プロジェクトにコンテナーを使用する

一般的に、コンテナーはマイクロサービス アーキテクチャと併用されますが、アーキテクチャ パターンに従う Web アプリやサービスをコンテナー化するために使用することもできます。 Windows コンテナーで .NET Framework を使用できますが、モジュール性があり、軽量な .NET Core はコンテナーとマイクロサービス アーキテクチャに最適です。 コンテナーを作成して展開すると、そのイメージは .NET Framework の場合よりも .NET Core の方がはるかに小さくなります。

## <a name="creating-and-deploying-microservices-on-containers"></a>マイクロサービスの作成とコンテナーへの展開

平易なプロセスを使用してマイクロサービス ベースのアプリケーション (コンテナーなし) を構築する場合は、従来の .NET Framework を使用できます。 この場合、.NET Framework は既にインストールされ、複数のプロセスで共有されているため、プロセスは軽量で起動も高速です。 ただし、コンテナーを使用している場合、従来の .NET Framework のイメージも Windows Server Core をベースにしているため、コンテナー上のマイクロサービスのアプローチには重くなりすぎます。

それに対し、.NET Core は軽量なので、コンテナーに基づくマイクロサービス指向のシステムを採用する場合は .NET Core が最適です。 さらに、関連するコンテナー イメージ (Linux イメージまたは Windows Nano イメージ) は軽量で小さいので、コンテナーも軽量で起動が高速になります。

マイクロサービスはできるだけ小さくなるように作られています。つまり、動作時には軽く、フットプリントは小さく、境界コンテキストは小さく、問題になる領域は小さく、開始と停止が高速になるように作られています。 このような要件を満たすには、.NET Core コンテナー イメージのような小型でインスタンス化が高速なコンテナー イメージを使用する必要があります。

マイクロサービス アーキテクチャでは、サービスの境界を越えて、複数のテクノロジを組み合わせて使用することもできます。 そのため、他のマイクロサービスまたは Node.js、Python、Java、GoLang などのテクノロジを使用して開発されたサービスと連携して動作する新しいマイクロサービスについて、.NET Core に徐々に移行することができます。

## <a name="deploying-high-density-in-scalable-systems"></a>スケーラブルなシステムへの高密度の導入

コンテナーベースのシステムで可能な限り最高の密度、粒度、パフォーマンスが必要な場合は、.NET Core と ASP.NET Core が最適です。 ASP.NET Core は、従来の.NET Framework 内の ASP.NET よりも最大 10 倍高速で、Java サーブレット、Go、Node.js など、マイクロサービス用の他の一般的な業界テクノロジをリードしています。

これは、特に何百ものマイクロサービス (コンテナー) を実行している可能性があるマイクロサービス アーキテクチャに関連します。 Linux または Windows Nano 上の (.NET Core ランタイムに基づく) ASP.NET Core イメージを使用すると、はるかに少ない数のサーバーまたは VM でシステムを実行できるので、最終的にはインフラストラクチャとホスティングのコストを節約できます。


>[!div class="step-by-step"]
[前へ] (general-guidance.md) [次へ] (net-framework-container-scenarios.md)
