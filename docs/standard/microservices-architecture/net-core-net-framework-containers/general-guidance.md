---
title: 一般的なガイダンス
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | 一般的なガイダンス'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: bd654c23cf8a8d0986575642ef25d6864251a4e4
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104080"
---
# <a name="general-guidance"></a>一般的なガイダンス

このセクションでは、どのような場合に .NET Core または .NET Framework を選択すべきかの概要を示します。 後続のセクションでこれらの選択の詳細について説明します。

次の場合には、コンテナー化された Docker サーバー アプリケーションで、.NET Core と Linux または Windows のコンテナーを併用する必要があります。

-   クロスプラット フォームが必要である。 たとえば、Linux と Windows のコンテナーの両方を使用する場合。

-   アプリケーション アーキテクチャがマイクロサービスに基づく場合。

-   コンテナーを高速で起動する必要があり、かつコンテナーあたりのフットプリントを小さくして密度を高めたり、ハードウェア ユニットあたりのコンテナーを増やしてコストを削減したりしたい場合。

つまり、コンテナー化された .NET アプリケーションを新たに作成する場合には、.NET Core を既定の選択肢として考慮する必要があります。 これには多くの利点があり、コンテナーの理念や作業スタイルとぴったりと適合します。

.NET Core を使用するその他の利点は、同じマシンで複数の .NET バージョンのアプリケーションを同時に実行できることです。 この利点は、コンテナーを使用しないサーバーまたは VM にとってはさらに重要になります。コンテナーは、アプリが必要とする .NET バージョンを特定するためです。 (基礎となる OS と互換性がある場合。)

次の場合には、コンテナー化された Docker サーバー アプリケーションで、.NET Framework と Windows コンテナーを併用する必要があります。

-   現在、アプリケーションで .NET Framework を使用し、Windows で強い依存関係がある場合。

-   .NET Core がサポートしていない Windows API を使用する必要がある場合。

-   .NET Core で使用できないサードパーティ製の .NET ライブラリまたは NuGet パッケージを使用する必要がある場合。

Docker で .NET Framework を使用すると、展開に関する問題を最小限に抑えて、展開のエクスペリエンスを改善できます。 この[*リストアンドシフトのシナリオ*](https://aka.ms/liftandshiftwithcontainersebook)は、ASP.NET WebForms、MVC Web アプリ、WCF (Windows Communication Foundation) サービスなどの、もともと従来の .NET Framework を使用して開発された旧式のアプリケーションをコンテナー化する場合に重要です。

### <a name="additional-resources"></a>その他の技術情報

-   **電子ブック: Azure および Windows コンテナーで既存の .NET Framework アプリケーションを最新化する**
    [*https://aka.ms/liftandshiftwithcontainersebook*](https://aka.ms/liftandshiftwithcontainersebook)

-   **サンプル アプリ: Windows コンテナーを使用した従来の ASP.NET Web アプリの最新化**
    [*https://aka.ms/eshopmodernizing*](https://aka.ms/eshopmodernizing)


>[!div class="step-by-step"]
[前へ](index.md)
[次へ](net-core-container-scenarios.md)
