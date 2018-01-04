---
title: "関数をアクティブ化する (WPF アンマネージ API リファレンス)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: Acrivate
api_location: PresentationHost_v0400.dll
ms.assetid: 1400329c-b598-465f-80f2-e3dabf044811
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d890f3bd69c721071695713e0750180d50ed1ddf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="activate-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="374d0-102">関数をアクティブ化する (WPF アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="374d0-102">Activate Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="374d0-103">この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしてをコードから直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="374d0-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="374d0-104">Windows の管理、Windows Presentation Foundation (WPF) インフラストラクチャによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="374d0-104">Used by the Windows Presentation Foundation (WPF) infrastructure for windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="374d0-105">構文</span><span class="sxs-lookup"><span data-stu-id="374d0-105">Syntax</span></span>  
  
```cpp  
void Activate(  
    const ActivateParameters* pParameters,  
    __deref_out_ecount(1) LPUNKNOWN* ppInner,  
    );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="374d0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="374d0-106">Parameters</span></span>  
 <span data-ttu-id="374d0-107">pParameters</span><span class="sxs-lookup"><span data-stu-id="374d0-107">pParameters</span></span>  
 <span data-ttu-id="374d0-108">ウィンドウのアクティブ化パラメーターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="374d0-108">A pointer to the window's activation parameters.</span></span>  
  
 <span data-ttu-id="374d0-109">ppInner</span><span class="sxs-lookup"><span data-stu-id="374d0-109">ppInner</span></span>  
 <span data-ttu-id="374d0-110">ポインターを格納している 1 つの要素のバッファーのアドレスへのポインター、<xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument>オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="374d0-110">A pointer to the address of a single-element buffer that contains a pointer to an <xref:Microsoft.VisualStudio.OLE.Interop.IOleDocument> object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="374d0-111">必要条件</span><span class="sxs-lookup"><span data-stu-id="374d0-111">Requirements</span></span>  
 <span data-ttu-id="374d0-112">**プラットフォーム:**を参照してください[.NET Framework システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="374d0-112">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="374d0-113">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="374d0-113">**DLL:**</span></span>  
  
 <span data-ttu-id="374d0-114">.NET framework 3.0 および 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="374d0-114">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="374d0-115">.NET Framework 4 以降: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="374d0-115">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="374d0-116">**.NET framework のバージョン:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="374d0-116">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="374d0-117">参照</span><span class="sxs-lookup"><span data-stu-id="374d0-117">See Also</span></span>  
 [<span data-ttu-id="374d0-118">WPF のアンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="374d0-118">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
