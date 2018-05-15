---
title: CreateInstallReferenceEnum 関数
ms.date: 03/30/2017
api_name:
- CreateInstallReferenceEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateInstallReference
helpviewer_keywords:
- CreateInstallReference function [.NET Framework fusion]
ms.assetid: 80dbbbf8-54fc-4894-b74a-0179d3201083
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e35654b03f68a306329ef488289cfecd6f012484
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="createinstallreferenceenum-function"></a><span data-ttu-id="f983b-102">CreateInstallReferenceEnum 関数</span><span class="sxs-lookup"><span data-stu-id="f983b-102">CreateInstallReferenceEnum Function</span></span>
<span data-ttu-id="f983b-103">ポインターを取得、 [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)を指定したアセンブリへのアプリケーションの参照の一覧を表すインスタンス。</span><span class="sxs-lookup"><span data-stu-id="f983b-103">Gets a pointer to an [IInstallReferenceEnum](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md) instance that represents a list of an application's references to the specified assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f983b-104">構文</span><span class="sxs-lookup"><span data-stu-id="f983b-104">Syntax</span></span>  
  
```  
HRESULT CreateInstallReferenceEnum (  
    [out] IInstallReferenceEnum **ppRefEnum,  
    [in]  IAssemblyName         *pName,  
    [in]  DWORD                 dwFlags,  
    [in]  LPVOID                pvReserved  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f983b-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f983b-105">Parameters</span></span>  
 `ppRefEnum`  
 <span data-ttu-id="f983b-106">[out]返された`IInstallReferenceEnum`ポインター。</span><span class="sxs-lookup"><span data-stu-id="f983b-106">[out] The returned `IInstallReferenceEnum` pointer.</span></span>  
  
 `pName`  
 <span data-ttu-id="f983b-107">[in][IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)の参照を列挙するアセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="f983b-107">[in] The [IAssemblyName](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md) that identifies the assembly for which to enumerate references.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="f983b-108">[in]列挙子の動作を制御するフラグ。</span><span class="sxs-lookup"><span data-stu-id="f983b-108">[in] Flags that influence the enumerator's behavior.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="f983b-109">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="f983b-109">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="f983b-110">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="f983b-110">`pvReserved` must be a null reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f983b-111">要件</span><span class="sxs-lookup"><span data-stu-id="f983b-111">Requirements</span></span>  
 <span data-ttu-id="f983b-112">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="f983b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f983b-113">**ヘッダー:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f983b-113">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f983b-114">**ライブラリ:** Fusion.dll と Mscorwks.dll です。</span><span class="sxs-lookup"><span data-stu-id="f983b-114">**Library:** Fusion.dll and Mscorwks.dll.</span></span> <span data-ttu-id="f983b-115">Mscorwks.dll の代わりに Fusion.dll を使用して、正しいバージョンの .NET Framework を対象にすることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f983b-115">Use Fusion.dll instead of Mscorwks.dll to ensure that you target the correct version of the .NET Framework.</span></span>  
  
 <span data-ttu-id="f983b-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f983b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f983b-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f983b-117">See Also</span></span>  
 [<span data-ttu-id="f983b-118">IInstallReferenceEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f983b-118">IInstallReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iinstallreferenceenum-interface.md)  
 [<span data-ttu-id="f983b-119">IAssemblyName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f983b-119">IAssemblyName Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/iassemblyname-interface.md)  
 [<span data-ttu-id="f983b-120">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="f983b-120">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
