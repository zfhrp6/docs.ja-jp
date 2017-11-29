---
title: "SaveToHistory 関数 (WPF アンマネージ API リファレンス)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: SaveToHistory
api_location: PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b30884433f81aa5e4bf1241ae4fe34494bef788e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="1acbd-102">SaveToHistory 関数 (WPF アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="1acbd-102">SaveToHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="1acbd-103">この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしてをコードから直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="1acbd-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="1acbd-104">Windows の管理、Windows Presentation Foundation (WPF) インフラストラクチャによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="1acbd-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1acbd-105">構文</span><span class="sxs-lookup"><span data-stu-id="1acbd-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1acbd-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1acbd-106">Parameters</span></span>  
 <span data-ttu-id="1acbd-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="1acbd-107">pHistoryStream</span></span>  
 <span data-ttu-id="1acbd-108">履歴ストリームへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1acbd-108">A pointer to the history stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1acbd-109">要件</span><span class="sxs-lookup"><span data-stu-id="1acbd-109">Requirements</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1acbd-110">要件</span><span class="sxs-lookup"><span data-stu-id="1acbd-110">Requirements</span></span>  
 <span data-ttu-id="1acbd-111">**プラットフォーム:**を参照してください[.NET Framework システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="1acbd-111">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1acbd-112">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="1acbd-112">**DLL:**</span></span>  
  
 <span data-ttu-id="1acbd-113">.NET framework 3.0 および 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="1acbd-113">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="1acbd-114">.NET Framework 4 以降: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="1acbd-114">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="1acbd-115">**.NET framework のバージョン:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1acbd-115">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1acbd-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="1acbd-116">See Also</span></span>  
 [<span data-ttu-id="1acbd-117">WPF のアンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="1acbd-117">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
