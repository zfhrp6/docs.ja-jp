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
helpviewer_keywords: tasks, creating pre-computed
ms.assetid: a73eafa2-1f49-4106-a19e-997186029b58
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4596b28afe48aad4a84a7dd72b4a1d44a9ada8a2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-pre-computed-tasks"></a><span data-ttu-id="c1b46-102">方法: 事前計算済みのタスクを作成する</span><span class="sxs-lookup"><span data-stu-id="c1b46-102">How to: Create Pre-Computed Tasks</span></span>
<span data-ttu-id="c1b46-103">このドキュメントを使用する方法について説明、<xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType>キャッシュ内に保持されている非同期ダウンロード操作の結果を取得します。</span><span class="sxs-lookup"><span data-stu-id="c1b46-103">This document describes how to use the <xref:System.Threading.Tasks.Task.FromResult%2A?displayProperty=nameWithType> method to retrieve the results of asynchronous download operations that are held in a cache.</span></span> <span data-ttu-id="c1b46-104"><xref:System.Threading.Tasks.Task.FromResult%2A>メソッドは、完成したを返します<xref:System.Threading.Tasks.Task%601>として指定された値を保持するオブジェクト、<xref:System.Threading.Tasks.Task%601.Result%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="c1b46-104">The <xref:System.Threading.Tasks.Task.FromResult%2A> method returns a finished <xref:System.Threading.Tasks.Task%601> object that holds the provided value as its <xref:System.Threading.Tasks.Task%601.Result%2A> property.</span></span> <span data-ttu-id="c1b46-105">このメソッドは <xref:System.Threading.Tasks.Task%601> オブジェクトの結果があらかじめ計算されている <xref:System.Threading.Tasks.Task%601> オブジェクトを返す、非同期操作を実行する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="c1b46-105">This method is useful when you perform an asynchronous operation that returns a <xref:System.Threading.Tasks.Task%601> object, and the result of that <xref:System.Threading.Tasks.Task%601> object is already computed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1b46-106">例</span><span class="sxs-lookup"><span data-stu-id="c1b46-106">Example</span></span>  
 <span data-ttu-id="c1b46-107">次の例は、文字列を web からダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c1b46-107">The following example downloads strings from the web.</span></span> <span data-ttu-id="c1b46-108">定義する、`DownloadStringAsync`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="c1b46-108">It defines the `DownloadStringAsync` method.</span></span> <span data-ttu-id="c1b46-109">このメソッドは、非同期的に、web から文字列をダウンロードします。</span><span class="sxs-lookup"><span data-stu-id="c1b46-109">This method downloads strings from the web asynchronously.</span></span> <span data-ttu-id="c1b46-110">またこの例では、<xref:System.Collections.Concurrent.ConcurrentDictionary%602>以前の操作の結果をキャッシュするオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c1b46-110">This example also uses a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> object to cache the results of previous operations.</span></span> <span data-ttu-id="c1b46-111">入力のアドレスがこのキャッシュに保持されている場合`DownloadStringAsync`を使用して、<xref:System.Threading.Tasks.Task.FromResult%2A>を生成するメソッド、<xref:System.Threading.Tasks.Task%601>そのアドレスでコンテンツを保持するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="c1b46-111">If the input address is held in this cache, `DownloadStringAsync` uses the <xref:System.Threading.Tasks.Task.FromResult%2A> method to produce a <xref:System.Threading.Tasks.Task%601> object that holds the content at that address.</span></span> <span data-ttu-id="c1b46-112">それ以外の場合、 `DownloadStringAsync` web からファイルをダウンロードし、結果をキャッシュに追加します。</span><span class="sxs-lookup"><span data-stu-id="c1b46-112">Otherwise, `DownloadStringAsync` downloads the file from the web and adds the result to the cache.</span></span>  
  
 [!code-csharp[TPL_CachedDownloads#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_cacheddownloads/cs/cacheddownloads.cs#1)]
 [!code-vb[TPL_CachedDownloads#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_cacheddownloads/vb/cacheddownloads.vb#1)]  
  
 <span data-ttu-id="c1b46-113">この例では、複数の文字列を 2 回ダウンロードするために必要な時間を計算します。</span><span class="sxs-lookup"><span data-stu-id="c1b46-113">This example computes the time that is required to download multiple strings two times.</span></span> <span data-ttu-id="c1b46-114">結果がキャッシュに保持されているために、ダウンロード操作の 2 番目のセットは、最初のセットよりも時間を短縮する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1b46-114">The second set of download operations should take less time than the first set because the results are held in the cache.</span></span> <span data-ttu-id="c1b46-115"><xref:System.Threading.Tasks.Task.FromResult%2A>メソッドにより、`DownloadStringAsync`メソッドを作成<xref:System.Threading.Tasks.Task%601>これらを保持するオブジェクトは、結果を事前計算します。</span><span class="sxs-lookup"><span data-stu-id="c1b46-115">The <xref:System.Threading.Tasks.Task.FromResult%2A> method enables the `DownloadStringAsync` method to create <xref:System.Threading.Tasks.Task%601> objects that hold these pre-computed results.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1b46-116">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c1b46-116">Compiling the Code</span></span>  
 <span data-ttu-id="c1b46-117">コード例をコピーし、Visual Studio プロジェクトに貼り付けるか、`CachedDownloads.cs` ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] では `CachedDownloads.vb`) という名前のファイルに貼り付けてから、Visual Studio のコマンド プロンプト ウィンドウで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="c1b46-117">Copy the example code and paste it in a Visual Studio project, or paste it in a file that is named `CachedDownloads.cs` (`CachedDownloads.vb` for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), and then run the following command in a Visual Studio Command Prompt window.</span></span>  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 <span data-ttu-id="c1b46-118">**csc.exe CachedDownloads.cs**</span><span class="sxs-lookup"><span data-stu-id="c1b46-118">**csc.exe CachedDownloads.cs**</span></span>  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 <span data-ttu-id="c1b46-119">**vbc.exe CachedDownloads.vb**</span><span class="sxs-lookup"><span data-stu-id="c1b46-119">**vbc.exe CachedDownloads.vb**</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c1b46-120">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="c1b46-120">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b46-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1b46-121">See Also</span></span>  
 [<span data-ttu-id="c1b46-122">タスク ベースの非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="c1b46-122">Task-based Asynchronous Programming</span></span>](../../../docs/standard/parallel-programming/task-based-asynchronous-programming.md)
