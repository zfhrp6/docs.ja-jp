---
title: global.json リファレンス
description: .NET Core ツールのバージョンを設定できる global.json ファイルのスキーマを参照します。
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.openlocfilehash: 7479774c7b9cdda233cf32d791c16e7fc6d733a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
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
