---
title: "global.json リファレンス | .NET Core"
description: "global.json リファレンス"
keywords: .NET, .NET Core
author: aL3891
ms.author: mairaw
manager: wpickett
ms.date: 11/02/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e1ac9659-425f-4486-a376-c12ca942ead8
translationtype: Human Translation
ms.sourcegitcommit: 1a84c694945fe0c77468eb77274ab46618bccae6
ms.openlocfilehash: 281f1b717a0e220e533078e973711977617a1401

---

# <a name="globaljson-reference"></a>global.json リファレンス

global.json ファイルは、.NET Core コマンド ラインの Preview 3 に引き続き存在します。 ただし、その主な目的は以前のリリースのようにソリューションのメタデータを定義することではなく、`sdk` プロパティによって使用されている CLI バージョンを選択できるようにすることです。 

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



<!--HONumber=Nov16_HO3-->


