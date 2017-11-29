---
title: marshalCleanupError MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c78fedaab26ff7f1da7bccd98c83a90e550d9014
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="marshalcleanuperror-mda"></a><span data-ttu-id="3d633-102">marshalCleanupError MDA</span><span class="sxs-lookup"><span data-stu-id="3d633-102">marshalCleanupError MDA</span></span>
<span data-ttu-id="3d633-103">共通言語ランタイム (CLR) が、ネイティブ コードとマネージ コードの境界間でのデータ型のマーシャリングに使用した一時的な構造体とメモリをクリーンアップしようとしたときにエラーが発生すると、`marshalCleanupError` マネージ デバッグ アシスタント (MDA) がアクティブ化されます。</span><span class="sxs-lookup"><span data-stu-id="3d633-103">The `marshalCleanupError` managed debugging assistant (MDA) is activated when the common language runtime (CLR) encounters an error while attempting to clean up temporary structures and memory used for marshaling data types between native and managed code boundaries.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="3d633-104">症状</span><span class="sxs-lookup"><span data-stu-id="3d633-104">Symptoms</span></span>  
 <span data-ttu-id="3d633-105">ネイティブ コードとマネージ コードの遷移を実行する場合、スレッド カルチャなどのランタイム状態が復元されない場合、または<xref:System.Runtime.InteropServices.SafeHandle> をクリーンアップしようしてエラーが発生した場合に、メモリ リークが発生します。</span><span class="sxs-lookup"><span data-stu-id="3d633-105">A memory leak occurs when making native and managed code transitions, runtime state such as thread culture is not restored, or errors occur in <xref:System.Runtime.InteropServices.SafeHandle> cleanup.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="3d633-106">原因</span><span class="sxs-lookup"><span data-stu-id="3d633-106">Cause</span></span>  
 <span data-ttu-id="3d633-107">一時的な構造体のクリーンアップ中に予期しないエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="3d633-107">An unexpected error occurred while cleaning up temporary structures.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="3d633-108">解決策</span><span class="sxs-lookup"><span data-stu-id="3d633-108">Resolution</span></span>  
 <span data-ttu-id="3d633-109">すべての <xref:System.Runtime.InteropServices.SafeHandle> デストラクター、ファイナライザー、カスタム マーシャラーの実装を調べ、エラーがないかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="3d633-109">Review all <xref:System.Runtime.InteropServices.SafeHandle> destructor, finalizer, and custom marshaler implementations for errors.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="3d633-110">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="3d633-110">Effect on the Runtime</span></span>  
 <span data-ttu-id="3d633-111">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="3d633-111">This MDA has no effect on the CLR.</span></span>  
  
## <a name="output"></a><span data-ttu-id="3d633-112">出力</span><span class="sxs-lookup"><span data-stu-id="3d633-112">Output</span></span>  
 <span data-ttu-id="3d633-113">クリーンアップ中に失敗した操作を報告するメッセージ。</span><span class="sxs-lookup"><span data-stu-id="3d633-113">A message reporting the operation that failed during cleanup.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3d633-114">構成</span><span class="sxs-lookup"><span data-stu-id="3d633-114">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3d633-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d633-115">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="3d633-116">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="3d633-116">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="3d633-117">相互運用マーシャリング</span><span class="sxs-lookup"><span data-stu-id="3d633-117">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
