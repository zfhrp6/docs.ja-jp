---
title: "global.json リファレンス"
description: ".NET Core ツールのバージョンを設定できる global.json ファイルのスキーマを参照します。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
ms.openlocfilehash: ffa97164736fc7f3edc450682d23bdf499b6eb34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="globaljson-reference"></a><span data-ttu-id="acf6b-104">global.json リファレンス</span><span class="sxs-lookup"><span data-stu-id="acf6b-104">global.json reference</span></span>

<span data-ttu-id="acf6b-105">*global.json* ファイルを利用すれば、`sdk` プロパティを介して使用される .NET Core ツールのバージョンを選択できます。</span><span class="sxs-lookup"><span data-stu-id="acf6b-105">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="acf6b-106">.NET Core CLI ツールは、現在の作業ディレクトリ (プロジェクト ディレクトリと同じではない場合があります) 内、またはその親ディレクトリのいずれかからこのファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="acf6b-106">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="acf6b-107">SDK</span><span class="sxs-lookup"><span data-stu-id="acf6b-107">sdk</span></span>
<span data-ttu-id="acf6b-108">型: Object</span><span class="sxs-lookup"><span data-stu-id="acf6b-108">Type: Object</span></span>

<span data-ttu-id="acf6b-109">SDK に関する情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="acf6b-109">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="acf6b-110">version</span><span class="sxs-lookup"><span data-stu-id="acf6b-110">version</span></span>
<span data-ttu-id="acf6b-111">型: String</span><span class="sxs-lookup"><span data-stu-id="acf6b-111">Type: String</span></span>

<span data-ttu-id="acf6b-112">使用する SDK のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="acf6b-112">The version of the SDK to use.</span></span>

<span data-ttu-id="acf6b-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="acf6b-113">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```
