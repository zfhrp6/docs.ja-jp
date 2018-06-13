---
title: Service Fabric を Windows コンテナーを展開するタイミング
description: Azure のクラウドと Windows コンテナーでの既存の .NET アプリケーションを最新化 |Service Fabric を Windows コンテナーを展開するタイミング
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: c41db8b37c883f9369a6b8d1f8bccbc0535f504c
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957912"
---
# <a name="when-to-deploy-windows-containers-to-service-fabric"></a>Service Fabric を Windows コンテナーを展開するタイミング

Windows コンテナーのベースとするアプリケーションはすばやく IaaS Vm からしても、さらに移動するプラットフォームを使用する必要があります。 これは、自動の強化されたスケーラビリティと高スケーラビリティ、および展開の場合、完全な管理エクスペリエンスの大きな改善点を取得するためにアップグレード バージョン管理、ロールバック、および正常性の監視します。 Azure Service Fabric、または別のクラウド内で、Microsoft Azure クラウドはでも、オンプレミスで使用できます。 orchestrator とこれらの目標を達成することができます。

多くの組織を上げると、2 つの理由をコンテナーに既存のモノリシックなアプリケーションをシフトします。

-   コストの削減、統合および既存のハードウェア、または高密度で実行中のアプリケーションからの削除が原因のいずれか。

-   開発と操作の間で一貫性のある展開コントラクト。

わかりやすく、コストの削減を追求していますのすべての組織がその目標を追跡がある可能性があります。 一貫性のある展開は、評価が困難が重要と同様にします。 一貫性のある展開のコントラクトを通知の開発者が自由に、それらに適したテクノロジを使用する選択でき、運用チームは、単一の方法でアプリケーションを展開および管理を取得します。 本ライセンス条項は、多数のさまざまなテクノロジの複雑さを処理する操作、または強制的に特定のテクノロジでのみ機能する開発者による損害を軽減します。 基本的には、各アプリケーションは自己完結型の展開イメージのコンテナーです。

一部の組織は、刷新 microservices (クラウド ネイティブ アプリケーション) を追加することで続行されますが、その他の多くの組織はここで停止 (アプリケーションをクラウドに最適化された)。 図 4-8 に示すように、する必要がある可能性がありますいないために、これらの組織が microservices アーキテクチャを移動しません。 いずれの場合は、既に取得したことコンテナー plus Service Fabric を使用して、展開を含む完全な管理を提供、エクスペリエンスのアップグレードの利点があります、バージョン管理、ロールバック、および正常性の監視します。

> ![リフト アンド シフト Service Fabric アプリケーション](./media/image8.png)
>
> **図 4-8 です。** リフト アンド シフト Service Fabric アプリケーション

Service Fabric するキーの方法は、既存のコードを再利用し、リフト アンド シフトします。 そのため、Windows コンテナーを使用して、現在の .NET Framework アプリケーションを移行し、Service Fabric に展開できます。 移動を刷新、最終的には、新しい microservices を追加することで維持しやすくなります。

Service Fabric を他の orchestrators を比較するときに、Service Fabric は Windows ベースのアプリケーションとサービスの実行で完成度の高いことを強調表示する必要があります。 Service Fabric が実行されている Windows ベースのサービスとアプリケーション、長年にわたって 1 層、ミッション クリティカルな Microsoft 製品を含むです。 Windows コンテナーの一般提供を持つ最初の orchestrator がありました。 Kubernetes、DC/OS では、Docker Swarm などの他のコンテナーは、Service Fabric の Windows ベースのアプリケーションと Windows コンテナーのよりも小さい完成度の高いが Linux では、完成です。

Service Fabric の最終的な目標 microservices のアプローチを使用したアプリケーション構築の複雑な作業を削減することができます。 最終的にする、microservices コストのかかる再設計を避けるために、アプリケーションの特定の種類。 ことができます小規模、拡張必要なときに、サービスを非推奨、新しいサービスは、追加、およびお客様による使用を使用してアプリケーションを展開します。 ほとんどの開発者にとって microservices をよりわかりやすく行うを解決するのには、まだ他の多くの問題があります。 現在は先ほどを持ち上げるし、Windows コンテナーでアプリケーションをシフト、将来のコンテナーに基づく microservices を追加しようと考えている場合は、Service Fabric sweet スポットです。

>[!div class="step-by-step"]
[前へ](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[次へ](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
