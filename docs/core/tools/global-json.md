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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ffa97164736fc7f3edc450682d23bdf499b6eb34
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="globaljson-reference"></a><span data-ttu-id="5e028-104">global.json リファレンス</span><span class="sxs-lookup"><span data-stu-id="5e028-104">global.json reference</span></span>

<span data-ttu-id="5e028-105">*global.json* ファイルを利用すれば、`sdk` プロパティを介して使用される .NET Core ツールのバージョンを選択できます。</span><span class="sxs-lookup"><span data-stu-id="5e028-105">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="5e028-106">.NET Core CLI ツールは、現在の作業ディレクトリ (プロジェクト ディレクトリと同じではない場合があります) 内、またはその親ディレクトリのいずれかからこのファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="5e028-106">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="5e028-107">SDK</span><span class="sxs-lookup"><span data-stu-id="5e028-107">sdk</span></span>
<span data-ttu-id="5e028-108">型: Object</span><span class="sxs-lookup"><span data-stu-id="5e028-108">Type: Object</span></span>

<span data-ttu-id="5e028-109">SDK に関する情報を指定します。</span><span class="sxs-lookup"><span data-stu-id="5e028-109">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="5e028-110">version</span><span class="sxs-lookup"><span data-stu-id="5e028-110">version</span></span>
<span data-ttu-id="5e028-111">型: String</span><span class="sxs-lookup"><span data-stu-id="5e028-111">Type: String</span></span>

<span data-ttu-id="5e028-112">使用する SDK のバージョンです。</span><span class="sxs-lookup"><span data-stu-id="5e028-112">The version of the SDK to use.</span></span>

<span data-ttu-id="5e028-113">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="5e028-113">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```

