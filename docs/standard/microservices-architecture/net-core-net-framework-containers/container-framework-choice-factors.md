---
title: 意思決定テーブル。 Docker に使用する .NET Frameworks
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | 意思決定テーブル、Docker に使用する .NET Frameworks'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 0e384fabca88d8ad6f93ae626140fb3d5dcaf971
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589324"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>意思決定テーブル: Docker に使用する .NET Frameworks

次では、.NET Framework または .NET Core および Windows または Linux コンテナーを使用するかどうかをまとめています。 Linux コンテナーには、Linux ベースの Docker ホスト (VM またはサーバー) が必要であり、Windows コンテナーには、Windows Server ベースの Docker ホスト (VM またはサーバー) が必要であることを覚えておいてください。

決定に影響を与えるアプリケーションの機能がいくつかあります。 これらの機能の重要性を考え、決定をする必要があります。

> [!IMPORTANT]
> 開発用のコンピューターは、Linux または Windows の Docker ホストを 1 つ実行します。 1 つのソリューションで同時に実行してテストしたい関連するマイクロサービスは、同じコンテナー プラットフォームで実行する必要があります。

* アプリケーション アーキテクチャに、**コンテナー上のマイクロサービス**を選択しました。
    - .NET の実装には、*.NET Core* を選択する必要があります。
    - コンテナー プラットフォームには、*Linux コンテナー*または *Windows コンテナー*を選択する必要があります。
* アプリケーション アーキテクチャに、**モノリシック アプリケーション**を選択しました。
    - .NET の実装には、*.NET Core* または *.NET Framework* を選択する必要があります。
    - *.NET Core* を選択した場合、コンテナー プラットフォームには、*Linux コンテナー*または *Windows コンテナー*を選択する必要があります。
    - *.NET Framework* を選択した場合、コンテナー プラットフォームには、*Windows コンテナー*を選択する必要があります。
* アプリケーションは、**コンテナー ベースの新しい開発 ("グリーン フィールド")** です。
    - .NET の実装には、*.NET Core* を選択する必要があります。
    - コンテナー プラットフォームには、*Linux コンテナー*または *Windows コンテナー*を選択する必要があります。
* アプリケーションは、**コンテナーに移行する Windows Server のレガシー アプリケーション ("ブラウン フィールド")** です。
    - .NET の実装は、フレームワークの依存関係に基づいて *.NET Framework* を選択する必要があります。
    - .NET Framework との依存関係のため、コンテナー プラットフォームには、*Windows コンテナー*を選択する必要があります。
* アプリケーションの設計目標は、**クラス最高のパフォーマンスと拡張性**です。
    - .NET の実装には、*.NET Core* を選択する必要があります。
    - コンテナー プラットフォームには、*Linux コンテナー*または *Windows コンテナー*を選択する必要があります。
* **ASP.NET Core** を使用して、アプリケーションをビルドしました。
    - .NET の実装には、*.NET Core* を選択する必要があります。
    - 他のフレームワークとの依存関係がある場合、*.NET Framework* の実装を使用します。
    - *.NET Core* を選択した場合、コンテナー プラットフォームには、*Linux コンテナー*または *Windows コンテナー*を選択する必要があります。
    - *.NET Framework* を選択した場合、コンテナー プラットフォームには、*Windows コンテナー*を選択する必要があります。
* **ASP.NET 4 (MVC 5、Web API 2、および Web Forms)** を使用してアプリケーションをビルドしました。
    - .NET の実装は、フレームワークの依存関係に基づいて *.NET Framework* を選択する必要があります。
    - .NET Framework との依存関係のため、コンテナー プラットフォームには、*Windows コンテナー*を選択する必要があります。
* アプリケーションで、**SignalR サービス**を使用しています。
    - .NET の実装には、*.NET Framework* または *.NET Core 2.1 (リリースされた場合) 以降*を選択する必要があります。
    - コンテナー プラットフォームには、.NET Framework で SignalR 実装を選択した場合は、*Windows コンテナー*を選択する必要があります。
    - コンテナー プラットフォームには、(リリースされた場合) .NET Core 2.1 以降で SignalR 実装を選択している場合は、Linux コンテナーまたは Windows コンテナーのいずれかを選択する必要があります。  
    - **SignalR サービス**が *.NET Core* 上で実行されている場合、*Linux コンテナーまたは Windows コンテナー*を使用することができます。
* アプリケーションで、**WCF、WF、およびその他の従来のフレームワーク**を使用しています。
    - .NET の実装には、*.NET Framework* または *(今後のリリースのロードマップで) .NET Core* を選択する必要があります。
    - .NET Framework との依存関係のため、コンテナー プラットフォームには、*Windows コンテナー*を選択する必要があります。
* アプリケーションで、**Azure サービスを消費**します。
    - .NET の実装には、*.NET Framework* または *.NET Core (最終的にはすべての Azure サービスで .NET Core 用のクライアント SDK が提供されます)* を選択する必要があります。
    - .NET Framework のクライアント API を使用している場合、コンテナー プラットフォームには、*Windows コンテナー*を選択する必要があります。
    - *.NET Core* 用のクライアント API を使用している場合、*Linux コンテナーと Windows コンテナー*のいずれかを選択することも可能です。

>[!div class="step-by-step"]
[前へ] (net-framework-container-scenarios.md) [戻る] (net-container-os-targets.md)
