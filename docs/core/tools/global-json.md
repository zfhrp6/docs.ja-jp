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
# <a name="globaljson-reference"></a><span data-ttu-id="58101-103">global.json リファレンス</span><span class="sxs-lookup"><span data-stu-id="58101-103">global.json reference</span></span>

<span data-ttu-id="58101-104">*global.json* ファイルを利用すれば、`sdk` プロパティを介して使用される .NET Core ツールのバージョンを選択できます。</span><span class="sxs-lookup"><span data-stu-id="58101-104">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="58101-105">.NET Core CLI ツールは、現在の作業ディレクトリ (プロジェクト ディレクトリと同じではない場合があります) 内、またはその親ディレクトリのいずれかからこのファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="58101-105">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="58101-106">SDK</span><span class="sxs-lookup"><span data-stu-id="58101-106">sdk</span></span>
<span data-ttu-id="58101-107">型: Object</span><span class="sxs-lookup"><span data-stu-id="58101-107">Type: Object</span></span>

<span data-ttu-id="58101-108">SDK に関する情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="58101-108">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="58101-109">version</span><span class="sxs-lookup"><span data-stu-id="58101-109">version</span></span>
<span data-ttu-id="58101-110">型: String</span><span class="sxs-lookup"><span data-stu-id="58101-110">Type: String</span></span>

<span data-ttu-id="58101-111">使用する SDK のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="58101-111">The version of the SDK to use.</span></span>

<span data-ttu-id="58101-112">例:</span><span class="sxs-lookup"><span data-stu-id="58101-112">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```
