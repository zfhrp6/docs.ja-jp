---
title: global.json リファレンス
description: .NET Core ツールのバージョンを設定できる global.json ファイルのスキーマを参照します。
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: ac53a899e76c99527f2670d0a6bed3f8cc6ce31f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
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

例:

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```
