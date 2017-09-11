---
title: "同時実行のプログラミング - C# のガイド"
description: "タスクを並行で実行する (CPU バインドなど) 手法について"
keywords: "C#、非同期、CPU バインド、ネットワーク バインド"
ms.date: 08/24/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0f8b42de-858a-44a3-87d9-998211f26377
redirect_url: /dotnet/csharp/tutorials/index
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 00cf3b04178ca48c9f8f35eb16bc216389e6b272
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="-concurrent-programming"></a><span data-ttu-id="530d5-104">🔧 同時実行のプログラミング</span><span class="sxs-lookup"><span data-stu-id="530d5-104">🔧 Concurrent Programming</span></span>

> <span data-ttu-id="530d5-105">**注:**</span><span class="sxs-lookup"><span data-stu-id="530d5-105">**Note**</span></span>
> 
> <span data-ttu-id="530d5-106">このトピックはまだ作成されておりません。</span><span class="sxs-lookup"><span data-stu-id="530d5-106">This topic hasn’t been written yet!</span></span> 
>
> <span data-ttu-id="530d5-107">適用範囲や方法を具体化するのに役立つ皆様からのご意見をお待ちしております。</span><span class="sxs-lookup"><span data-stu-id="530d5-107">We welcome your input to help shape the scope and approach.</span></span> <span data-ttu-id="530d5-108">GitHub で状態の追跡やこの[件](https://github.com/dotnet/docs/issues/953)に関するご意見を投稿することができます。</span><span class="sxs-lookup"><span data-stu-id="530d5-108">You can track the status and provide input on this [issue](https://github.com/dotnet/docs/issues/953) at GitHub.</span></span>
> 
> <span data-ttu-id="530d5-109">このトピックの初期ドラフトや概要の確認をご希望の場合は、この件の連絡先情報を含むメモを入力してください。</span><span class="sxs-lookup"><span data-stu-id="530d5-109">If you would like to review early drafts and outlines of this topic, please leave a note with your contact information in the issue.</span></span>
>
> <span data-ttu-id="530d5-110">ご意見の投稿方法の詳細については、[GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md) でご確認ください。</span><span class="sxs-lookup"><span data-stu-id="530d5-110">Learn more about how you can contribute on [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>
>

