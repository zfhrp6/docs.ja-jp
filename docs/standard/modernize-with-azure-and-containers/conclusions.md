---
title: "まとめ"
description: "Azure のクラウドと Windows コンテナーの既存の .NET アプリケーションを最新化 |結論"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 9ab627793ac45510aba6ce76fdb87834b02e55f8
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2018
---
# <a name="conclusions"></a>まとめ

- 最終的には、コンテナー ベースのソリューションには、コスト節約の利点があります。 コンテナーは、実稼働環境での依存関係が存在しない場合の原因となった摩擦を削除するために、展開に関する問題の解決策です。 これらの問題を削除すると、その開発/テスト、DevOps、および運用操作大幅に向上します。

- Docker コンテナーは、サーバー ベースのアプリケーションまたはサービスの配置の標準的な単位になっています。

- 運用環境でのスケーラブルな Windows コンテナー ベースのアプリケーションをホストするオーケストレーター (Service Fabric Kubernetes など) を使用してください。

- コンテナーをホストする azure Vm は、クラウドでの小規模な開発およびテスト環境の作成を高速で簡単な方法です。

- Azure に既存のアプリケーションから、リレーショナル データベースを移行する場合、azure SQL データベースのマネージ インスタンスが既定で勧めします。

- Visual Studio 2017 と Image2Docker は、Windows コンテナーで、既存の .NET アプリケーションを取得中に開始された学習を向上させることにより刷新を開始するための基本的なツールです。

- 実稼働環境でコンテナー化アプリケーションを配置するときを常に作成または DevOps カルチャと Visual Studio Team Services や Jenkins などの CI/CD パイプライン DevOps ツールを導入します。

- Microsoft Azure では、Windows コンテナー、クラウド インフラストラクチャの PaaS サービスと、既存の .NET Framework アプリケーションを最新化するための最も包括的で完全な環境を提供します。

>[!div class="step-by-step"]
[前へ](walkthroughs-technical-get-started-overview.md)