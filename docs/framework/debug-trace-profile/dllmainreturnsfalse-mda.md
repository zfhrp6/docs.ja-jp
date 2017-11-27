---
title: dllMainReturnsFalse MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 91d2dfefc8de49770ec5c0b0083767bbb4b76c0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="dllmainreturnsfalse-mda"></a><span data-ttu-id="02a17-102">dllMainReturnsFalse MDA</span><span class="sxs-lookup"><span data-stu-id="02a17-102">dllMainReturnsFalse MDA</span></span>
<span data-ttu-id="02a17-103">`dllMainReturnsFalse` マネージ デバッグ アシスタント (MDA) は、DLL_PROCESS_ATTACH が原因で呼び出されたユーザー アセンブリのマネージ `DllMain` 関数が FALSE を返す場合にアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="02a17-103">The `dllMainReturnsFalse` managed debugging assistant (MDA) is activated if the managed `DllMain` function of a user assembly, called with reason DLL_PROCESS_ATTACH, returns FALSE.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="02a17-104">症状</span><span class="sxs-lookup"><span data-stu-id="02a17-104">Symptoms</span></span>  
 <span data-ttu-id="02a17-105">`DllMain` 関数が、正しく実行されなかったことを示す FALSE を返しました。</span><span class="sxs-lookup"><span data-stu-id="02a17-105">The `DllMain` function returned FALSE, indicating that it did not execute properly.</span></span> <span data-ttu-id="02a17-106">`DllMain` 関数には通常、重要な初期化コードが含まれているため、これは原因不明の問題を引き起こす可能性があります。</span><span class="sxs-lookup"><span data-stu-id="02a17-106">This can cause undetermined issues because `DllMain` functions typically contain important initialization code.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="02a17-107">原因</span><span class="sxs-lookup"><span data-stu-id="02a17-107">Cause</span></span>  
 <span data-ttu-id="02a17-108">`DllMain` 関数は、ロード時の DLL 初期化の DLL_PROCESS_ATTACH が原因で呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="02a17-108">The `DllMain` function is called with reason DLL_PROCESS_ATTACH for DLL initialization upon load.</span></span> <span data-ttu-id="02a17-109">FALSE が返された場合は、その DLL 初期化が失敗したことを意味します。</span><span class="sxs-lookup"><span data-stu-id="02a17-109">If it returns FALSE, it means that DLL initialization failed.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="02a17-110">解像度</span><span class="sxs-lookup"><span data-stu-id="02a17-110">Resolution</span></span>  
 <span data-ttu-id="02a17-111">失敗した DLL の `DllMain` 関数のコードを分析し、初期化エラーの原因を特定します。</span><span class="sxs-lookup"><span data-stu-id="02a17-111">Analyze the code of the `DllMain` function of the failed DLL and identify the cause of the initialization failure.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="02a17-112">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="02a17-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="02a17-113">この MDA は CLR に影響しません。</span><span class="sxs-lookup"><span data-stu-id="02a17-113">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="02a17-114">`DllMain` の戻り値に関するデータのみを報告します。</span><span class="sxs-lookup"><span data-stu-id="02a17-114">It only reports data about the return value for `DllMain`.</span></span>  
  
## <a name="output"></a><span data-ttu-id="02a17-115">出力</span><span class="sxs-lookup"><span data-stu-id="02a17-115">Output</span></span>  
 <span data-ttu-id="02a17-116">DLL_PROCESS_ATTACH が原因で呼び出された `DllMain` 関数で FALSE が返されたことを示すメッセージ。</span><span class="sxs-lookup"><span data-stu-id="02a17-116">A message indicating that a `DllMain` function, called for reason DLL_PROCESS_ATTACH, returned FALSE.</span></span> <span data-ttu-id="02a17-117">この MDA は、`DllMain` がマネージ コードで実装された場合にのみアクティブになることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="02a17-117">Note that this MDA is activated only if `DllMain` is implemented in managed code.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="02a17-118">構成</span><span class="sxs-lookup"><span data-stu-id="02a17-118">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="02a17-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="02a17-119">See Also</span></span>  
 [<span data-ttu-id="02a17-120">マネージ デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="02a17-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
