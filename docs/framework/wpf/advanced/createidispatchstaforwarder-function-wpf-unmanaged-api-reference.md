---
title: "CreateIDispatchSTAForwarder 関数 (WPF アンマネージ API リファレンス)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
api_name: CreateIDispatchSTAForwarder
api_location: PresentationHost_v0400.dll
ms.assetid: 57a02dfa-f091-4ace-9c06-1f4ab52b3527
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 63195ce2a47add2606f528b18d0d1d58ab0d968c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="createidispatchstaforwarder-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="fc786-102">CreateIDispatchSTAForwarder 関数 (WPF アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="fc786-102">CreateIDispatchSTAForwarder Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="fc786-103">この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしてをコードから直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="fc786-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="fc786-104">スレッドと windows の管理、Windows Presentation Foundation (WPF) インフラストラクチャによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="fc786-104">Used by the Windows Presentation Foundation (WPF) infrastructure for thread and windows management.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc786-105">構文</span><span class="sxs-lookup"><span data-stu-id="fc786-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateIDispatchSTAForwarder(  
   __in IDispatch *pDispatchDelegate,   
   __deref_out IDispatch **ppForwarder  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fc786-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="fc786-106">Parameters</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="fc786-107">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="fc786-107">Property Value/Return Value</span></span>  
 <span data-ttu-id="fc786-108">pDispatchDelegate</span><span class="sxs-lookup"><span data-stu-id="fc786-108">pDispatchDelegate</span></span>  
 <span data-ttu-id="fc786-109">ポインター、`IDispatch`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="fc786-109">A pointer to an `IDispatch` interface.</span></span>  
  
 <span data-ttu-id="fc786-110">ppForwarder</span><span class="sxs-lookup"><span data-stu-id="fc786-110">ppForwarder</span></span>  
 <span data-ttu-id="fc786-111">アドレスへのポインター、`IDispatch`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="fc786-111">A pointer to the address of an `IDispatch` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc786-112">要件</span><span class="sxs-lookup"><span data-stu-id="fc786-112">Requirements</span></span>  
 <span data-ttu-id="fc786-113">**プラットフォーム:**を参照してください[.NET Framework システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="fc786-113">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc786-114">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="fc786-114">**DLL:**</span></span>  
  
 <span data-ttu-id="fc786-115">.NET framework 3.0 および 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="fc786-115">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="fc786-116">.NET Framework 4 以降: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="fc786-116">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="fc786-117">**.NET framework のバージョン:**[!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc786-117">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc786-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc786-118">See Also</span></span>  
 [<span data-ttu-id="fc786-119">WPF のアンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="fc786-119">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
