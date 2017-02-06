---
title: "global.json リファレンス | Microsoft Docs"
description: "global.json リファレンス"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 11/02/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
translationtype: Human Translation
ms.sourcegitcommit: 2ad428dcda9ef213a8487c35a48b33929259abba
ms.openlocfilehash: 97a9ee85025c15e21d4a7cbdce31d35d3894e7d6

---

# <a name="globaljson-reference-tooling-preview-4"></a>global.json リファレンス (Tooling Preview 4)

> [!WARNING]
> このトピックは、Visual Studio 2017 RC - .NET Core Tools Preview 4 を対象としています。 .NET Core Tools Preview 2 バージョンについては、「[global.json リファレンス](../../tools/global-json.md)」トピック参照してください。

global.json ファイルは、.NET Core コマンド ラインの Preview 4 に引き続き存在します。 ただし、その主な目的は以前のリリースのようにソリューションのメタデータを定義することではなく、`sdk` プロパティによって使用されている CLI バージョンを選択できるようにすることです。 

このリファレンスはこのような事実を反映しています。 

## <a name="sdk"></a>SDK
型: Object

SDK に関する情報を指定します。

### <a name="version"></a>version
型: String

使用する SDK のバージョンです。

次に例を示します。

```json
{
    "sdk": {
        "version": "1.0.0-preview2-003121"
    }
}
```


<!--HONumber=Jan17_HO3-->


