---
title: "フレームワークとターゲット"
description: ".NET のコードを記述するときのフレームワーク ターゲットの概念について説明します。"
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 09/19/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6ef56a2e-593d-497b-925a-1e25bb6df2e6
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: f0c1987f46bd3715c54e270c15eea4b8ee7b67e6
ms.lasthandoff: 03/02/2017

---

# <a name="frameworks-and-targets"></a>フレームワークとターゲット

.NET エコシステムには、フレームワークの概念があります。 フレームワークは、特定のプラットフォームをターゲットにするために使用できる API を定義します。 .NET Framework 4.6 は、これらのプラットフォームの 1 つです。 フレームワークは、Visual Studio やその他の IDE およびエディターで、適切な API セットを提供するために使用されます。 これらは、対象としているフレームワークの適切なパッケージ (および基になるアセット) を確実に作成して使用するため、NuGet パッケージの運用と使用の両方で NuGet でも使用されます。 .NET エコシステムにおける基軸通貨の&1; つとしてフレームワークを考えることができます。 概念は正確性のためにあり、実行時に @System.MissingMethodException やフレンドがユーザーおよび顧客に表示されないようにしるものです。

## <a name="framework-versions"></a>フレームワークのバージョン

次の表は、使用できるフレームワークのセットと、これらが参照される方法、およびこれらが実装する [.NET Standard Library](library.md) のバージョンを定義します。

| フレームワーク | [最新バージョン] | ターゲット フレームワーク モニカー (TFM) | コンパクトなターゲット フレームワーク モニカー (TFM) | .NET Standard バージョン | メタパッケージ |
|:--------: | :--: | :--: | :--: | :--: | :--: | :--: |
| .NET Standard | 1.6 | .NETStandard,Version=1.6 | netstandard1.6 | N/A | [NETStandard.Library](https://www.nuget.org/packages/NETStandard.Library)|
| .NET Core アプリケーション | 1.0.1 | .NETCoreApp,Version=1.0 | netcoreapp1.0 | 1.6 | [Microsoft.NETCore.App](https://www.nuget.org/packages/Microsoft.NETCore.App)|
| .NET Framework | 4.6.2 | .NETFramework,Version=4.6.2 | net462 | 1.5 | N/A |

> [!NOTE]
> これらのフレームワークのバージョンは、最新の安定したバージョンです。 この表で説明されていないリリース前のバージョンがある可能性があります。

## <a name="writing-about-frameworks"></a>フレームワークに関する記述

記述された形式でフレームワークを参照する複数の方法があり、そのほとんどがこのドキュメントで使用されています。 それらは、どちらもドキュメントを解釈するための凡例として以下に説明されていますが、他のドキュメントでガイドとしても使用できます。

例として .NET Framework 4.6.1 を使用すると、次の形式が使用できます。

**成果物を参照する**

.NET プラットフォームまたはランタイムを参照することができます。

- ".NET Framework 4.6.1"

**フレームワークを参照する**

長い形式または短い形式の TFM を使用して、フレームワークまたはフレームワークの対象を参照することができます。 一般的なケースではどちらも等しく有効です。

- `.NETFramework,Version=4.6.1`
- `net461`

**フレームワークのファミリを参照する**

長い形式または短い形式のフレームワーク ID を使用して、フレームワークのファミリを参照することができます。 一般的なケースではどちらも等しく有効です。

- `.NETFramework`
- `net`

