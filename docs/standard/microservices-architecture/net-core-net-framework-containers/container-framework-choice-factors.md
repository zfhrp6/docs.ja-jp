---
title: "意思決定テーブル。 Docker を使用する .NET フレームワーク"
description: "コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |意思決定テーブル、Docker を使用する .NET フレームワーク"
keywords: "Docker, マイクロサービス, ASP.NET, コンテナー"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4889662c4d887bebd320389e3ced6aae1c93133b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>意思決定テーブル: Docker に使用する .NET フレームワーク

.NET Framework または .NET Core および Windows または Linux のコンテナーを使用するかどうかを以下にまとめます。 Linux コンテナーのことに注意して、Linux ベースの Docker ホスト (Vm またはサーバー) を作成する必要があり、Windows コンテナーの必要がある Windows Server ベースの Docker ホスト (Vm またはサーバー)。

アプリケーションの決定に影響を与えるいくつかの機能があります。 決定を行う際に、これらの機能の重要性を比較検討する必要があります。

> [!IMPORTANT]
> 開発用コンピューターでは、Linux または Windows のいずれか 1 つの Docker ホストを実行します。 実行し、同時に 1 つのソリューションをテストする関連 microservices は、すべて同じコンテナー プラットフォーム上で実行する必要があります。

* アプリケーション アーキテクチャが選択肢として、**コンテナーに対する Microservices**です。
    - .NET 実装の選択をする必要があります*.NET Core*です。
    - コンテナー プラットフォームの選択には、いずれかを指定できる*Linux コンテナー*または*Windows コンテナー*です。
* アプリケーション アーキテクチャが選択肢としては、**モノリシック アプリケーション**です。
    - .NET 実装の選択には、いずれかを指定できる*.NET Core*または*.NET Framework*です。
    - 選択した場合*.NET Core*、コンテナー プラットフォームの選択には、いずれかを指定できる*Linux コンテナー*または*Windows コンテナー*です。
    - 選択した場合*.NET Framework*、コンテナー プラットフォームの選択をする必要があります*Windows コンテナー*です。
* アプリケーションが、**新しいコンテナー ベースの開発 (「緑フィールド」)**です。
    - .NET 実装の選択をする必要があります*.NET Core*です。
    - コンテナー プラットフォームの選択には、いずれかを指定できる*Linux コンテナー*または*Windows コンテナー*です。
* アプリケーションが、 **Windows Server コンテナーへの移行のレガシー アプリケーション (「brown フィールド」)**
    - .NET 実装の選択は*.NET Framework* framework の依存関係に基づいています。
    - コンテナー プラットフォームの選択をする必要があります*Windows コンテナー* .NET Framework の依存関係が原因です。
* アプリケーションの設計目標は**クラスで最高のパフォーマンスとスケーラビリティ**です。
    - .NET 実装の選択をする必要があります*.NET Core*です。
    - コンテナー プラットフォームの選択には、いずれかを指定できる*Linux コンテナー*または*Windows コンテナー*です。
* 使用して、アプリケーションをビルドした**ASP.NET Core**です。
    - .NET 実装の選択をする必要があります*.NET Core*です。
    - 使用することができます、 *.NET Framework*実装では、他のフレームワークの依存関係がある場合。
    - 選択した場合*.NET Core*、コンテナー プラットフォームの選択には、いずれかを指定できる*Linux コンテナー*または*Windows コンテナー*です。
    - 選択した場合*.NET Framework*、コンテナー プラットフォームの選択をする必要があります*Windows コンテナー*です。
* 使用して、アプリケーションをビルドした**(MVC 5 の場合、Web API 2、および Web フォーム) に ASP.NET 4**です。
    - .NET 実装の選択は*.NET Framework* framework の依存関係に基づいています。
    - コンテナー プラットフォームの選択をする必要があります*Windows コンテナー* .NET Framework の依存関係が原因です。
* アプリケーションで使用**SignalR サービス**です。
    - .NET 実装の選択は、 *.NET Framework*、または*.NET Core 2.1 (リリースされた場合) またはそれ以降*です。
    - コンテナー プラットフォームの選択をする必要があります*Windows コンテナー* SignalR 実装では、.NET Framework で選択した場合。
    - コンテナー プラットフォームの選択には、(リリースされた場合)、SignalR 実装では、.NET Core 2.1 以降を選択した場合は、Linux コンテナーまたは Windows コンテナーのいずれかを指定できます。  
    - ときに**SignalR サービス**'åžàs' *.NET Core*、使用することができます*Linux コンテナーや Windows コンテナー*です。
* アプリケーションで使用**WCF、WF、およびその他の従来のフレームワーク**です。
    - .NET 実装の選択は*.NET Framework*、または*(将来のリリースのロードマップ) で .NET Core*です。
    - コンテナー プラットフォームの選択をする必要があります*Windows コンテナー* .NET Framework の依存関係が原因です。
* アプリケーションで**消費の Azure サービス**です。
    - .NET 実装の選択は*.NET Framework*、または*(最終的にすべての Azure サービスでは、クライアント Sdk .NET Core) .NET Core*です。
    - コンテナー プラットフォームの選択をする必要があります*Windows コンテナー* .NET Framework クライアント Api を使用する場合。
    - クライアントの利用可能な Api を使用する場合*.NET Core*、間で選択することもできます。 *Linux コンテナーと Windows コンテナーの*します。

>[!div class="step-by-step"]
[前](net-framework-コンテナーの scenarios.md) [次へ] (net-コンテナーの os-targets.md)
