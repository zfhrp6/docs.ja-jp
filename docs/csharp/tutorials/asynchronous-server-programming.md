---
title: "非同期サーバー プログラミング - C# のガイド"
description: "非同期のプログラミング手法を使用してサーバーのワークロードをオフロードする手法を学ぶ"
keywords: "C#、非同期、CPU バインド、ネットワーク バインド"
ms.date: 08/24/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 7402b29b-1093-456d-be4c-f60ecb8926bb
redirect_url: /dotnet/csharp/tutorials/index
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 390d0eb2c8416165984ffe6c80ed6977e61a2845
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="-asynchronous-server-programming"></a><span data-ttu-id="be5a1-104">🔧 非同期サーバー プログラミング</span><span class="sxs-lookup"><span data-stu-id="be5a1-104">🔧 Asynchronous Server Programming</span></span>

> <span data-ttu-id="be5a1-105">**注:**</span><span class="sxs-lookup"><span data-stu-id="be5a1-105">**Note**</span></span>
> 
> <span data-ttu-id="be5a1-106">このトピックはまだ作成されておりません。</span><span class="sxs-lookup"><span data-stu-id="be5a1-106">This topic hasn’t been written yet!</span></span> 
>
> <span data-ttu-id="be5a1-107">適用範囲や方法を具体化するのに役立つ皆様からのご意見をお待ちしております。</span><span class="sxs-lookup"><span data-stu-id="be5a1-107">We welcome your input to help shape the scope and approach.</span></span> <span data-ttu-id="be5a1-108">GitHub で状態の追跡やこの[件](https://github.com/dotnet/docs/issues/952)に関するご意見を投稿することができます。</span><span class="sxs-lookup"><span data-stu-id="be5a1-108">You can track the status and provide input on this [issue](https://github.com/dotnet/docs/issues/952) at GitHub.</span></span>
> 
> <span data-ttu-id="be5a1-109">このトピックの初期ドラフトや概要の確認をご希望の場合は、この件の連絡先情報を含むメモを入力してください。</span><span class="sxs-lookup"><span data-stu-id="be5a1-109">If you would like to review early drafts and outlines of this topic, please leave a note with your contact information in the issue.</span></span>
>
> <span data-ttu-id="be5a1-110">ご意見の投稿方法の詳細については、[GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md) でご確認ください。</span><span class="sxs-lookup"><span data-stu-id="be5a1-110">Learn more about how you can contribute on [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>
>

