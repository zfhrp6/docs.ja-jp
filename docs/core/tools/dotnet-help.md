---
title: "dotnet help コマンド - .NET Core CLI"
description: "dotnet help コマンドでは、指定したコマンドについてより詳細なドキュメントがオンラインで表示されます。"
author: mairaw
ms.author: mairaw
ms.date: 08/17/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: ca7c88675d54d99fdb3526244daaeffe32f32d45
ms.openlocfilehash: 0d43db0bb0a62bb598f7db50c3b8e37936451550
ms.contentlocale: ja-jp
ms.lasthandoff: 08/17/2017

---
# <a name="dotnet-help-reference"></a>dotnet help reference

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>名前

`dotnet help` - 指定したコマンドについて、より詳細なドキュメントがオンラインで表示されます。

## <a name="synopsis"></a>構文

`dotnet help <COMMAND_NAME> [-h|--help]`

## <a name="description"></a>説明

`dotnet help` コマンドは、docs.microsoft.com で、指定したコマンドに関する詳細情報のリファレンス ページを開きます。

## <a name="arguments"></a>引数

`COMMAND_NAME`

.NET Core CLI コマンドの名前です。 有効な CLI コマンドの一覧については、[CLI コマンド](index.md#cli-commands)を参照してください。

## <a name="options"></a>オプション

`-h|--help`

コマンドの短いヘルプを印刷します。

## <a name="examples"></a>例

ドキュメントの [dotnet new](dotnet-new.md) コマンドに関するページを開きます。

`dotnet help new`

