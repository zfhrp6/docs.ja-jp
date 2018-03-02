---
title: "方法: 事前計算済みのタスクを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 262aa626e9e426da94de0d2ad5f2ef04a5bbc5f3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="b82dd-102">方法: 事前計算済みのタスクを作成する</span><span class="sxs-lookup"><span data-stu-id="b82dd-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="b82dd-103">このドキュメントでは、キャッシュに保持されている非同期ダウンロード操作の結果を取得する <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> メソッドの使用方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="b82dd-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="b82dd-104"><xref:System.Threading.Tasks.Task.FromResult%2A> メソッドは、<xref:System.Threading.Tasks.Task%601.Result%2A> プロパティとして指定された値を保持する、完成した <xref:System.Threading.Tasks.Task%601> オブジェクトを返します。</span><span class="sxs-lookup"><span data-stu-id="b82dd-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="b82dd-105">このメソッドは <xref:System.Threading.Tasks.Task%601> オブジェクトの結果があらかじめ計算されている <xref:System.Threading.Tasks.Task%601> オブジェクトを返す、非同期操作を実行する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="b82dd-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b82dd-106">例</span><span class="sxs-lookup"><span data-stu-id="b82dd-106">Example</span></span>  
 <span data-ttu-id="b82dd-107">次の例では、Web から文字列をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b82dd-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="b82dd-108">これは `DownloadStringAsync` を定義します。</span><span class="sxs-lookup"><span data-stu-id="b82dd-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="b82dd-109">このメソッドでは、Web から非同期的に文字列をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="b82dd-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="b82dd-110">また、この例では <xref:System.Collections.Concurrent.ConcurrentDictionary%602> オブジェクトを使用して、前の操作の結果をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="b82dd-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="b82dd-111">入力アドレスがこのキャッシュに保持されている場合、`DownloadStringAsync` では <xref:System.Threading.Tasks.Task.FromResult%2A> メソッドを使用して、そのアドレスでコンテンツを保持する <xref:System.Threading.Tasks.Task%601> オブジェクトを生成します。</span><span class="sxs-lookup"><span data-stu-id="b82dd-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="b82dd-112">それ以外の場合、`DownloadStringAsync` では Web からファイルをダウンロードし、結果をキャッシュに追加します。</span><span class="sxs-lookup"><span data-stu-id="b82dd-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="b82dd-113">この例では、複数の文字列を 2 回ダウンロードするために必要な時間を計算します。</span><span class="sxs-lookup"><span data-stu-id="b82dd-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="b82dd-114">結果がキャッシュに保持されているため、ダウンロード操作の 2 番目のセットにかかる時間は最初のセットより短くなります。</span><span class="sxs-lookup"><span data-stu-id="b82dd-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="b82dd-115"><xref:System.Threading.Tasks.Task.FromResult%2A> メソッドを使用することで、`DownloadStringAsync` メソッドでこれらの事前計算済みの結果を保持する <xref:System.Threading.Tasks.Task%601> オブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="b82dd-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b82dd-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="b82dd-116">Compiling the Code</span></span>  
 <span data-ttu-id="b82dd-117">コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`CachedDownloads.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `CachedDownloads.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="b82dd-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `CachedDownloads.cs` (`CachedDownloads.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="b82dd-118">**csc.exe CachedDownloads.cs**</span><span class="sxs-lookup"><span data-stu-id="b82dd-118">**csc.exe CachedDownloads.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="b82dd-119">**vbc.exe CachedDownloads.vb**</span><span class="sxs-lookup"><span data-stu-id="b82dd-119">**vbc.exe CachedDownloads.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b82dd-120">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="b82dd-120">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b82dd-121">参照</span><span class="sxs-lookup"><span data-stu-id="b82dd-121">See Also</span></span>  
 [<span data-ttu-id="b82dd-122">タスク ベースの非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="b82dd-122">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
