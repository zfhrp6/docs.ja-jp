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
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: b814bfc79c2fcd0fd15b9494c18c6d0443a70fb1

---

# <a name="globaljson-reference-net-core-tools-rc4"></a>global.json リファレンス (.NET Core Tools RC4)

> [!WARNING]
> このトピックは .NET Core Tools RC4 を対象としています。 .NET Core Tools Preview 2 バージョンについては、「[global.json リファレンス](../../tools/global-json.md)」トピック参照してください。

global.json ファイルは、.NET Core コマンド ラインの RC4 に引き続き存在します。 ただし、その主な目的は以前のリリースのようにソリューションのメタデータを定義することではなく、`sdk` プロパティによって使用されている CLI バージョンを選択できるようにすることです。 

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


<!--HONumber=Feb17_HO2-->


