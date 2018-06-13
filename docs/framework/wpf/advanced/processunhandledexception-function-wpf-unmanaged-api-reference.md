---
title: ProcessUnhandledException 関数 (WPF アンマネージ API リファレンス)
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ProcessUnhandledException
api_location:
- PresentationHost_v0400.dll
ms.assetid: 495ce5f6-bb4d-4b30-807a-c3c35f1ca95c
ms.openlocfilehash: bcde3fe6d3fdc1749f29a5c9f7625f802dd49535
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544525"
---
# <a name="processunhandledexception-function-wpf-unmanaged-api-reference"></a><span data-ttu-id="12d70-102">ProcessUnhandledException 関数 (WPF アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="12d70-102">ProcessUnhandledException Function (WPF Unmanaged API Reference)</span></span>
<span data-ttu-id="12d70-103">この API は、Windows Presentation Foundation (WPF) インフラストラクチャをサポートしてをコードから直接使用するものではありません。</span><span class="sxs-lookup"><span data-stu-id="12d70-103">This API supports the Windows Presentation Foundation (WPF) infrastructure and is not intended to be used directly from your code.</span></span>  
  
 <span data-ttu-id="12d70-104">例外処理のため、Windows Presentation Foundation (WPF) インフラストラクチャによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="12d70-104">Used by the Windows Presentation Foundation (WPF) infrastructure for exception handling.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12d70-105">構文</span><span class="sxs-lookup"><span data-stu-id="12d70-105">Syntax</span></span>  
  
```cpp  
void __stdcall ProcessUnhandledException(  
   __in_ecount(1) BSTR errorMsg  
)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="12d70-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="12d70-106">Parameters</span></span>  
 <span data-ttu-id="12d70-107">errorMsg</span><span class="sxs-lookup"><span data-stu-id="12d70-107">errorMsg</span></span>  
 <span data-ttu-id="12d70-108">エラー メッセージ。</span><span class="sxs-lookup"><span data-stu-id="12d70-108">The error message.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12d70-109">要件</span><span class="sxs-lookup"><span data-stu-id="12d70-109">Requirements</span></span>  
 <span data-ttu-id="12d70-110">**プラットフォーム:** を参照してください[.NET Framework システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="12d70-110">**Platforms:** See [.NET Framework System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12d70-111">**DLL:**</span><span class="sxs-lookup"><span data-stu-id="12d70-111">**DLL:**</span></span>  
  
 <span data-ttu-id="12d70-112">.NET framework 3.0 および 3.5: PresentationHostDLL.dll</span><span class="sxs-lookup"><span data-stu-id="12d70-112">In the .NET Framework 3.0 and 3.5: PresentationHostDLL.dll</span></span>  
  
 <span data-ttu-id="12d70-113">.NET Framework 4 以降: PresentationHost_v0400.dll</span><span class="sxs-lookup"><span data-stu-id="12d70-113">In the .NET Framework 4 and later: PresentationHost_v0400.dll</span></span>  
  
 <span data-ttu-id="12d70-114">**.NET framework のバージョン:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12d70-114">**.NET Framework Version:** [!INCLUDE[net_current_v30plus](../../../../includes/net-current-v30plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12d70-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="12d70-115">See Also</span></span>  
 [<span data-ttu-id="12d70-116">WPF のアンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="12d70-116">WPF Unmanaged API Reference</span></span>](../../../../docs/framework/wpf/advanced/wpf-unmanaged-api-reference.md)
