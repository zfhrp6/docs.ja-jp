---
title: "ProcessUnhandledException 関数 (WPF アンマネージ API リファレンス)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ProcessUnhandledException
api_location: PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bc43b42c2e671e13076ba87ce72e054bd65d107
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="db7f2-102">ProcessUnhandledException 関数 (WPF アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="db7f2-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="db7f2-103">この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしてをコードから直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="db7f2-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="db7f2-104">例外処理のため、Windows Presentation Foundation (WPF) インフラストラクチャによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="db7f2-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db7f2-105">構文</span><span class="sxs-lookup"><span data-stu-id="db7f2-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="db7f2-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="db7f2-106">Parameters</span></span>  
 <span data-ttu-id="db7f2-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="db7f2-107">errorMsg</span></span>  
 <span data-ttu-id="db7f2-108">エラー メッセージ。</span><span class="sxs-lookup"><span data-stu-id="db7f2-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="db7f2-109">必要条件</span><span class="sxs-lookup"><span data-stu-id="db7f2-109">Requirements</span></span>  
 <span data-ttu-id="db7f2-110">**プラットフォーム:**を参照してください[.NET Framework システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="db7f2-110">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db7f2-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="db7f2-111">**DLL:**</span></span>  
  
 <span data-ttu-id="db7f2-112">.NET framework 3.0 および 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="db7f2-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="db7f2-113">.NET Framework 4 以降: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="db7f2-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="db7f2-114">**.NET framework のバージョン:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db7f2-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db7f2-115">参照</span><span class="sxs-lookup"><span data-stu-id="db7f2-115">See Also</span></span>  
 [<span data-ttu-id="db7f2-116">WPF のアンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="db7f2-116">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
