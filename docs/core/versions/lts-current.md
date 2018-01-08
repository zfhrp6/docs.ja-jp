---
title: ".NET Core サポート"
description: ".NET Core のさまざまなリリース トレーニング サポート (LTS と現在) について説明します。"
keywords: ".NET, .NET Core, lts, 現在, fts, サポート, サポート トレーニング, サポート トラック, ライフサイクル, リリース トレーニング"
author: kendrahavens
ms.author: mairaw
ms.date: 01/30/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: fedc7025-f320-4cba-957b-ef74885f66de
ms.workload: dotnetcore
ms.openlocfilehash: 2fcb33c7c5a4a3c31960a683865b0e5e29269a8b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-support"></a>.NET Core サポート

これは .NET Core サポートの一般的な説明です。

## <a name="lts-and-current-release-trains"></a>LTS と現在のリリース トレーニング

2 つのサポート リリース トレーニングを用意することは、ソフトウェア業界、特に、.NET Core のようなオープンソース プロジェクトで一般的に利用されている共通の概念です。 .NET Core には、[LTS (Long Term Support/長期サポート)](https://en.wikipedia.org/wiki/Long-term_support) と現在というサポート リリース トレーニングがあります。 LTS はライフサイクルを通して安定してご利用いただくためのものであり、重大な問題の修正プログラムやセキュリティ上の修正プログラムが提供されます。 新機能の動作と追加のバグ修正は現在のリリースで提供されます。 サポートの観点から、リリース トレーニングには次のサポート ライフサイクル属性が与えられます。

LTS リリースのサポート期間
* LTS リリースの一般公開日から 3 年間
* または後続の LTS リリースの一般公開から 1 年間

現在のリリースのサポート期間
* 親 LTS リリースと同じ 3 年間
* 後続の現在のリリースの一般公開から 3 か月
* および後続の LTS リリースの一般公開から 1 年間

## <a name="versioning"></a>バージョン管理
新しい LTS リリースが発表されると、メジャー バージョン番号が大きくなります。 現在のリリースにはそれに対応する LTS トレーニングと同じメジャー番号が与えられ、マイナー バージョン番号が大きくなります。 たとえば、1.0.3 が LTS で、1.1.0 が現在になります。 いずれかのトレーニングをバグ修正でアップデートすると、パッチ番号が大きくなります。 バージョン管理スキームの詳細については、「[.NET Core バージョン管理](index.md)」を参照してください。

## <a name="what-causes-updates-in-lts-and-current-trains"></a>LTS トレーニングと現在のトレーニングが更新されるしくみ
バグ修正や API 追加など、特定の変更によりバージョン番号が更新されるしくみを理解するには、「[Versioning Documentation](index.md)」 (バージョン管理文書) の「デシジョン ツリー」セクションを参照してください。 現在から LTS 分岐に引き出される変更を決定する絶対的な規則というものはありません。 一般的には、セキュリティ上の更新や動作を修正するパッチが必要となった場合、LTS 分岐の更新が求められます。 LTS 分岐で最近のデスクトップ開発者オペレーティング システムをサポートする予定もありますが、それは常に可能というわけではありません。 特定のリリースでサポートされている API、修正プログラム、オペレーティング システムを理解するには、GitHub でその[リリース ノート](https://github.com/dotnet/core/tree/master/release-notes)を参照してください。

### <a name="further-reading"></a>関連項目
* [.NET Core サポート ライフサイクルのファクト シート](https://www.microsoft.com/net/core/support)
* [現在サポートされているオペレーティング システムとバージョン](https://github.com/dotnet/core/blob/master/roadmap.md)
