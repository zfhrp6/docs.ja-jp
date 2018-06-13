---
title: SaveToHistory 関数 (WPF アンマネージ API リファレンス)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- SaveToHistory
api_location:
- PresentationHost_v0400.dll
ms.assetid: 6dd101a3-44ad-4143-b228-772156f9b8ff
ms.openlocfilehash: d678d632fda625420b6f66a5522229fc2ec71317
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546215"
---
# <a name="savetohistory-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="dbe48-102">SaveToHistory 関数 (WPF アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="dbe48-102">SaveToHistory Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="dbe48-103">この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしてをコードから直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="dbe48-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="dbe48-104">Windows の管理、Windows Presentation Foundation (WPF) インフラストラクチャによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="dbe48-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe48-105">構文</span><span class="sxs-lookup"><span data-stu-id="dbe48-105">Syntax</span></span>  
  
```cpp  
HRESULT SaveToHistory(  
   __in_ecount(1) IStream* pHistoryStream  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dbe48-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dbe48-106">Parameters</span></span>  
 <span data-ttu-id="dbe48-107">pHistoryStream</span><span class="sxs-lookup"><span data-stu-id="dbe48-107">pHistoryStream</span></span>  
 <span data-ttu-id="dbe48-108">履歴ストリームへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dbe48-108">A pointer to the history stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbe48-109">要件</span><span class="sxs-lookup"><span data-stu-id="dbe48-109">Requirements</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbe48-110">要件</span><span class="sxs-lookup"><span data-stu-id="dbe48-110">Requirements</span></span>  
 <span data-ttu-id="dbe48-111">**プラットフォーム:** を参照してください[.NET Framework システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="dbe48-111">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbe48-112">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="dbe48-112">**DLL:**</span></span>  
  
 <span data-ttu-id="dbe48-113">.NET framework 3.0 および 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="dbe48-113">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="dbe48-114">.NET Framework 4 以降: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="dbe48-114">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="dbe48-115">**.NET framework のバージョン:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbe48-115">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe48-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="dbe48-116">See Also</span></span>  
 [<span data-ttu-id="dbe48-117">WPF のアンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="dbe48-117">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
