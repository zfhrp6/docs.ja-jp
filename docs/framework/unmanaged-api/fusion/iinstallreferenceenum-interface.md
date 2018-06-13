---
title: IInstallReferenceEnum インターフェイス
ms.date: 03/30/2017
api_name:
- IInstallReferenceEnum
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IInstallReferenceEnum
helpviewer_keywords:
- IInstallReferenceEnum interface [.NET Framework fusion]
ms.assetid: 2863b33b-a541-462c-bbe8-702a2832898e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cac9f9db0b7527a80671c825a4435e8ea2d135b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429661"
---
# <a name="iinstallreferenceenum-interface"></a><span data-ttu-id="00c4d-102">IInstallReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00c4d-102">IInstallReferenceEnum Interface</span></span>
<span data-ttu-id="00c4d-103">グローバル アセンブリ キャッシュにインストールされている参照先アセンブリの列挙子を表します。</span><span class="sxs-lookup"><span data-stu-id="00c4d-103">Represents an enumerator for the referenced assemblies installed in the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00c4d-104">構文</span><span class="sxs-lookup"><span data-stu-id="00c4d-104">Syntax</span></span>  
  
```  
interface IInstallReferenceEnum : IUnknown {  
    HRESULT GetNextInstallReferenceItem (  
        [out] IInstallReferenceItem **ppRefItem,  
        [in]  DWORD dwFlags,  
        [in]  LPVOID pvReserved  
    );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="00c4d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="00c4d-105">Methods</span></span>  
  
|<span data-ttu-id="00c4d-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="00c4d-106">Method</span></span>|<span data-ttu-id="00c4d-107">説明</span><span class="sxs-lookup"><span data-stu-id="00c4d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="00c4d-108">GetNextInstallReferenceItem メソッド</span><span class="sxs-lookup"><span data-stu-id="00c4d-108">GetNextInstallReferenceItem Method</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-getnextinstallreferenceitem-method.md)|<span data-ttu-id="00c4d-109">ポインターを取得`IInstallReferenceItem`これに含まれている`IInstallReferenceEnum`です。</span><span class="sxs-lookup"><span data-stu-id="00c4d-109">Gets a pointer to the next `IInstallReferenceItem` contained in this `IInstallReferenceEnum`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="00c4d-110">要件</span><span class="sxs-lookup"><span data-stu-id="00c4d-110">Requirements</span></span>  
 <span data-ttu-id="00c4d-111">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="00c4d-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00c4d-112">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="00c4d-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="00c4d-113">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00c4d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00c4d-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="00c4d-114">See Also</span></span>  
 [<span data-ttu-id="00c4d-115">Fusion インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00c4d-115">Fusion Interfaces</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [<span data-ttu-id="00c4d-116">IInstallReferenceItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="00c4d-116">IInstallReferenceItem Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceitem-interface.md)
