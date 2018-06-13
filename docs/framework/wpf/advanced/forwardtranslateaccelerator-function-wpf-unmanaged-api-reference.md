---
title: ForwardTranslateAccelerator 関数 (WPF アンマネージ API リファレンス)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ForwardTranslateAccelerator
api_location:
- PresentationHost_v0400.dll
ms.assetid: fff47a86-9d9f-4176-9530-10e1876e393f
ms.openlocfilehash: d8a296c0590d07c4929610021714d2a257236d67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542562"
---
# <a name="forwardtranslateaccelerator-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="2d8b3-102">ForwardTranslateAccelerator 関数 (WPF アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="2d8b3-102">ForwardTranslateAccelerator Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="2d8b3-103">この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしてをコードから直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="2d8b3-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="2d8b3-104">Windows の管理、Windows Presentation Foundation (WPF) インフラストラクチャによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="2d8b3-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d8b3-105">構文</span><span class="sxs-lookup"><span data-stu-id="2d8b3-105">Syntax</span></span>  
  
```cpp  
HRESULT ForwardTranslateAccelerator(  
   MSG* pMsg,   
   VARIANT_BOOL appUnhandled  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d8b3-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2d8b3-106">Parameters</span></span>  
 <span data-ttu-id="2d8b3-107">pMsg</span><span class="sxs-lookup"><span data-stu-id="2d8b3-107">pMsg</span></span>  
 <span data-ttu-id="2d8b3-108">メッセージへのポインター。</span><span class="sxs-lookup"><span data-stu-id="2d8b3-108">A pointer to a message.</span></span>  
  
 <span data-ttu-id="2d8b3-109">appUnhandled</span><span class="sxs-lookup"><span data-stu-id="2d8b3-109">appUnhandled</span></span>  
 <span data-ttu-id="2d8b3-110">`true` アプリが既に指定されていますが、入力メッセージの処理が、それが処理されていません。それ以外の場合、`false`です。</span><span class="sxs-lookup"><span data-stu-id="2d8b3-110">`true` when the app has already been given a chance to handle the input message, but has not handled it; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d8b3-111">要件</span><span class="sxs-lookup"><span data-stu-id="2d8b3-111">Requirements</span></span>  
 <span data-ttu-id="2d8b3-112">**プラットフォーム:** を参照してください[.NET Framework システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="2d8b3-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d8b3-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="2d8b3-113">**DLL:**</span></span>  
  
 <span data-ttu-id="2d8b3-114">.NET framework 3.0 および 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="2d8b3-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="2d8b3-115">.NET Framework 4 以降: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="2d8b3-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="2d8b3-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d8b3-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d8b3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="2d8b3-117">See Also</span></span>  
 [<span data-ttu-id="2d8b3-118">WPF のアンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="2d8b3-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
