---
title: "global.json リファレンス | Microsoft Docs"
description: "global.json リファレンス"
keywords: .NET, .NET Core
author: aL3891
ms.author: mairaw
ms.date: 11/02/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: e1ac9659-425f-4486-a376-c12ca942ead8
translationtype: Human Translation
ms.sourcegitcommit: 796df1549a7553aa93158598d62338c02d4df73e
ms.openlocfilehash: a6b0ad546a8a121ad5ea4642c11842a8dccf7055

---

# <a name="globaljson-reference"></a>global.json リファレンス

> [!WARNING]
> このトピックは .NET Core Tools Preview 2 を対象としています。 .NET Core Tools RC4 バージョンについては、「[global.json リファレンス (.NET Core Tools RC4)](../preview3/tools/global-json.md)」トピックを参照してください。

global.json ファイルは、.NET Core プロジェクトでソリューション メタデータの定義に使用されます。 このファイルは、.NET Core プロジェクトの依存関係を復元する [dotnet-restore](dotnet-restore.md) コマンドが呼び出されたときに使用されます。
このリファレンス トピックでは、global.json ファイルで定義可能なプロパティの一覧を示します。

## <a name="projects"></a>プロジェクト
型: String[]

依存関係を解決するためにビルド システムで検索する必要があるプロジェクトのフォルダーを指定します。 ビルド システムで検索されるのは、最上位の子フォルダーのみです。

次に例を示します。

```json
{
    "projects": [ "src", "test" ]
}
```

## <a name="packages"></a>パッケージ
型: String

パッケージを保存する場所です。

次に例を示します。
```json
{
    "packages": "packages-dir"
}
```

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


