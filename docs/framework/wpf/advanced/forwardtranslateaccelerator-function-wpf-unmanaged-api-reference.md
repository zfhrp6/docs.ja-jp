---
title: "ForwardTranslateAccelerator 関数 (WPF アンマネージ API リファレンス)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: ForwardTranslateAccelerator
api_location: PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cca9c78eaf13e04d22fce9f61ce4a7ab9ee09769
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="de109-102">ForwardTranslateAccelerator 関数 (WPF アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="de109-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="de109-103">この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしてをコードから直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="de109-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="de109-104">Windows の管理、Windows Presentation Foundation (WPF) インフラストラクチャによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="de109-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de109-105">構文</span><span class="sxs-lookup"><span data-stu-id="de109-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de109-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="de109-106">Parameters</span></span>  
 <span data-ttu-id="de109-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="de109-107">pMsg</span></span>  
 <span data-ttu-id="de109-108">メッセージへのポインター。</span><span class="sxs-lookup"><span data-stu-id="de109-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="de109-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="de109-109">appUnhandled</span></span>  
 <span data-ttu-id="de109-110">`true`アプリが既に指定されていますが、入力メッセージの処理が、それが処理されていません。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="de109-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de109-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="de109-111">Requirements</span></span>  
 <span data-ttu-id="de109-112">**プラットフォーム:**を参照してください[.NET Framework システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="de109-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de109-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="de109-113">**DLL:**</span></span>  
  
 <span data-ttu-id="de109-114">.NET framework 3.0 および 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="de109-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="de109-115">.NET Framework 4 以降: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="de109-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="de109-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de109-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de109-117">参照</span><span class="sxs-lookup"><span data-stu-id="de109-117">See Also</span></span>  
 [<span data-ttu-id="de109-118">WPF のアンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="de109-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
