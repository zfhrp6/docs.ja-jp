---
title: "LoadFromHistory 関数 (WPF アンマネージ API リファレンス)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: LoadFromHistory
api_location: PresentationHost_v0400.dll
ms.assetid: d037c062-a911-4949-b251-ccd3e48b1d17
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cdb68700ab0c11bbd6b09b83a826dc5ca4faa086
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="loadfromhistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="e3887-102">LoadFromHistory 関数 (WPF アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="e3887-102">LoadFromHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="e3887-103">この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしてをコードから直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="e3887-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="e3887-104">Windows の管理、Windows Presentation Foundation (WPF) インフラストラクチャによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="e3887-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3887-105">構文</span><span class="sxs-lookup"><span data-stu-id="e3887-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadFromHistory_export(  
        IStream* pHistoryStream,   
        IBindCtx* pBindCtx  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e3887-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e3887-106">Parameters</span></span>  
 <span data-ttu-id="e3887-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="e3887-107">pHistoryStream</span></span>  
 <span data-ttu-id="e3887-108">履歴情報のストリームへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e3887-108">A pointer to a stream of history information.</span></span>  
  
 <span data-ttu-id="e3887-109">pBindCtx</span><span class="sxs-lookup"><span data-stu-id="e3887-109">pBindCtx</span></span>  
 <span data-ttu-id="e3887-110">バインド コンテキストへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e3887-110">A pointer to a bind context.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3887-111">要件</span><span class="sxs-lookup"><span data-stu-id="e3887-111">Requirements</span></span>  
 <span data-ttu-id="e3887-112">**プラットフォーム:**を参照してください[.NET Framework システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="e3887-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3887-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="e3887-113">**DLL:**</span></span>  
  
 <span data-ttu-id="e3887-114">.NET framework 3.0 および 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="e3887-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="e3887-115">.NET Framework 4 以降: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="e3887-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="e3887-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3887-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3887-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="e3887-117">See Also</span></span>  
 [<span data-ttu-id="e3887-118">WPF のアンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="e3887-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
