---
title: "ポータブル ライブラリの作成 - C# のガイド"
description: "ポータブル ライブラリを作成し、プラットフォームと、ライブラリでサポートするバージョンを指定する方法について説明します。"
keywords: "C#、UWP、ポータブル アセンブリ、クロス プラットフォーム"
ms.date: 08/24/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 254836c0-3be7-4549-bd9a-40fc0f445c31
redirect_url: /dotnet/csharp/tutorials/index
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 534380026773fb2e2203db502b21b8c0ac3d3081
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---

# <a name="creating-portable-libraries"></a><span data-ttu-id="a0443-104">ポータブル ライブラリの作成</span><span class="sxs-lookup"><span data-stu-id="a0443-104">Creating Portable Libraries</span></span>

> <span data-ttu-id="a0443-105">**注:**</span><span class="sxs-lookup"><span data-stu-id="a0443-105">**Note**</span></span>
> 
> <span data-ttu-id="a0443-106">このトピックはまだ作成されておりません。</span><span class="sxs-lookup"><span data-stu-id="a0443-106">This topic hasn't been written yet!</span></span> 
>
> <span data-ttu-id="a0443-107">適用範囲や方法を具体化するのに役立つ皆様からのご意見をお待ちしております。</span><span class="sxs-lookup"><span data-stu-id="a0443-107">We welcome your input to help shape the scope and approach.</span></span> <span data-ttu-id="a0443-108">GitHub で状態の追跡やこの[件](https://github.com/dotnet/docs/issues/950)に関するご意見を投稿することができます。</span><span class="sxs-lookup"><span data-stu-id="a0443-108">You can track the status and provide input on this [issue](https://github.com/dotnet/docs/issues/950) at GitHub.</span></span>
> 
> <span data-ttu-id="a0443-109">このトピックの初期ドラフトや概要の確認をご希望の場合は、この件の連絡先情報を含むメモを入力してください。</span><span class="sxs-lookup"><span data-stu-id="a0443-109">If you would like to review early drafts and outlines of this topic, please leave a note with your contact information in the issue.</span></span>
>
> <span data-ttu-id="a0443-110">ご意見の投稿方法の詳細については、[GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md) でご確認ください。</span><span class="sxs-lookup"><span data-stu-id="a0443-110">Learn more about how you can contribute on [GitHub](https://github.com/dotnet/docs/blob/master/CONTRIBUTING.md).</span></span>
>

