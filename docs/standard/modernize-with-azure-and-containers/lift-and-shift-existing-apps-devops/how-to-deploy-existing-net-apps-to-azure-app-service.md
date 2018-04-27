---
title: 既存の .NET アプリケーションを Azure App Service をデプロイする方法
description: コンテナーの .NET アプリケーションの .NET Microservices アーキテクチャ |既存の .NET アプリケーションを Azure App Service をデプロイする方法
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 74f4d4b1812976d2e2b1581e10134fa57938bffc
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-deploy-existing-net-apps-to-azure-app-service"></a>既存の .NET アプリケーションを Azure App Service をデプロイする方法 

Azure App Service の Web アプリの機能は、web サイトと web アプリをホストするために最適化された完全に管理されたコンピューティング プラットフォームです。 Microsoft Azure でのこの paas 型サービスに専念するビジネス ロジック、Azure は、インフラストラクチャを実行し、アプリをスケールの処理中にします。

## <a name="validate-sites-and-migrate-to-app-service-with-azure-app-service-migration-assistant"></a>サイトを検証し、Azure App Service Migration Assistant の App Service に移行

Visual Studio で、通常、アプリを App Service に移動する新しいアプリケーションを作成することは簡単です。 ただし、App Service に既存のアプリケーションの移行を計画している場合は、まずすべてのアプリケーションの依存関係は App Service と互換性があるかどうかを評価するします。 これには、サーバーの OS など、サーバーにインストールされているサード パーティのソフトウェアの依存関係が含まれます。

使用することができます[Azure App Service Migration Assistant](https://www.migratetoazure.net/)をサイトを分析し、App Service に Windows および Linux の web サーバーから移行します。 移行の一環として、ツールは web アプリを作成および Azure 上のデータベースに応じて、コンテンツを発行し、データベースを発行します。

Azure アプリのサービスの移行のアシスタントをクラウドに Windows Server で実行されている IIS からの移行をサポートします。 App Service では、Windows Server 2003 およびそれ以降のバージョンをサポートします。

> ![https://www.migratetoazure.net/Images/ImageCanvas.png](./media/image5.png)
>
> **図 4-5 です。** Azure App Service Migration Assistant を使用します。

アプリ サービス Migration Assistant は、web サイトを web サーバーから Azure クラウドに移動するツールです。

Web サイトは、App Service に移行は、後にサイトがありますを安全かつ効率的に実行する必要があります。 サイトがセットアップし、Azure クラウド PaaS サービス (アプリ サービス) で自動的に実行します。

App Service の移行ツールでは、web サイトを分析でき、App Service に移動するための互換性についてレポートすることができます。 場合は、分析に満足したら、アプリ サービス Migration Assistant の内容、データ、および設定を移行することができます。 サイトに非常に互換性がない場合、移行ツールがわかります機能させるを調整する必要があります。

### <a name="additional-resources"></a>その他の技術情報

- **Azure App Service Migration Assistant**

    [https://www.migratetoazure.net/](https://www.migratetoazure.net/)

>[!div class="step-by-step"]
[前へ](what-about-cloud-optimized-applications.md)
[次へ](deploy-existing-net-apps-as-windows-containers.md)
