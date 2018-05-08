---
title: Docker のアプリケーションを設計します。
description: Microsoft プラットフォームとツールでコンテナー化された Docker アプリケーションのライフサイクル
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 6525e5f80ebb0551e4f85904a467d862aa4133ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="design-docker-applications"></a>Docker のアプリケーションを設計します。

第 1 章には、コンテナーと Docker に関する基本的な概念が導入されました。 その情報は、基本的なレベルの作業を開始するに必要な情報です。 しかし、エンタープライズ アプリケーションには、1 つのサービスまたはコンテナーではなく複数のサービスで構成され、複雑なを指定できます。 これらのオプションで使用する場合、オーケストレーションの概念デザイン、サービス指向アーキテクチャ (SOA) より高度な microservices および概念コンテナーへの追加方法を把握する必要があります。 このドキュメントの範囲は microservices に限定されませんが、Docker アプリケーションのライフ サイクルをそのため、これは情報を表示しません microservices アーキテクチャの深さでも正規サン、バック グラウンド タスクまたはジョブでコンテナーと Docker を使用したりもあるためモノリシックなアプリケーション展開アプローチです。

ただし、DevOps とアプリケーションのライフ サイクルに進む前をデザインに移動する方法を理解し、アプリケーションと設計の選択は、新機能を構築する重要な。


>[!div class="step-by-step"]
[前] (index.md) [次へ] (共通のコンテナーのデザインの principles.md)
