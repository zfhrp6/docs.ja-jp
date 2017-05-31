---
title: "global.json リファレンス | Microsoft Docs"
description: "global.json リファレンス"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
ms.translationtype: Human Translation
ms.sourcegitcommit: ec7028d43e7236056e5a53160f6017edadfec8c2
ms.openlocfilehash: a35938d355cb86205e9c822736862298508cf861
ms.contentlocale: ja-jp
ms.lasthandoff: 04/06/2017

---

# <a name="globaljson-reference"></a>global.json リファレンス

*global.json* ファイルを利用すれば、`sdk` プロパティを介して使用される .NET Core ツールのバージョンを選択できます。

.NET Core CLI ツールは、現在の作業ディレクトリ (プロジェクト ディレクトリと同じではない場合があります) 内、またはその親ディレクトリのいずれかからこのファイルを検索します。

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

